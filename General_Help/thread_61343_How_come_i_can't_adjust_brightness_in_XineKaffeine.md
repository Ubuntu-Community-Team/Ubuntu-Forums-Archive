---
title: "How come i can't adjust brightness in Xine/Kaffeine?"
date: 2005-08-31
forum: General Help
---

### Post by sk545 on 2005-08-31
I can't adjust brightness/contrast, etc in either xine-ui or kaffeine...does anyone else have the same problem?  In xine-ui, the sliders aren't even there to adjust, and in kaffeine, the sliders are there but nothing changes in i move them left to right.  Could it be a video driver issue?  I am using the drivers from nvidia.com 1.0-7676.  The only other thing i can think of is xorg.conf and some setting there.

Thanks.

---

### Post by arnieboy on 2005-08-31
[QUOTE=sk545]I can't adjust brightness/contrast, etc in either xine-ui or kaffeine...does anyone else have the same problem?  In xine-ui, the sliders aren't even there to adjust, and in kaffeine, the sliders are there but nothing changes in i move them left to right.  Could it be a video driver issue?  I am using the drivers from nvidia.com 1.0-7676.  The only other thing i can think of is xorg.conf and some setting there.

Thanks.[/QUOTE]
everytime u make a change to video driver settings like brightness etc, u have to save and exit your media player (xine in this case) and then start it again for the changes to take effect. have u tried that?

---

### Post by sk545 on 2005-08-31
you mean that if i change the brightness in kaffeine, i have to close it then restart it for it to work?  That didn't work.

I haven't changed anything in the nvidia driver settings or in xorg.cong.

---

### Post by arnieboy on 2005-08-31
[QUOTE=sk545]you mean that if i change the brightness in kaffeine, i have to close it then restart it for it to work?  That didn't work.

I haven't changed anything in the nvidia driver settings or in xorg.cong.[/QUOTE]
what kind of computer are u using? laptop/desktop? if its a desktop, u can change the screen brightness from the monitor. if its a sony VAIO laptop for example, I can give u a step by step method to load separate modules and control the screen brightness. I cant guarantee that it will work however, cuz I dont work on any laptop. u can go ahead and try though if u are interested.

---

### Post by sk545 on 2005-08-31
its a desktop.  I don't want to have to change the entire screen's brightness through the monitor controls, just want it so that xine/kaffeine will change the playing video's brightness thats in a window.  Is no one else having this problem?  Are you able to set the brightness through xine's controls on the fly?

---

### Post by arnieboy on 2005-08-31
[QUOTE=sk545]its a desktop.  I don't want to have to change the entire screen's brightness through the monitor controls, just want it so that xine/kaffeine will change the playing video's brightness thats in a window.  Is no one else having this problem?  Are you able to set the brightness through xine's controls on the fly?[/QUOTE]
I will try tonight and let u know when I get back home to my ubuntu box from work .

---

### Post by arnieboy on 2005-08-31
[QUOTE=sk545]its a desktop.  I don't want to have to change the entire screen's brightness through the monitor controls, just want it so that xine/kaffeine will change the playing video's brightness thats in a window.  Is no one else having this problem?  Are you able to set the brightness through xine's controls on the fly?[/QUOTE]
ok dude, brightness controls work like a charm on my desktop from the xine-ui. I have an nvidia card as well. are u sure xine is using the xv driver?
also post the contents of your /etc/X11/xorg.conf file

---

### Post by sk545 on 2005-08-31
man, i just got back from work too...midnight right now...soo tired...

Anyhow, if the controls work for you, then i dunno why mine's wont.  

I am not sure what xine is using as a driver, but here is the ouput from 'xine-check':

