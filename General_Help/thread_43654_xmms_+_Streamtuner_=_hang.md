---
title: "xmms + Streamtuner = hang"
date: 2005-06-22
forum: General Help
---

### Post by Flakes on 2005-06-22
Hey guys first time post. i just started using Ubuntu and i love it, learning new stuff constantly, and now that i have xmms and streamtuner on my system, i would love for it to work, but each and every time i try to connect to any SHOUTcast station, it will buffer and then hang when attempting to actually play the stream. any ideas on what's wrong? thanks  :)

*edit* there's something wrong with it beyond shoutcast, and it has nothing to do with xmms because i encounter the same problem using beep media player... am i missing something?

---

### Post by Flakes on 2005-06-22
[QUOTE=Flakes]Hey guys first time post. i just started using Ubuntu and i love it, learning new stuff constantly, and now that i have xmms and streamtuner on my system, i would love for it to work, but each and every time i try to connect to any SHOUTcast station, it will buffer and then hang when attempting to actually play the stream. any ideas on what's wrong? thanks  :)[/QUOTE]
 it has been 4 hours since i posted this and xmms is still sitting idle on my desktop... what is the command to force quit the application? it doesn't prompt a force quit when i right click xmms in the task menu and click "close"

---

### Post by Xian on 2005-06-22
[QUOTE=Flakes]Hey guys first time post. i just started using Ubuntu and i love it, learning new stuff constantly, and now that i have xmms and streamtuner on my system, i would love for it to work, but each and every time i try to connect to any SHOUTcast station, it will buffer and then hang when attempting to actually play the stream. any ideas on what's wrong? thanks  :)[/QUOTE]
It might not just be one thing, but for certain you will want to check and see if your output plugin is set properly. What is proper? Well, that depends on how your system is configured for sound. My system is set up as in [THIS](http://www.ubuntuforums.org/showthread.php?t=32063&highlight=multiple) thead. I would suggest that if you are having issues with XMMS as you described that you consider doing likewise.

To set the output plugin in XMMS you right-click on the interface and then:
Options > Preferences > Audio I/O Plugins

---

### Post by Xian on 2005-06-22
[QUOTE=Flakes]it has been 4 hours since i posted this and xmms is still sitting idle on my desktop... what is the command to force quit the application? it doesn't prompt a force quit when i right click xmms in the task menu and click "close"[/QUOTE]
```
$ sudo killall xmms
```

---

### Post by Flakes on 2005-06-23
thanks :) i've been looking and trying to figure out why xmms hangs every time i try to play streaming audio, and i downloaded just about every plugin for it from Synaptic... maybe im missing one or one is conflicting with another. here are the input plugins listed and enabled in the preferences menu:

libcdread.so
libcdaudio.so
libradio.so
libxmmsmad.so
libmodplugxmms.so
libmpg123.so
libvorbis.so
libxmms-flac.so
libsmpeg_xmms.so
libtonegen.so
libwav.so
libxmmssid.so
xmp-plugin.so

anyone have suggestions? thanks :)

*edit* i just discovered that xmms freezes no matter what i try to play, even if its an mp3 locally on my hard drive... :( now i realize the problem is beyond xmms... beep media player does the exact same damn thing... any ideas?

---

### Post by oneybm on 2005-07-09
I just installed Hoary this morning and tried the exact samething with the exact same results.  Sound does work on my machine as the startup sound works and so do the notifications of applications being opened or closed.  If I use XMMS it buffers and then suddenly stops and then I can do nothing but close the program.  It doesn't seem to matter how I configure the output plugin to work I still get no sound at all.  However, I have used Suse 9.2 on this system and it worked just fine.  Perhaps I need to download XMMS from another repository instead of using the Synaptics installer.  I don't know if that would make a difference but it's the only other idea I have at the moment.

Any suggestions would be much appreciated and thank you in advance.

---

### Post by ibanez88 on 2005-07-10
[http://ubuntuforums.org/showthread.php?t=29338](http://ubuntuforums.org/showthread.php?t=29338)

---

### Post by dwaldie on 2005-07-10
if any sound programs just hangs just enter the command killall esd.

That should work.

David Waldie

---

### Post by oneybm on 2005-07-12
Yeah that would be how you can stop the program but it doesn't fix the problem of it not playing.  I finally fixed mine after trying the esd fix while looking through the Unofficial Guide.  Don't misunderstand this, that guid is phenomenal and I love it.  It has been a big help.  But what I had to do to take care of XMMS not streaming was to go to the sound manager for the entire system and change the output to ALSA.  Of course I'm in XP now so I can't recall exactly where it is but I can repost later once in Ubuntu and update that.  Works great now though.  

On to other setup problems.  ;-) 

Oneybm
Semi Noob to Linux

---

### Post by oneybm on 2005-07-12
Finally logged back into linux.  The trick was to change the Multimedia Systems Selector.  Under Audo change the Output to ALSA and it was good to go.

Thanks again.

---

### Post by phubai on 2005-07-19
I had the same problem. Changed the output to Alsa, clicked play on XMMS and it froze. I entered command to killall esd, and it started working. 

pb

---

