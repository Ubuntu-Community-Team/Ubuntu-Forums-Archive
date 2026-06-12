---
title: "Is there a way to interpolate videos"
date: 2015-11-27
forum: General Help
---

### Post by Chelidze on 2015-11-27
I know I know interpolating videos isn't the best idea but i am curious and just want it.

The windows users have megui ([found this guide]("http://www.spirton.com/convert-videos-to-60fps/")) and the results aren't bad.

So is there a way to do this task on linux, one more thing Yes i know about slowmovideo but I really didn't like the results.

---

### Post by TheFu on 2015-11-27
Sure. use avconv, ffmpeg, or mencoder. These tools easily make 2x the frames from interlaced videos.

---

### Post by Chelidze on 2015-11-27
> **TheFu said:**
> Sure. use avconv, ffmpeg, or mencoder. These tools easily make 2x the frames from interlaced videos.

Well there is a small problem, sure the ffmpeg will copy frames but I want something more effective like megui

Take a look:
[Original file]("http://www.spirton.com/uploads/InterFrame/20110618-Sample-Original.mkv")
[Converted file]("http://www.spirton.com/uploads/InterFrame/20110618-Sample-InterFrame.mkv") (megui)

---

### Post by TheFu on 2015-11-27
effective? That is a completely subjective comparison.

I've created tiny scripts around ffmpeg to transcode hundreds/thousands of video files. Hard to imagine any "gui" to be more 'effective' than that. OTOH, if pointing-and-clicking is deemed 'effective', fine.

As to quality, ffmpeg has thousands of options to control the resulting output file. A little reading should provide the necessary options to achieve a desired result.

There is always avidemux or handbrake if a GUI is mandated.

---

### Post by Chelidze on 2015-11-27
> **TheFu said:**
> effective? That is a completely subjective comparison.

I've created tiny scripts around ffmpeg to transcode hundreds/thousands of video files. Hard to imagine any "gui" to be more 'effective' than that. OTOH, if pointing-and-clicking is deemed 'effective', fine.

As to quality, ffmpeg has thousands of options to control the resulting output file. A little reading should provide the necessary options to achieve a desired result.

There is always avidemux or handbrake if a GUI is mandated.

I really don't like Megui and I don't want to ever use it, however I can't argue with the results the megui script is very effective in making videos look smooth, if they were really recorded on 60fps.

 If you can give me a script for ffmpeg that will create new interpolated frames. then i will be really great full

---