```

~$ xine-check
Please be patient, this script may take a while to run...
[ good ] you're using Linux, doing specific tests
[ good ] looks like you have a /proc filesystem mounted.
[ good ] You seem to have a reasonable kernel version (2.6.13)
[ good ] intel compatible processor, checking MTRR support
[ good ] you have MTRR support and there are some ranges set.
[ good ] found the player at /usr/bin/xine
[ good ] /usr/bin/xine is in your PATH
[ good ] found /usr/bin/xine-config in your PATH
[ good ] plugin directory /usr/lib/xine/plugins/1.0.0 exists.
[ good ] found unknown plugin: xineplug_flac.so
[ good ] found input plugins
[ good ] found demux plugins
[ good ] found decoder plugins
[ good ] found video_out plugins
[ good ] found audio_out plugins
[ good ] skin directory /usr/share/xine/skins exists.
[ good ] found logo in /usr/share/xine/skins
[ good ] I even found some skins.
[ good ] /dev/cdrom points to /dev/hdc
[ good ] /dev/dvd points to /dev/hdc
[ good ] DMA is enabled for your DVD drive
[ good ] found xvinfo: X-Video Extension version 2.2
[ good ] your Xv extension supports YV12 overlays (improves MPEG performance)
[ good ] your Xv extension supports YUY2 overlays
[ good ] Xv ports:  YUY2 YV12 UYVY I420 YUY2 YV12 UYVY I420

```

I am also attaching xorg.conf and ~/.xine/config below.

Thanks.

---

### Post by arnieboy on 2005-09-01
[QUOTE=sk545]man, i just got back from work too...midnight right now...soo tired...

Anyhow, if the controls work for you, then i dunno why mine's wont.  

I am not sure what xine is using as a driver, but here is the ouput from 'xine-check':

```

~$ xine-check
Please be patient, this script may take a while to run...
[ good ] you're using Linux, doing specific tests
[ good ] looks like you have a /proc filesystem mounted.
[ good ] You seem to have a reasonable kernel version (2.6.13)
[ good ] intel compatible processor, checking MTRR support
[ good ] you have MTRR support and there are some ranges set.
[ good ] found the player at /usr/bin/xine
[ good ] /usr/bin/xine is in your PATH
[ good ] found /usr/bin/xine-config in your PATH
[ good ] plugin directory /usr/lib/xine/plugins/1.0.0 exists.
[ good ] found unknown plugin: xineplug_flac.so
[ good ] found input plugins
[ good ] found demux plugins
[ good ] found decoder plugins
[ good ] found video_out plugins
[ good ] found audio_out plugins
[ good ] skin directory /usr/share/xine/skins exists.
[ good ] found logo in /usr/share/xine/skins
[ good ] I even found some skins.
[ good ] /dev/cdrom points to /dev/hdc
[ good ] /dev/dvd points to /dev/hdc
[ good ] DMA is enabled for your DVD drive
[ good ] found xvinfo: X-Video Extension version 2.2
[ good ] your Xv extension supports YV12 overlays (improves MPEG performance)
[ good ] your Xv extension supports YUY2 overlays
[ good ] Xv ports:  YUY2 YV12 UYVY I420 YUY2 YV12 UYVY I420

```

I am also attaching xorg.conf and ~/.xine/config below.

Thanks.[/QUOTE]

