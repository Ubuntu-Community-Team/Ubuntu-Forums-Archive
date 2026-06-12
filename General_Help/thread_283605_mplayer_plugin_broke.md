---
title: "mplayer plugin broke?"
date: 2006-10-24
forum: General Help
---

### Post by Bloch on 2006-10-24
My mplayer plugin stopped working after the recent update. It was not detected when I typed 
about:plugins
in the address bar.
However when I uninstall and reinstall nothing changes. I tried a lot of things (including letting Automatix handle the installation) and nothing worked. Synaptic claims the plugins are there and uptodate; but Firefox doesn't see them.

I've searched through the forum but the info is quite old and doesn't help.

I would appreciate any help, but I would also like to know if this is a bug or if other people have the same problem. I do everything by synaptic: why should my system suddenly break?

It might be significant, but after the installation symlinks are created 

The file mplayerplug-in-wmp.xpt in the directory 
/usr/lib/firefox/plugins   links to:
/usr/lib/firefox/plugins/mplayerplug-in-wmp.xpt

And there are 11 such apparently self-linking files in the same directory. These disappear when I uninstall mplayer plugin, and reappear when I install it again. Nautilus reports them as 
Type: Link (broken)

Methinks this is a bug

---

### Post by Bloch on 2006-10-24
/bump

---

### Post by Bloch on 2006-10-24
Any takers? Anyone with the same problem? Why does apt-get install broken symlinks?

---

### Post by spamzilla on 2006-10-29
I am having the same problem in FIrefox 2. Even though i know I have mplayer and the plugin installed, I still cannot watch certain videos on websites.

Has anyone found a fix for this?

---

### Post by jongkind on 2006-10-29
Can it be related to this (that worked for me)?

[http://www.ubuntuforums.org/showthread.php?t=284927](http://www.ubuntuforums.org/showthread.php?t=284927)

---

### Post by spamzilla on 2006-10-29
tht didnt fix my problem :/

I think it may have to do with my mplayer file not being linked to my firefox 2 file. How do I do this?

---

### Post by jongkind on 2006-10-29
> **spamzilla said:**
> tht didnt fix my problem :/

I think it may have to do with my mplayer file not being linked to my firefox 2 file. How do I do this?

I notice that you use Dapper, while I'm on Edgy. I guess that does not make to much of a difference.

What you can do is (assuming that you're in Ubuntu):

[LIST]
[*]from terminal: sudo nautilus --no-desktop (nautilus opens as root)
[*]Browse to /usr/lib/mozilla/plugins
[*]Assuming that you installed mplayer: make a link of each "mplayerplug-in" file that you see there.
[*]Copy those links to /usr/lib/firefox/plugins
[*]Remove the words "link to" from the filenames of those links
[*]Restart firefox
[*]Verify whether MPlayer works.
[/LIST]

I hope this helps.

---

### Post by tommcd on 2006-10-30
I am having a similar problem on edgy. If I try to play a mpeg video with mplayer, it just crashes. I can play mpegs on totem and vlc, so I assume it is not a codec problem. Also, I cannot stream mpegs at all in firefox.
Jonkind, will ypur solution help my problem? And how do I remove the words "link to" from the filenames of those links, as you stated in your previous post?
Mplayer plays other codecs (wmv, avi) just fine, but not mpeg.

---

### Post by jongkind on 2006-10-31
> **tommcd said:**
> I am having a similar problem on edgy. If I try to play a mpeg video with mplayer, it just crashes. I can play mpegs on totem and vlc, so I assume it is not a codec problem. Also, I cannot stream mpegs at all in firefox.
Jonkind, will ypur solution help my problem? And how do I remove the words "link to" from the filenames of those links, as you stated in your previous post?
Mplayer plays other codecs (wmv, avi) just fine, but not mpeg.

The method that I described will likely solve your problems with streaming media in Firefox. I don't think it will help the mpeg issue. 

You can remove the "link to" from the filename by right-click the filename, choose the rename option and remove the link to words.

---

### Post by tommcd on 2006-11-01
Jongkind, when I right-click on the file name (mplayerplug-in-gmp.so and mplayerplug-in-gmp.xpt) there is no "link to" to remove, just the file name itself. I also noticed that you can 'fix' the 2 broken plugins by creating dummy files with the same names in /usr/lib/mozilla/plugins. Unfortunately this did not fix my problem.
If I launch mplayer from terminal and try to play a mpeg video I get this error:


MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3200+ (Family: 15, Model: 47, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.



Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.

** (<unknown>:21613): CRITICAL **: mist_draw_border: assertion `shadow_type != GTK_SHADOW_NONE' failed
(this repeats many times, then)

Playing /home/tom/01.mpg.
MPEG-PS file format detected.
VIDEO:  MPEG1  448x256  (aspect 1)  29.970 fps  1000.0 kbps (125.0 kbyte/s)
==========================================================================
Trying to force audio codec driver family hwmpa...
Opening audio decoder: [hwmpa] MPEG audio pass-through (fake decoder)
AUDIO: 44100 Hz, 2 ch, mpeg2, 64.0 kbit/4.54% (ratio: 8000->176400)
Selected audio codec: [hwmpa] afm: hwmpa (MPEG audio pass-through for hardware MPEG decoders)
==========================================================================
==========================================================================
Trying to force video codec driver family dshow...
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 448 x 256 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
alsa-init: using device default
alsa-init: format mpeg2 are not supported by hardware, trying default
alsa: 48000 Hz/2 channels/4 bpf/65536 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
[format] Sample format big-endian MPEG-2 not yet supported 
Couldn't find matching filter/ao format!
Starting playback...

I've tried selecting every video output device and codec option in mplayer and I still get this. I can play mpegs with totem and vlc, and mplayer works fine with wmv files. I can't figure this out.

---

### Post by jongkind on 2006-11-02
tomm cd,

The instructions above indicated that the words "link to" must be removed from the **links** from each "mplayerplug-in" file that you **copied** to the /usr/lib/firefox/plugins folder. That indeed happens via re-naming that file. I expect that when you re-read these instructions and follow each step that it becomes clear to you.

---

### Post by Anwar Farooq Qadri on 2006-11-11
Please tell me how i can play mp3 and dat files in ubuntu without conversion.

---

### Post by mavsman78 on 2006-11-12
One reason the Mplayer plugin might not be working is because it's only tested to work with Firefox 1.5. Each extension has a code in it telling FF which versions it is compatible with. The only thing this means is that the developer of the extension has only tested it up to a certain version.

A way around this is to install the MR Tech extension. You can get it from here: [https://addons.mozilla.org/firefox/421/](https://addons.mozilla.org/firefox/421/)

Once installed, you can re-download the Mplayer extension from here: [http://prdownloads.sourceforge.net/mplayerplug-in/mplayerplug-in-0.3.xpi?download](http://prdownloads.sourceforge.net/mplayerplug-in/mplayerplug-in-0.3.xpi?download)
There will be a checkbox asking if you want to ignore the maxversion or something like that. Make sure that box is checked.

Finally, you may have to delete the totem plugins from your /usr/lib/firefox/plugins directory.

I hope this helps.

---

