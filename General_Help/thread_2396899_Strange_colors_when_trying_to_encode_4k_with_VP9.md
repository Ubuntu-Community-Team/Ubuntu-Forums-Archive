---
title: "Strange colors when trying to encode 4k with VP9"
date: 2018-07-22
forum: General Help
---

### Post by rockerovo on 2018-07-22
[COLOR=#242729][FONT=Arial]I'm trying to encode 4k yuv video with webmproject VP9 I m using Linux Kubuntu 18.04 my command :

[/FONT][/COLOR][COLOR=#242729][FONT=Arial]when trying to open webm in chrome, I got a Strange color [/FONT][/COLOR][https://i.stack.imgur.com/EYdJS.jpg](https://i.stack.imgur.com/EYdJS.jpg)
[COLOR=#242729][FONT=Arial]
[/FONT][/COLOR]./vpxenc --codec=vp9  --profile=0  --fps=50000/1001 --static-thresh=0 --drop-frame=0 --good --auto-alt-ref=1  --kf-min-dist=50 --kf-max-dist=50 --min-q=32 --max-q=32 --max-intra-rate=50 -w 3840 -h 2160 --limit=1 --i420 /home/siraj/Desktop/Project/Samples/Jockey_3840x2160_120fps_420_10bit_YUV.yuv -o siraj.webm

---