### Post by blm-ubunet on 2015-11-27
The "mvtools" avisynth plugin has been recently ported to vapoursynth which allows motion vector interpolation amongst loads of other things.
[https://launchpad.net/~djcj/+archive/ubuntu/vapoursynth](https://launchpad.net/~djcj/+archive/ubuntu/vapoursynth)
There is vapoursynth plug support in later ffmpeg, might have to build later version or get from ppa.
Ffmpeg was never able to do interpolation natively.

Other alternative is the mjpegtools yuvfps or the extra:-
[http://jcornet.free.fr/linux/yuvmotionfps.html](http://jcornet.free.fr/linux/yuvmotionfps.html)
These work on raw yuv so have to decode & (pipe) process & (pipe) encode with ffmpeg for ex.

---

### Post by TheFu on 2015-11-27
> **Chelidze said:**
>  If you can give me a script for ffmpeg that will create new interpolated frames. then i will be really great full

[https://superuser.com/questions/504669/ffmpeg-for-frame-interpolation-ala-twixtor](https://superuser.com/questions/504669/ffmpeg-for-frame-interpolation-ala-twixtor) says that ffmpeg cannot interpolate frames alone.  There are addons, but I've never used any for this purpose.
[https://superuser.com/questions/253691/how-to-convert-108050i-72050p-using-ffmpeg](https://superuser.com/questions/253691/how-to-convert-108050i-72050p-using-ffmpeg) has a few examples and explains why they look bad.

Did you look at avidemux?
 
What about using vlc? It has deinterlacing as playback options. Perhaps one could be used for transcoding?

---

### Post by Chelidze on 2015-11-27
> **blm-ubunet said:**
> The "mvtools" avisynth plugin has been recently ported to vapoursynth which allows motion vector interpolation amongst loads of other things.
[https://launchpad.net/~djcj/+archive/ubuntu/vapoursynth](https://launchpad.net/~djcj/+archive/ubuntu/vapoursynth)
There is vapoursynth plug support in later ffmpeg, might have to build later version or get from ppa.
Ffmpeg was never able to do interpolation natively.

Other alternative is the mjpegtools yuvfps or the extra:-
[http://jcornet.free.fr/linux/yuvmotionfps.html](http://jcornet.free.fr/linux/yuvmotionfps.html)
These work on raw yuv so have to decode & (pipe) process & (pipe) encode with ffmpeg for ex.


I been looking around the web and couldn't find the answer so I will ask if you don't mind 

I will build the latest ffmpeg no problem but how do I use vapoursynth with it ??
small example would be great :D

> **TheFu said:**
> [https://superuser.com/questions/504669/ffmpeg-for-frame-interpolation-ala-twixtor](https://superuser.com/questions/504669/ffmpeg-for-frame-interpolation-ala-twixtor) says that ffmpeg cannot interpolate frames alone.  There are addons, but I've never used any for this purpose.
[https://superuser.com/questions/253691/how-to-convert-108050i-72050p-using-ffmpeg](https://superuser.com/questions/253691/how-to-convert-108050i-72050p-using-ffmpeg) has a few examples and explains why they look bad.

Did you look at avidemux?
 

What about using vlc? It has deinterlacing as playback options. Perhaps one could be used for transcoding?

thank you, I will look into avidemux.

Update
Well so far no luck with avidemux maybe I can't use it properly but the frames look copped

---

### Post by blm-ubunet on 2015-11-27
There are (at least) 2 ways to try make it all work..
1. Use ffmpeg & vapoursynth plugins
would require to build ffmpeg with additional config option "--enable-avisynth"
```
ffmpeg -i input.avs -c:v libx264 [options] output.mkv
```
where input.avs is a avxsynth script; not even sure this is still workable TBH.

2. Use vapoursynth frameserver & ffmpeg just as encoder.
Install vapoursynth & plugins from that ppa posted previous..

I think that (2.) is the better approach.
```
python-script.vpy | ffmpeg -f yuv4mpegpipe -i - output.mkv 
```

That's the easy part.. a nice small linux example would be great..
The vapoursynth editor could be a starting point.

Another solution is almost all modern TVs can frame interpolate.
Could do interpolation with windows & madVR.

---

### Post by Chelidze on 2015-11-27
OK been trying this and that and came to a conclusion that I just can't get it to work.

So hope one day some one will make a step by step tutorial on how to make this work, otherwise i give up.

---

### Post by blm-ubunet on 2015-11-27
This what the python-script.py could look like.
[[http://forum.doom9.org/showthread.php?p=1590279#post1590279](http://forum.doom9.org/showthread.php?p=1590279#post1590279)
That's an old example that is broken..

This program/process is incredibly powerful/flexible but there is a steep learning curve for non-programmers or video novices.

The mjpegtools yuvfps is much easier to use initially.

---

### Post by Chelidze on 2015-11-28
> **blm-ubunet said:**
> This what the python-script.py could look like.
[[http://forum.doom9.org/showthread.php?p=1590279#post1590279](http://forum.doom9.org/showthread.php?p=1590279#post1590279)
That's an old example that is broken..

This program/process is incredibly powerful/flexible but there is a steep learning curve for non-programmers or video novices.

The mjpegtools yuvfps is much easier to use initially.

Thank you very much for your help, but sadly i just dont have enough skills. 

Would be great if some one would make a good guide or make a small software that does all of this.

---

### Post by blm-ubunet on 2015-11-28
The problem with a step-by-step guide is that it would need lots of maintenance.
There are maintained web resources for each of the different components required.
What is missing is the explanation of the purpose of each component & how to obtain & then compile with the required options.

This is compounded by the ubuntu version & possibly having to upgrade ffmpeg libs.
I built ffmpeg (& libs) four times before remembering the right configure options to make shared PIC libraries.

After getting vapoursynth & mvtools plugin working I now think the ffmpeg avxsynth plugin is a better option. But you still need to compile/build ffmpeg if ubuntu < 15.10 and you have to compile avxsynth & ffms & mvtools.

The vapoursynth (& mjpegtools yuvfps) process require the AV media to be demuxed, processed & then re-muxed together.
The ffmpeg avxsynth plugin could avoid all that.
Still have to write the avxsynth script to actual achieve the interpolated frame rate doubling.

---

### Post by Chelidze on 2015-11-28
> **blm-ubunet said:**
> The problem with a step-by-step guide is that it would need lots of maintenance.
There are maintained web resources for each of the different components required.
What is missing is the explanation of the purpose of each component & how to obtain & then compile with the required options.

This is compounded by the ubuntu version & possibly having to upgrade ffmpeg libs.
I built ffmpeg (& libs) four times before remembering the right configure options to make shared PIC libraries.

After getting vapoursynth & mvtools plugin working I now think the ffmpeg avxsynth plugin is a better option. But you still need to compile/build ffmpeg if ubuntu < 15.10 and you have to compile avxsynth & ffms & mvtools.

The vapoursynth (& mjpegtools yuvfps) process require the AV media to be demuxed, processed & then re-muxed together.
The ffmpeg avxsynth plugin could avoid all that.
Still have to write the avxsynth script to actual achieve the interpolated frame rate doubling.

To be honest i don't want to bother my self that much, well if there was an easy way out then I would gladly use it.
Yes, It would be great if there was a easy way out like on windows but there is cons to it.
for example now on windows after following this [guide]("http://www.spirton.com/convert-videos-to-60fps/") the system has ton of conflicting codecs :D

---

### Post by blm-ubunet on 2015-11-29
Almost all the code mentioned in your link is open source & could run in linux.
The SVP plugin is (not free) & avisynth (windows or wine) only.

I got ffmpeg & avxsynth plugin working with a script opening/playing a video with SMTP timestamp overlay.. 4hrs.

I found this info about mvtools & avxsynth in mvp (movie player):-
[https://github.com/mpv-player/mpv/issues/566#issuecomment-73280199](https://github.com/mpv-player/mpv/issues/566#issuecomment-73280199)

And this for processing video files:-
[https://aur.archlinux.org/packages/butterflow](https://aur.archlinux.org/packages/butterflow)
looks to use openCL so potential for using the GPU. Could be what you're looking for.

---

### Post by Chelidze on 2015-11-29
> **blm-ubunet said:**
> Almost all the code mentioned in your link is open source & could run in linux.
The SVP plugin is (not free) & avisynth (windows or wine) only.

I got ffmpeg & avxsynth plugin working with a script opening/playing a video with SMTP timestamp overlay.. 4hrs.

I found this info about mvtools & avxsynth in mvp (movie player):-
[https://github.com/mpv-player/mpv/issues/566#issuecomment-73280199](https://github.com/mpv-player/mpv/issues/566#issuecomment-73280199)

And this for processing video files:-
[https://aur.archlinux.org/packages/butterflow](https://aur.archlinux.org/packages/butterflow)
looks to use openCL so potential for using the GPU. Could be what you're looking for.

Thank you very much the butterflow software looks really promising.

Thank you for all your help :KS

---

### Post by blm-ubunet on 2015-12-03
mpv allows for playback & transcoding..
Install mpv & vapoursynth from this ppa 
[https://launchpad.net/~djcj/+archive/ubuntu/vapoursynth](https://launchpad.net/~djcj/+archive/ubuntu/vapoursynth)

I think you still have to compile mvtools plugin (from github) as it is not in the ppa extras package.

Here's a script that converts (with motion vectors etc) to 60fps:-
[https://github.com/haasn/gentoo-conf/blob/nanodesu/home/nand/.mpv/filters/mvtools.vpy](https://github.com/haasn/gentoo-conf/blob/nanodesu/home/nand/.mpv/filters/mvtools.vpy)

Playback useage:
mpv --vf=vapoursynth=mvtools.vpy <video_file>

FYI:
[https://github.com/mpv-player/mpv/wiki/Interpolation](https://github.com/mpv-player/mpv/wiki/Interpolation)

---

