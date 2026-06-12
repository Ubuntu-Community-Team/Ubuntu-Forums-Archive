---
title: "repair corrupted AVI/MKV family videos"
date: 2021-12-14
forum: General Help
---

### Post by alain.roger on 2021-12-14
Hi,

I have some family videos in AVI/MKV formats that are corrupted.

I would like to know what is the best tool (or commandlines) to fix those files unde ubuntu 21.10 ?

I know that a lot of tools/apps exist under windows, but I have some troubles to find something working under linux.

thanks a lot to drop me a comment/line about how to fix them or tools helping in this process.

thx

---

### Post by #&amp;thj^% on 2021-12-14
If you already have VLC Media Player installed on your computer, then this "might" work for you.
 you can have VLC automatically fix the file when it is played by going to Tools and then Preferences. Click on Inputs and Codecs and then choose Always Fix next to Damaged or incomplete AVI file.
 
 There are online tools as well for a fee. One  suggestion is: [https://fix.video/](https://fix.video/)

 You can use a feature in ffmpeg video converter: if you will specify it to recode video to nothing it will just read input file and report any errors that will appear. This is very fast process because video frames are just being read, checked and silently dropped.

Example command line: (for Linux)

```
ffmpeg -v error -i file.avi -f null - 2>error.log
```

-v error means a certain level of verbosity (to show some errors that are normally hidden because they don't affect playability a much).

You will get a full error log with some generic information with file ffmpeg will output, so this will probably require your attention.

---

### Post by alain.roger on 2021-12-14
1. I already tried several times VLC and it never fixed any video in last 4 years... So i'm not so much positive about VLC fixing errors.
2. fix.video website is very limited interm of allowed extensions and AVI / MKV are not a part of them unfortunately.

---

### Post by #&amp;thj^% on 2021-12-14
> **alain.roger said:**
> 2. fix.video website is very limited interm of allowed extensions and AVI / MKV are not a part of them unfortunately.

If that's the case they have changed then, I never had any issues with them or FFMPEG when repairing videos.

---

### Post by DuckHook on 2021-12-14
> **alain.roger said:**
> 1. I already tried several times VLC and it never fixed any video in last 4 years... So i'm not so much positive about VLC fixing errors.
2. fix.video website is very limited interm of allowed extensions and AVI / MKV are not a part of them unfortunately.
This is a good reason to keep a Windows VM on a Linux box: there are just some things that Windows still does better than Linux, if for no other reason than more devs producing apps for Windows.

For MKV, I use a GUI overlay of *MKVToolNix* called *MKVToolNix-Gui*. Both can be installed with:```
sudo apt install mkvtoolnix mkvtoolnix-gui
```

I've used *MKVToolNix* for merging MKV files, but not for repair, so I have no experience to help you there. However, files can sometimes be repaired by re-encoding them, though this process involves some loss.

You can also try re&#8209;encoding the file using *HandBrake*, which can be installed with:```
sudo apt install handbrake
```Depending on your CPU, *HandBrake* can take a loooong time (I mean hours, so be patient).

---

### Post by dragonfly41 on 2021-12-14
I believe that Blender 2.8.0 might offer features for fixing videos.

In Google search .. blender fix video

There are some articles/tutorials.

I have Blender installed on Ubuntu 20.04. 
Also perhaps try ffDiaporama.

---

### Post by dragonfly41 on 2021-12-15
[COLOR=#000000]> I have some troubles to find something working under linux.

As an afterthought, although Blender appears to be very powerful (post above) if you have some clips which require deep repair you might consider Wolfram (there is a free developer licence for personal use).

[/COLOR][COLOR=#000000]Wolfram - wolframscript for CLI and WolframEngine run on Ubuntu 20.04 for my hobby usage.

Here are example community posts:

[/COLOR][https://community.wolfram.com/groups/-/m/t/2188963](https://community.wolfram.com/groups/-/m/t/2188963)

[https://reference.wolfram.com/language/tutorial/ImportingAndExportingVideo.html](https://reference.wolfram.com/language/tutorial/ImportingAndExportingVideo.html)

But it takes time to understand this ecosystem. Only for advanced operations, I suggest.
Read the background of Wolfram, the founder.
[COLOR=#000000]
[/COLOR]

---

