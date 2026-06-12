---
title: "screen recorder in Ubuntu repository?"
date: 2022-01-05
forum: General Help
---

### Post by Skaperen on 2022-01-05
is there any screen recorder (X windows full screen to video file ... usually with some way to include audio) in the Ubuntu package repository?  as an alternative, i can use something that has source code actually used (compiled or interpreted).

---

### Post by schragge on 2022-01-05
[vokoscreenNG]("https://linuxecke.volkoh.de/vokoscreen/vokoscreen.html"), [OBS Studio]("https://obsproject.com"), [Kazam]("https://launchpad.net/kazam"), [SimpleScreenRecorder]("https://www.maartenbaert.be/simplescreenrecorder"), [Deepin Screen Recorder](https://www.deepin.org/en/original/deepin-screen-recorder), [peek]("https://github.com/phw/peek/blob/main/README.md"), [byzanz]("https://www.mankier.com/1/byzanz"), [recordMyDesktop]("http://recordmydesktop.sf.net").

---

### Post by TheFu on 2022-01-05
ffmpeg too.  There are many, many, example commands on the web.
[https://trac.ffmpeg.org/wiki/Capture/Desktop](https://trac.ffmpeg.org/wiki/Capture/Desktop)  video only, audio via ALSA and audio via pulse examples in that link.

I find the -preset superfast option the best mix of file size and speed for fast action. YMMV, depends on your CPU capability. Using ultrafast creates larger files than a raw capture, IME, but later, transcoding the result down to at least 50-75% smaller is possible with something like Handbrake.

I use simplescreenrecorder 99% of the time.  Bet it uses ffmpeg code underneath.

---

### Post by Skaperen on 2022-01-05
i tried the example in that ffmpeg link.  i've never gotten any command to work,  here's the latest results.  i'm assuming it should capture th 1024x720+100+200 portion of the screen.  i will also try to capture the entire 1920x1080+0+0.  if i can get ffmpeg to work, i won't see any advantage for the others.  note "Invalid MIT-MAGIC-COOKIE-1 key" near the end.  is that the problem?
```

lt2a/forums /home/forums 7> ffmpeg -video_size 1024x768 -framerate 25 -f x11grab -i :0.0+100,200 output.mp4
ffmpeg version 3.4.8-0ubuntu0.2 Copyright (c) 2000-2020 the FFmpeg developers
  built with gcc 7 (Ubuntu 7.5.0-3ubuntu1~18.04)
  configuration: --prefix=/usr --extra-version=0ubuntu0.2 --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --enable-gpl --disable-stripping --enable-avresample --enable-avisynth --enable-gnutls --enable-ladspa --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libmp3lame --enable-libmysofa --enable-libopenjpeg --enable-libopenmpt --enable-libopus --enable-libpulse --enable-librubberband --enable-librsvg --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvorbis --enable-libvpx --enable-libwavpack --enable-libwebp --enable-libx265 --enable-libxml2 --enable-libxvid --enable-libzmq --enable-libzvbi --enable-omx --enable-openal --enable-opengl --enable-sdl2 --enable-libdc1394 --enable-libdrm --enable-libiec61883 --enable-chromaprint --enable-frei0r --enable-libopencv --enable-libx264 --enable-shared
  libavutil      55. 78.100 / 55. 78.100
  libavcodec     57.107.100 / 57.107.100
  libavformat    57. 83.100 / 57. 83.100
  libavdevice    57. 10.100 / 57. 10.100
  libavfilter     6.107.100 /  6.107.100
  libavresample   3.  7.  0 /  3.  7.  0
  libswscale      4.  8.100 /  4.  8.100
  libswresample   2.  9.100 /  2.  9.100
  libpostproc    54.  7.100 / 54.  7.100
Invalid MIT-MAGIC-COOKIE-1 key[x11grab @ 0x557659c24960] Cannot open display :0.0+100,200, error 1.
:0.0+100,200: Input/output error
lt2a/forums /home/forums 8> 

```

---

### Post by DuckHook on 2022-01-05
> **TheFu said:**
> …I use simplescreenrecorder 99% of the time…
It's apt description says:```
duckhook@Zeus:~$  apt show simplescreenrecorder
Package: simplescreenrecorder
…
Description: Feature-rich screen recorder for X11 and OpenGL
…
To perform an X11 recording, all it takes is selecting an area on
 the root window with the mouse, choosing an output file and pressing record,
 either by using the mouse or using a hotkey.
…
…It allows one
 to record X11 screen areas and fullscreen OpenGL applications including sound
 supporting both ALSA, PulseAudio, JACK and OSS. 
…
```
All references are to X. Will it work in Wayland?

---

### Post by schragge on 2022-01-06
[wf-recorder](https://github.com/ammen99/wf-recorder) will.

---

### Post by mIk3_08 on 2022-01-06
I have been using OBS and it was very smooth to use. So far so good without any hassle. It render videos very smoothly using my Linux Ubuntu Operating System. So far of use, I haven't encountered any errors in both my Linux Ubuntu Operating System and the OBS alone. Give 5 star feedback. I'm not advertising this application I used. I just shared my cool experienced using this video application. I know that there are a lot of video apps here in Open Source but I just recommend what I've used. So Good Luck and cheers.

---

### Post by Skaperen on 2022-01-06
> **DuckHook said:**
> It's apt description says:```
duckhook@Zeus:~$  apt show simplescreenrecorder
Package: simplescreenrecorder
…
Description: Feature-rich screen recorder for X11 and OpenGL
…
To perform an X11 recording, all it takes is selecting an area on
 the root window with the mouse, choosing an output file and pressing record,
 either by using the mouse or using a hotkey.
…
…It allows one
 to record X11 screen areas and fullscreen OpenGL applications including sound
 supporting both ALSA, PulseAudio, JACK and OSS. hardware
…
```
is that "press record" step when simplescreenrecorder gets started?  or do you start simplescreenrecorder before selecting an area?  what if you want the full screen recorded since it's kinda hard to select the full screen with the mouse.

> **DuckHook said:**
> All references are to X. Will it work in Wayland?
curious question but not an urgency since i don't use Wayland.

also, i'd like to keep recording the screen when i switch to a different user which is a different X process.  it's the screen *hardware* i want to record.

they should integrate recording in Wayland.

---

### Post by Skaperen on 2022-01-06
> **schragge said:**
> [wf-recorder]("https://github.com/ammen99/wf-recorder") will.

so it will work with Wayland.  it interfaces with the compositor. not the screen?  will it also work in X?

---

### Post by Skaperen on 2022-01-06
> **mIk3_08 said:**
> I have been using OBS and it was very smooth to use. So far so good without any hassle. It render videos very smoothly using my Linux Ubuntu Operating System. So far of use, I haven't encountered any errors in both my Linux Ubuntu Operating System and the OBS alone. Give 5 star feedback. I'm not advertising this application I used. I just shared my cool experienced using this video application. I know that there are a lot of video apps here in Open Source but I just recommend what I've used. So Good Luck and cheers.

can you describe the steps to start recording fullscreen?  can it be done by setting up a custom button that starts it (i can do that if it can be run as a command and no GUI).

---

### Post by DuckHook on 2022-01-06
> **Skaperen said:**
> …not an urgency since i don't use Wayland…
Not on Focal perhaps, but X's days are numbered.

[https://www.omgubuntu.co.uk/2021/01/ubuntu-21-04-will-use-wayland-by-default](https://www.omgubuntu.co.uk/2021/01/ubuntu-21-04-will-use-wayland-by-default)

X is no longer being developed and is barely even being maintained. Most of its devs have moved on to Wayland. If you intend to upgrade to Jammy, better start prepping now.

---

### Post by TheFu on 2022-01-06
> **DuckHook said:**
> Not on Focal perhaps, but X's days are numbered.

[https://www.omgubuntu.co.uk/2021/01/ubuntu-21-04-will-use-wayland-by-default](https://www.omgubuntu.co.uk/2021/01/ubuntu-21-04-will-use-wayland-by-default)

X is no longer being developed and is barely even being maintained. Most of its devs have moved on to Wayland. If you intend to upgrade to Jammy, better start prepping now.

[https://lists.x.org/archives/xorg/2021-October/060799.html](https://lists.x.org/archives/xorg/2021-October/060799.html)
There is a new X11 release coming - they don't do full, huge, releases anymore. If it is dropped from Ubuntu, I'll have little choice but to migrate if replacement tools or old tools don't work under Wayland ... in early 2025.  I'm still planning my 18.04 --> 20.04 migration.  We don't "do" bleeding edge.

For many people, "not being developed" means - "it will be stable".  ;)

---

### Post by Skaperen on 2022-01-06
> **DuckHook said:**
> Not on Focal perhaps, but X's days are numbered.

[https://www.omgubuntu.co.uk/2021/01/ubuntu-21-04-will-use-wayland-by-default](https://www.omgubuntu.co.uk/2021/01/ubuntu-21-04-will-use-wayland-by-default)

X is no longer being developed and is barely even being maintained. Most of its devs have moved on to Wayland. If you intend to upgrade to Jammy, better start prepping now.

X definitely needs to eventually go away.  but i may need to pause at focal (then jump past jammy) if it is going to require more time.

will *lightdm* still be involved?  among the things i want to be able to do is:

    dm-tool switch-to-user $username

of course there are things i need to learn about how *Wayland* works like what to do in cases where you would have 2 or more instances of *X* to support 2 or more desktop users and switching around among them.

1.  can Wayland be run in a VM hosted on a system running X?
2.  can Wayland and X be run concurrently on the same system?
3.  where can i find tutorial-like documentation on Wayland (for operations, not GUI app programming)?

i will have to see how Xfce handles this change.

---

### Post by TheFu on 2022-01-06
All screen recorders actually record what is ON THE SCREEN.  If you bring up a different window or otherwise hide or allow a screen saver to happen, then that will be recorded, not the screen you want.  Get a 2nd monitor, run the screen recorder you want on it.  If you don't need to interact with the screen at all, check out the xvfb device.  That will setup a virtual screen that cannot be accessed. It will have a different DISPLAY and you can set the DISPLAY to a different value for the screen recording software to capture it.  I've never done that. My only use of xvfb was when some Oracle server software had X11 client dependencies and refused to run at all on a headless server - headless, meaning ZERO GPU installed. Just TTY and network access.  Not only did the X/Client libraries need to be installed, but there had to be an X device with an X/Session that the server process could connect.  All I could say was "Bad Oracle Developer, bad, bad, bad."

X11 has weenie security, but it is sufficient, by default, to prevent a different userid from gaining access to  processes controlled by another user.  You'll need to read up on how to defeat that security, if that is your intention.  This is one of the major security faults in X11 and why some Wayland zealots exist.  They aren't wrong.  In the 1990s, I was an X/Windows developer working on a huge govt contract creating GUIs for a control center.  In that environment, everything was very team oriented - you've probably seen movies about it. Anyway, we'd just replaced some very old, almost-Unix systems throughout the entire control center and is all support locations worldwide with some real Unix workstations and secure links. Inside each center, there was a requirement for team members to have access to each other's screens.  X11 allows that, but it defeats all sort of security - allowing anyone on the network the ability to access the x/protocol.  It was funny - they insisted on running Kerberos for authentication and everyone in the building had clearances, but they also insisted on opening up access for remote control, display, and funny business using a UDP-based protocol that cannot be traced easily.

Anyway, you can look up the **xhost** command and see the new options (ok, they are new to me, but probably more than 5 yrs old), if you still want to do that.

Really, I'd say just to run SimpleScreenRecorder - try it out. It is pretty bonehead easy.

---

### Post by TheFu on 2022-01-06
> 
1. can Wayland be run in a VM hosted on a system running X?
2. can Wayland and X be run concurrently on the same system?
3. where can i find tutorial-like documentation on Wayland (for operations, not GUI app programming)?


1. yes.  It works.  May need to be more specific about the exact releases used for the host and the guest OSes, but I've used X11 on 18.04 with Wayland running in 21.04 accessing the VM using KVM-Spice and virt-viewer.

2. I don't know. They connect to the GPU, so if you have 2 GPUs, perhaps, but I honestly don't know.

3. Unknown.  Usually, when GUI apps that previously supported X don't work under Wayland, there is an open bug to fix it.  Most local X/Apps just work, but if there is networking or the X/app is doing something which breaks security ... like xdotool or screen capture ... then the effort is greater. Many old X/apps won't port to Wayland ever.  I'm worried that my xnee and cnee workflows will all need reworking under Wayland.

So, OBS make a big announcement when they had a release that supported Wayland with screen capture capabilities.  OBS is sorta huge just for screen capture.  The Gnome guys made a screen capture program that requires gstreamer to work.  I've always found gstreamer to be junk - perhaps it is just my initial use and all the bloat it had way back then, but since it is part of Gnome, I expect bloat. I've not been disappointed, so far.  Plus the Gnome people are evil, since they allow applications to ignore the window decorations provided by the WM.  Evil I say - pure evil. ;)

---

### Post by Skaperen on 2022-01-06
> **TheFu said:**
> 

Really, I'd say just to run SimpleScreenRecorder - try it out. It is pretty bonehead easy.

tried that.  it records video OK but audio was just silent.

---

### Post by Skaperen on 2022-01-06
> **TheFu said:**
> 1. yes.  It works.  May need to be more specific about the exact releases used for the host and the guest OSes, but I've used X11 on 18.04 with Wayland running in 21.04 accessing the VM using KVM-Spice and virt-viewer.

2. I don't know. They connect to the GPU, so if you have 2 GPUs, perhaps, but I honestly don't know.

3. Unknown.  Usually, when GUI apps that previously supported X don't work under Wayland, there is an open bug to fix it.  Most local X/Apps just work, but if there is networking or the X/app is doing something which breaks security ... like xdotool or screen capture ... then the effort is greater. Many old X/apps won't port to Wayland ever.  I'm worried that my xnee and cnee workflows will all need reworking under Wayland.

So, OBS make a big announcement when they had a release that supported Wayland with screen capture capabilities.  OBS is sorta huge just for screen capture.  The Gnome guys made a screen capture program that requires gstreamer to work.  I've always found gstreamer to be junk - perhaps it is just my initial use and all the bloat it had way back then, but since it is part of Gnome, I expect bloat. I've not been disappointed, so far.  Plus the Gnome people are evil, since they allow applications to ignore the window decorations provided by the WM.  Evil I say - pure evil. ;)

1.  i hoping to do that with VNC to access.  maybe that is how it is doing that.

2,  when running 2 Xs, one can "detach" from the screen hardware to allow the other to take over.  i hope Wayland can do that in some form.  long ago i would press Ctrl+Alt+F3 to switch out of X to a text screen.  i ran 3 instances of X and could switch to a different X.  i hope Wayland can do that.  FYI, back then those 3 Xs were started by the same user and had no problems.

3.  i will need both *xdotool* and _screen capture_.  Wayland designers should have a way to securely pass credentials to allow doing that.  there should be ways (defined protocols) to allow programs to "become" the human (screen, keyboard, mouse).  a randomly named file set up securely in the user's home directory (maybe in a subdirectory) that environment variable names might be secure enough to acquire credentials for that user instance of Wayland.

---

### Post by Skaperen on 2022-01-06
i figured out one issue why *ffmpeg* was not working.  the example command lines included a hard coded DISPLAY value of **:0.0** combined with some other stuff.  eventually i just put "$DISPLAY" there and it started recording video.  the example default of **:0.0** did not work for me.  my DISPLAY value is **:7.0**.  i have 17 users running right now ... 17 instances of X under control of lightdm.  maybe someday 17 instances of Wayland.

---

### Post by TheFu on 2022-01-07
The DISPLAY setting of :0 is for the first physical GPU. If you use virtual GPUs (like via VNC), then you'll need to manage the DISPLAY setting manually.
DISPLAY is really 
{IP}:{GPU}:{Monitor}  We leave the {IP} off, which becomes localhost automatically.
:0.0 <---- says GPU 0 with the first monitor.

The IP setting is used when using xdmcp ... like in the early 1990s with Xterminals (hardware).

If audio capture isn't working in SSR, check that that connected audio device is correct both for the output AND for the input to SSR.  There is an audio level meter in the preview mode of SSR, which should be pretty clear that audio is or is not being captured.  But for 17 different users, ffmpeg would certainly be the method I used.  I'd transcode as the capture happens - example transcoding options:
```
-vcodec libx264 -crf 22 -preset superfast -strict experimental -c:a libvorbis -q:a 6 -qscale:a 6 
```
On a Ryzen, this encodes around 8x normal playback speed, so it should easily handle 8 users and saves 50% disk per user.

---

### Post by Skaperen on 2022-01-07
when i saw ":0.0" in the example at first i did not recognize it as the DISPLAY value.  had they coded that as $DISPLAY then it would have worked for the video-only case.  once i recognized that and changed it, then video started working.  so that's been one problem all along but is no more.

as for the audio, i once tried plain audio-only recording and tried a few examples but nothing worked.  had i been the one to design the audio system i would have made sure there was a port to get an exact copy of what is being sent to the audio device, buffered up to a point, as configured, secure by default (a "--nosecurity" option would be available to use if you wanted anyone to get it).

i wish audio had been part of X all along.  but it's not too late to add it to Wayland.  audio should be thought of as part of the human interface, speakers and microphones, multiple channels (numbered and dynamically named) each.  then selectors for multiple human interfaces will be selecting both audio and video.

*edit:*

basically, i know nothing about selecting an audio source the equivalent of $DISPLAY.  some program may be using defaults.  it may even have an option to choose.  but i don't know enough to say where mine is other than "pulse".

---

### Post by TheFu on 2022-01-07
When X/Windows was created, computers didn't have speakers.  They only had beepers.  I don't recall any UNIX workstations prior to 1996 having speakers.  SGI did, but we never used them for that - they were just used for visuals.

When CDRoms were possible with computers, it was a hardware-only interface into the sound card.  Before that, they had a 3.5mm jack on the front of the CDROM player itself for audio music CD playback.

I understand that pulse audio and jack can provide complete local/remote and muxing of audio from sources anywhere the network reaches.  I don't know much more about it. Sorry.  I think Pulse is on the way out now. Fedora has a newer audio engine - after all, now that pulse is mostly stable after 11 yrs of crashes and other non-working situations - it is time to change it. ;(

---

### Post by Skaperen on 2022-01-07
so once a project becomes stable and there are no more updates, it is marked as no longer in development.  and that justifies replacing it.  so, what will Debian or Ubuntu replace Pulse Audio with and when?  Jack in 24.10?

---

### Post by DuckHook on 2022-01-08
> **Skaperen said:**
> so once a project becomes stable and there are no more updates, it is marked as no longer in development and that justifies replacing it.
I think you are conflating two different concepts: there are lots of projects that are stable enough that they don't qualify as being under 'active' development, but they are still actively maintained. One that comes to mind is ssh. It does all that it is supposed to do now, so we don't see any 'new' features being added. Yet, it is actively maintained with some big names behind it. Because it is so important (and elegant), I doubt it will ever be replaced.

The reason that X is a candidate for replacement is not because it is stable, but because it is kludgey, finicky, not actually that stable and, most of all, inherently insecure. In other words, there are too many negatives weighing against it to try salvaging it and a decision was made to replace it. (It should be obvious that the foregoing is laced through with my personal opinion, so please don't treat it as gospel).

I've had X crashes and strange behaviours over the years; I've yet to have a Wayland problem since switching to it, though I grant that I've only been using it for a little over a year. What X does have going for it is that it's been around a long time, so it's quirks and failings are well known and workarounds are in place. Since most systems don't change much after they're installed, most people understandably don't want to fix what ain't broken. There's a lot to be said for that approach.
> so, what will Debian or Ubuntu replace Pulse Audio with and when?  Jack in 24.10?
There is always talk of replacing PA. I haven't heard anything definitive for some time, so my uninformed guess is that it will be around for a while. It's another of those platforms that are complex and prone to problems, but now have known workarounds and achieved the status of "stable".

I've tried Jack and it is a fussy, finicky little beastie. I've found that the best way to use it is to install Ubuntu Studio and let the devs and the installer do the thinking/configuring for me. When trying it on my own, I always muck it up.

I don't want to send the wrong signal here: even though Ubuntu Desktop is moving to Wayland in its future releases, I think the X option will be around for a long while. While I've gotten comfortable with Wayland and see it as the wave of the future, X is so ingrained in the Linux ecosystem that I don't see it fading away anytime soon.

---

### Post by Skaperen on 2022-01-08
that sounds to me like a reason to not use Jack.  i want to always have literal control over every aspect of my computer.  that is a want but i am still far away.  it sounds (not a pun) like Jack would move me further away from that goal.

1. how well can you video record your Wayland display?
2. can you switch user without logging out, either to text mode or to a new to login user that is normally using Wayland?
3. if the system starts entirely in text mode, how could you start Wayland?

---

### Post by schragge on 2022-01-09
Just found this: [https://github.com/ColumPaget/screenrecord.lua](https://github.com/ColumPaget/screenrecord.lua)

---

### Post by DuckHook on 2022-01-09
> **Skaperen said:**
> that sounds to me like a reason to not use Jack.  i want to always have literal control over every aspect of my computer.  that is a want but i am still far away.  it sounds (not a pun) like Jack would move me further away from that goal.

You can always hand&#8209;tune it if you want. Like anything Linux, that's always an option and the audio gurus do it all the time. I found it too arcane for me, but then, I get lost with PulseAudio, so take what I say with a heavy dose of salt.
> &#8230;how well can you video record your Wayland display?
I don't want to mislead you here. I'm just getting my feet wet in the whole screen recording thing myself. You likely have way more experience in this than me.
> &#8230;can you switch user without logging out, either to text mode or to a new to login user that is normally using Wayland?
I don't quite understand what you are asking here. To my knowledge, if we're talking about the GUI desktop, then "switching users" always involves either logging out of the current session or doing the "switch user" thing in the tray. If so, then the new user can call up either X or Wayland at login, just like the initial user at startup. But the new user would have no access to the initial user's session. If we're talking CLI, then the usual su command works in the terminal, but I don't know how that helps for screen capture, because AFAIK different users cannot access each others' GUI sessions for security reasons. If we're talking about invoking another TTY, then launching from that into another user session, then that's always possible and is done all the time in the usual way <Ctrl>+<Alt>+<F2-5> then log in as user of choice, etc. But, again, no access to the initial user's session. There may be ways around this restriction. TheFu knows way more about that sort of stuff than I do.
> &#8230;if the system starts entirely in text mode, how could you start Wayland?
I've never had occasion to do something like that, so don't have personal experience. I suppose it's no different than working with X. You would have to invoke the display server from the command line. A web search turned up this: [https://stackoverflow.com/questions/31213773/how-to-start-gnome-wayland-session-from-command-line-tty](https://stackoverflow.com/questions/31213773/how-to-start-gnome-wayland-session-from-command-line-tty)

---

### Post by hk42 on 2022-01-10
It may be OT but I recently tested an HDMI to USB dongle and it may be a nice solution to
many problems:
It is cheap
Does sound too
Capture a lot of modern devices.
It is supported out of the box by W10 and Ubuntu 
OBS is the software I used.
It gets a bit hot so choosing a metal box and USB3 at least
for Power supply is a good idea.

---

### Post by mIk3_08 on 2022-01-10
> **Skaperen said:**
> can you describe the steps to start recording fullscreen?  can it be done by setting up a custom button that starts it (i can do that if it can be run as a command and no GUI). Wow! that can be more cooler using command and not using the graphical user interface. I haven't tested it yet using the command but maybe I'll be using that one later to explore the OBS app in my Linux Ubuntu Operating System. Thanks for the idea. cheers.

---

### Post by Skaperen on 2022-01-11
> **hk42 said:**
> It may be OT but I recently tested an HDMI to USB dongle and it may be a nice solution to
many problems:
It is cheap
Does sound too
Capture a lot of modern devices.
It is supported out of the box by W10 and Ubuntu 
OBS is the software I used.
It gets a bit hot so choosing a metal box and USB3 at least
for Power supply is a good idea.

i'm using a laptop with barely enough extra space for an external hard drive, wireless mouse, and a box of kleenex.  i've already considered getting a TV RF receiver to USB device but i don't have space for it.

---

### Post by Skaperen on 2022-01-11
i am not at all experienced with recording the screen.  i just recently got it half working (no audio).  so i will not be using it, yet.  once the audio problem is solved, then it will be a useful thing.

---

### Post by TheFu on 2022-01-11
I have an HDMI recorder device  (amazon item: B08SC8QFVC). It isn't tied to any computer, just sits between the computer HDMI output and whatever screen is going to display it.  1080i at 30fps.  Think the cheapo version I have from China was $65. Appear to be $50 now. It can only record stereo audio, no DD or DD+ or AC3 5.1 stuff - just stereo - so the audio input to it needs to be 2 channels only if you want that captured too. The resolution sent to the device needs to match a standard that a TV would know.  480p, 720p, 1080i with frame rates that also are standard for TVs. I think it records either 720p@60hz or 1080i@30hz.  I don't use the 1080 resolution, but have previously.  Lots of caveats with this specific device.  Always use externally powered storage. Use an HDCP filter for that sort of content. The start/stop recording is a manual button. No way that I know to delay the start or set the stop is possible. The REC button can be finicky and sometimes the connected storage becomes corrupted, so be certain to remove all the files you want to keep to a different storage device.

The HDMI recorder saves to USB connected storage. It supports only FAT32 or NTFS storage, so each chunk is 2GB in size ~ 20 minutes of 720p content.  It doesn't support live streaming.  To edit or playback the recorded video, copy the USB storage files off and merge the files for a specific show. I have a script that does it.  Encode_01.mp4 + Encode_01_002.mp4  + Encode_01_003.mp4  + Encode_01_004.mp4 ---> "Name of event recorded.mkv".  The mp4 container has barely compressed h.264 video and AAC stereo audio.  Using handbrake on this will easily reduce the file size 50% with no artifacts noticed in the smaller file.  Anything that can be sent to a monitor can be recorded, IME.

There are lots of these types of devices. Offloading the recording so it doesn't take any computer CPU really is good.

It can be used to record streaming audio too, if you like, but I typically use the browser to get the cURL location for audio files. Much easier and faster.

---

### Post by Skaperen on 2022-01-12
the only URL pattern i can find on Amazon.com uses s description before the product ID code.  o i don't know how to access that.

how about a command line script that you just give it that code and it fires up a preferred browser instance with the appropriate URL.

---