ok, see if this works for u or not. I think the brightness control not working has got to do with the default refresh rates that linux is using on your comp. u gotta find out the horizontal and vertical refresh rates from the monitor manual (look for it on the manufacturer's website when u key in the model number) and plug them in under section "Monitor" in xorg.conf. make sure u make a backup of ur xorg.conf before u replace it.
The "monitor" section will look  something like this:
```
Section "Monitor"
	Identifier	"E19CRT1"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-120
```
with the horizontal and vertical refresh rates as u plug them in.
after u save and exit, restart x-server. If X server crashes dont panic. just copy back your xorg.conf backup on to /etc/X11/xorg.conf and restart your comp.

---

### Post by sk545 on 2005-09-01
thx for pointing that out, i didn't know that my xorg.conf didn't have the refresh rates in it.  However, that didn't fix the problem. :(

I do get a error with mplayer when i do brightness/contrast, etc:

```
Video attribute 'contrast' is not supported by selected vo & vd. 0 55%
Video attribute 'brightness' is not supported by selected vo & vd. 48%
Video attribute 'hue' is not supported by selected vo & vd..2% 0 0 48%
Video attribute 'saturation' is not supported by selected vo & vd. 48%
[code]

The only way i can adjust brightness with mplayer is if i do something like this:

[code]
mplayer -vf eq=20:50 your_movie.mpg

```

I have looked high and low for a command similar to that for xine, but haven't found it.

---

### Post by sk545 on 2005-09-01
thx for pointing that out, i didn't know that my xorg.conf didn't have the refresh rates in it.  However, that didn't fix the problem. :(

I do get a error with mplayer when i do brightness/contrast, etc:

```
Video attribute 'contrast' is not supported by selected vo & vd. 0 55%
Video attribute 'brightness' is not supported by selected vo & vd. 48%
Video attribute 'hue' is not supported by selected vo & vd..2% 0 0 48%
Video attribute 'saturation' is not supported by selected vo & vd. 48%

```

The only way i can adjust brightness with mplayer is if i do something like this:

```

mplayer -vf eq=20:50 your_movie.mpg

```

I have looked high and low for a command similar to that for xine, but haven't found it.  Another thing to point out is that i am using a PCI express video card.  Could that be the "problem."?

---

### Post by sk545 on 2005-09-04
bump, anyone?

---

### Post by moopere on 2005-09-10
[QUOTE=sk545]bump, anyone?[/QUOTE]

Yeah, looks like a bug in xine, I'm getting the same problem here with an nvidia 5700 using the non free drivers.  I'll try doing this with the nv driver on the off chance its a nvidia problem.

Cheers,
Craig

---

### Post by sk545 on 2005-09-10
wow, finally someone else with the same problem.  I think i have posted this in like 4 separate forums, and no one even came forward to say they were having the issue.  Thx sooo much for verifiying.   :)

I did file a bug with bugzilla a while ago, but its left as 'Unconfirmed':

[https://bugzilla.ubuntu.com/show_bug.cgi?id=13275](https://bugzilla.ubuntu.com/show_bug.cgi?id=13275)

---

### Post by moopere on 2005-09-11
[QUOTE=sk545]wow, finally someone else with the same problem.  I think i have posted this in like 4 separate forums, and no one even came forward to say they were having the issue.  Thx sooo much for verifiying.   :)

I did file a bug with bugzilla a while ago, but its left as 'Unconfirmed':

[https://bugzilla.ubuntu.com/show_bug.cgi?id=13275](https://bugzilla.ubuntu.com/show_bug.cgi?id=13275)[/QUOTE]


Hmm.  I did close down my X and reconfigured xorg.conf to use 'nv' instead of nvidia module.  Restarted X, now brightness works (aha! I say).

Ok, to prove it to myself, I reconfigure xorg.conf again, back to nvidia, then restart X - and brightness works!!

Smells fishy eh?  I think that the nv driver has programmed something in the chipset which stayed that way after I ran the nvidia driver again.  I will test again tomorrow with a cold boot and see if anything shows up.

For now, I am more suspicous of the 7667 nvidia driver than xine.

Cheers,
Craig

---

### Post by sk545 on 2005-09-11
That didn't work for me. :(  I did change the driver from 'nvidia' to 'nv' and rebooted, still the brightness doesn't work in xine or kaffeine.  Going back to 'nvidia' didn't help either.

---

### Post by sk545 on 2005-09-13
Found my answer:

> More modern Geforce6 cards like the 6200/6600(GT) and other recent models (including the Geforce7) don't contain hardware overlay support anymore, that's the reason you can't change all these settings.

[http://www.nvnews.net/vbulletin/showthread.php?p=693350#post693350](http://www.nvnews.net/vbulletin/showthread.php?p=693350#post693350)

That REALY SuCKS.

Thx for the help though, moopere.  BTW, what video card are you using?

---

