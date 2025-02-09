<script>
	import { getContext } from 'svelte';
	const i18n = getContext('i18n');

	import { WEBUI_BASE_URL } from '$lib/constants';

	import Marquee from './common/Marquee.svelte';
	import SlideShow from './common/SlideShow.svelte';
	import ArrowRightCircle from './icons/ArrowRightCircle.svelte';

	export let show = true;
	export let getStartedHandler = () => {};
</script>

{#if show}
	<div class="w-full h-screen max-h-[100dvh] text-white relative">
		<div class="fixed m-10 z-50">
			<div class="flex space-x-2">
				<div class=" self-center">
					<img
						crossorigin="anonymous"
						src="{WEBUI_BASE_URL}/static/favicon.png"
						class=" w-6 rounded-full"
						alt="logo"
					/>
				</div>
			</div>
		</div>

		<SlideShow duration={5000} />

		<div
			class="w-full h-full absolute top-0 left-0 bg-gradient-to-t from-20% from-black to-transparent"
		></div>

		<div class="w-full h-full absolute top-0 left-0 backdrop-blur-sm bg-black/50"></div>

		<div class="relative bg-transparent w-full min-h-screen flex z-10">
			<div class="flex flex-col justify-end w-full items-center pb-10 text-center">
				<div class="text-5xl lg:text-7xl font-secondary">
					<Marquee
						duration={5000}
						words={[
							$i18n.t('Debug by day, degenerate by night.'),
							$i18n.t('Server racks don\'t judge, but HR does.'),
							$i18n.t('Uptime is 99.9%, but my filter is 0%.'),
							$i18n.t('Rebooting systems, corrupting morals.'),
							$i18n.t('AI runs the data center, I run the afterparty.'),
							$i18n.t('Error 404: Shame not found.'),
							$i18n.t('Drink now, patch later.'),
							$i18n.t('First I optimize networks, then I optimize my bar tab.'),
							$i18n.t('Not all heroes wear capes—some wear banana-stained hoodies.'),
							$i18n.t('Chaos is just a poorly managed algorithm.')
						]}
					/>

					<div class="mt-0.5">{$i18n.t(`wherever you are`)}</div>
				</div>

				<div class="flex justify-center mt-8">
					<div class="flex flex-col justify-center items-center">
						<button
							class="relative z-20 flex p-1 rounded-full bg-white/5 hover:bg-white/10 transition font-medium text-sm"
							on:click={() => {
								getStartedHandler();
							}}
						>
							<ArrowRightCircle className="size-6" />
						</button>
						<div class="mt-1.5 font-primary text-base font-medium">{$i18n.t(`Get started`)}</div>
					</div>
				</div>
			</div>

			<!-- <div class="absolute bottom-12 left-0 right-0 w-full"></div> -->
		</div>
	</div>
{/if}
