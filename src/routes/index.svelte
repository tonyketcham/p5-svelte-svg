<script lang="ts">
	import P5 from 'p5-svelte';
	import p5SvgRuntime from 'p5.js-svg';
	import type { default as p5Type } from 'p5';

	interface P5Svg extends p5Type {
		/**
		 * SVG runtime for the p5.js canvas.
		 */
		SVG: p5Type.RENDERER;
	}

	type SvgSketch = (p5Svg: P5Svg) => void;

	const sketch: SvgSketch = (p5) => {
		// p5SvgRuntime(p5);
		p5.setup = () => {
			// US Letter size paper (8.5 x 11 in) @ 96 DPI
			p5.createCanvas(816, 1054, p5.SVG);
		};
		console.log(p5.SVG);
		p5.draw = () => {
			p5.clear(0, 0, 0, 0);
			p5.ellipse(p5.mouseX, p5.mouseY, 80, 80);
		};
	};
</script>

<P5 {sketch} />
