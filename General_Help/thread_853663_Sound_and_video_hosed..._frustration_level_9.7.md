---
title: "Sound and video hosed... frustration level 9.7"
date: 2008-07-08
forum: General Help
---

### Post by snurfle on 2008-07-08
OK... first the system:
Asus A7V8X-X mobo
2 Gb RAM
AMD Athlon 2200XP CPU (no overclocking)
Nvidia FX 5200 8X AGP + 256Mb Vram
Dual booting 8.04, WIN XP
Ummm... Monitor = Westinghouse LCM 22w2 (D-sub)
Kernel 2.6.24.19
VIA8235 integrated sound into 5.1 speakers

Been running Ubuntu for about a year and a half.
And, as I'm sure gets mentioned here all the time, "Windoze runs fine".

Back story... Christmas 2007, I got my son a music keyboard with a USB connection that ostensibly lets it run MIDI.  (Years ago, Win3.1 days, that meant the special cable to the soundcard...)
Fiddled around with it for a week, ended up installing Rosegarden (iirc - whatever the Ubuntu-friendly sequencer is), which also required 'QT Jack interface' and 'Pulse audio device chooser' to be installed (don't ask why... lots of late nights on the interwebs gave me lots of iffy advice.); my sound has never been the same since...  I tried to stumble my way through it, but could never get a DVD to play correctly, as the 5.1 channels were totally mucked up (Front/Rear/LFE coming out of random speakers, no center channel at all...), the start up sound went away...  In my efforts to fix it, I installed the Gnome Alsa Mixer, and manually editing some config files (long-forgotten by now) and tried re-installing the drivers...  suffice it to say I totally hosed it up.
During this time, the kernel went through some updates.  Every time it updated, I would have to re-compile the nvidia driver if I wanted all the pretty eye candy (if I wanted higher than an 800x600 display!)
Somewhere in the past 6 months, I also noticed something new... any time there were updates to install, I would get a "subprocess post-removal script returned error exit status 2" and a mention of Nvidia-glx. (I am currently using Nvidia driver 173.14.05, btw)

So... in order to isolate the sound troubles, I tried uninstalling RoseGarden... but I was reminded whilst doing so, that adding/removing anything using the add/remove launcher would also yield the "script returned error exit status 2" message.

Today, the add/remove manager would start, but attempting to use it at all resulted in a never-ending delay.
"$sudo gnome-app-install" gave the same behaviour, but the terminal also revealed a hiccup related to nvidia-glx in the output as well.
An hour of searching for *that* online gave me a suggestion to "$sudo rm /usr/lib/xorg/modules/libwfb.so"
Lo and behold, no more nvidia-glx woes; I was then able to "$sudo apt-get install nvidia-glx-new", which seems to be the underlying culprit to the "script returned error exit status 2" issue.
But then I rebooted.

Welcome to 800x600 again.

Here's my current status.
I turn on my machine and fire up Ubuntu.
The display comes up shifted about 2" to the right, because (if memory serves) Ubuntu + nvidia does not grab the correct EDID info from the Westy monitor (this was working before I upped to Hardy).
I'm back to the 800x600 rez, and 1680x1050 is not available.  (the only fix I have found to this is to ctrl+alt+F1, "$sudo /etc/init.d/gdm stop", and reinstall the nvidia driver with "$sh sudo NVIDIA-Linux-x86-173.14.05-pkg1.run" and reboot.
The keyboard numlock is lit, but the keypad does not work unless I poke the numlock key three times (serves me right for using a mostly-numeric password!); it's done that ever since I started using Ubuntu, but today it's just one more thing in a long list of things that just tick me off. (kidding... but it is annoying, and I can't find a fix anywhere!)
And, no startup sounds, no voices if I watch a movie...
($ cat /proc/asound/cards returns:
 0 [V8235          ]: VIA8233 - VIA 8235
                      VIA 8235 with AD1980 at 0xe000, irq 18 )

and here is "/etc/modules"
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
fuse
lp
Intel536
snd-via82xx



So... If anyone has any tips for me...
I would like to completely wipe all sound-related 'stuff' from my machine and just start from scratch (he never touches the music keyboard, anyway!) and get the sound working again, preferably with the 5.1 mapped correctly.
I would like to know what is the deal with the nvidia driver... do I need to re-compile every time the kernel gets updated? Isn't there some way to automate that?
The shifted display is just nuts... I don't know if Ubuntu is shifted right, or if windows is shifted left.  Last year, though, is when Hardy showed up shifted right, so I'm pretty sure it's a Nvidia+Ubuntu+Westy issue.

I know I should be able to take a deep breath and start on these one at a time, but it seems like every time I think I have it figured out, it's just a momentary thing that breaks a dozen other things, or that futzes something that I don't see until a week or a month later...  And like I said... my frustration level right now is at an all-time high, so I am going to hope some kind soul(s) take pity on me and... help.

I have attached:
dmesg output
xorg.0.log (from current session)
xorg.conf (from current session)
xorg.conf.dontdelete (a backup from when I finally got nvidia to give me 1680x1050 last winter!)
lsmod grep snd output.txt

Am I missing anything?

Thanks a bazillion.

---

### Post by snurfle on 2008-07-08
Just an afterthought... is the "subprocess post-removal script returned error exit status 2  Nvidia-glx"  message something that shows up with the newer driver?  This is one of those things that could've been caused by a video driver update, but went unnoticed for days or weeks...

---

### Post by snurfle on 2008-07-09
Update:
After playing with it for several hours, I have also found that
"$nvidia-settings" results in "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."
even after running "$sudo nvidia-xconfig" and rebooting.
Further, running "$nvidia-settings" always terminates with
"ERROR: Failure while closing file '/home/greg/.nvidia-settings-rc'"
I'm ready to just accept no sound and live with it, but the video is really ticking me off.  Mostly, I think it's because my eyes are getting tired after staring at (blurry) 800x600 on a 22" monitor!

---

### Post by snurfle on 2008-07-09
Another update
And this is new...
Firefox 3 will not allow me to D/L the newest nvidia driver (173.14.09).  Clicking on the link on Nvidia's page causes FF to close.  Immediately.  No warning, no reason, no message.  It just closes.
Trying the 'right-click save-link-as' results in...  Absolutely Nothing Happens.  Right clicking does as much good as doing nothing at all.  No response, no pop-up menu... nothing.
But normal left-click causes FF3 to just go away.
So add that to my list of crap.

I've been a fanboy of Linux since first installing Mandriva something like 4 years ago... but this is really getting ridiculous.
Is there any hope for this, or do I need to just...
sorry.  I won't turn this into a rant.  I'm just incredibly frustrated at the whole thing right now, I've been fussing with it for almost 8 hours straight, and watching the new Firefox crash and burn like that, out of the blue, is making me want to just blow the whole thing away and go back to XP full-time.  This is insane.

---

### Post by snurfle on 2008-07-09
OK.
Rebooted into windows, downloaded the nvidia driver, rebooted into Ubuntu, copied the driver over, went through the incantations to install it (btw... Am I doing it right?  ctrl-alt-f1, 
"sudo /etc/init.d/gdm stop", 
"sudo sh NVIDIA-Linux-blah-blah-pkg1.run"
run through the configuration 'stuff', accepting all the defaults...
reboot

I am now able to get 1024x768 at least, which makes everything all squishy looking, but that's just from trying to put a standard h/w display on a 1680x1050 monitor.  I can put up with it like this.

But.

No compiz functions at all.  Again I guess I can put up with it, it's a darn site better that 800 x 600.

And, running 'nvidia-settings' still returns "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."
and 'sudo nvidia-xconfig' gives me errors about my mouse and keyboard (because obviously installing a new video driver will break the mouse and keyboard settings!)

Rebooting still gives me no compiz functions, even though the 'advanced desktop effects settings' appears to be all set up the same way it was before everything else took a dump.  But again, I just need a working computer, the eye candy really doesn't matter at this point.
And attempting to install anything via the add/remove launcher is back to giving me the "script returned error exit status 2" from nvidia-glx.  But at least it's not going into infinite wait status any more, so I'll call that one fixed.

So forget the video problems, I can put up with it like this.  It's rebooted into a working desktop several times in a row, so I can live with it like this.

But I still need to know what (if anything) can be done about the sound.

Anyone?

---

### Post by snurfle on 2008-07-09
OK... maybe what I want to do can't be answered so easily.
So let me try this, instead.
Let's say I am going to take out my sound card and put in a whole different new one.
How do I get rid of all the settings and drivers and such for the old one and put in all the drivers and settings and such for the new one?
How do I configure it (the new one, that is) to run 5.1 just like Windows?

---

### Post by itkeepsrepeating on 2008-09-01
As far as your vid card goes, I can suggest a program named envy-ng by [I think] a guy named Alberto Milone. Quick googling for the instructs from his site. It autodetects your video card and installs the proper drivers, along with a config utility for it. Supports NVidia and ATI cards.

I have same motherboard. Same sound chip, same lack of sound. It's my only problem. 

My lspci and lshw show the same relevant parts, no errors. I had a bobo-extra-cheapo sound card in this machine as a workaround, but have just now slapped it in a secondary box for another person. All I need is sound. Perhaps someone can chime back in to help us now that it's not just you complaining. I, too can supply any relevant outputs and whatnots necessary.

---

