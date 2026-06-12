---
title: "Ubuntu Experience - Day 1"
date: 2007-05-05
forum: General Help
---

### Post by bbarcelo on 2007-05-05
I've just installed Ubuntu and have been using it for less than 24 hours now. I'm a novice nix user, not a beginner, but that said, it's been a long while since I've done much besides host a server with Apache or something here and there.

I have a file server that utilizes 10+ hard drives at one time and was having stability issues in Win Server 2003. It finally got to the point where I really needed to make the switch and finally did - to Feisty Ubuntu. I first tested the LiveCD to see if it would recognize all these drives across the multiple IDE and SATA controllers and, suprisingly enough, it did a great job.

So here I am now, I've configured Samba, installed one app, and used the Ubuntu Restricted Drivers Manager to install the nVidia drivers (Oh, and VNC configured correctly). The computer I'm using is as follows (short version):
CPU: AMD Athlon64 3000+
RAM: 1.5GiB Mixed DDR (@ DDR2700)
Motherboard: Soltek (Don't want to bother looking up the exact model since I forgot)
Controller Cards: Highpoint, Western Digital, and Silicon
Graphics Card: Nvidia MX420 (I can hear the sighs already)
No CD/DVD Drive. No floppy. Two PSUs that work great in tandem.

I like the look and feel of Ubuntu, though it feels a little sluggish on this machine that I consider to be pretty high end of a basic Ubuntu install. That aside though, the disk performance seems to be on par with that I achieved in Server 2003. However.. In Server 2003 my computer blue-screened, something it obviously can no longer do and THE primary reason I made the switch. While I've been writing this forum post though, my Ubuntu machine has decided to do two things, the only two things I've found wrong thus far with my switch to Linux, but GIANT problems nonetheless.

1. Kicking me out to the login screen:
[INDENT]This happens both through VNC and while using the computer with a monitor and keyboard. Not really sure why this is happening. Checked power management settings, the only real direction I had found for a fix, and everything was OK there. So this is still going on and, speak of the devil, just happened. Logging back in (which must be done at the machine) usually results in slow OS loading times and is pretty annoying to have to go and do.[/INDENT]
2. Locking up:
[INDENT]I think this is a severe issue related to my Nvidia MX series graphics card. While the graphics card inside this computer really doesn't matter, I need something that won't be interferring and crashing the machine constantly. This happened at the beginning of this post and has been happening quite a bit in the last <24 hours. Probably somewhere around 10-15 times that I have to do a hard restart. This is VERY aggravating.[/INDENT]

Attempts to fix the Lock Ups:
I've tried modifying my xorg.conf file with the following options:
NvAGP 0
RenderAccel Off
IgnoreDisplayDevices DFP,TV
NoRenderExtension Off
AllowGLXWithComposite Off

So, please, someone provide some insight that I might be able to resolve these problems and continue life as a happy nix user. I really do not like the idea of switching back to the (more stable given my conditions) Server 2003 OS.

To any Admin who saw this post in the Absolute Beginner section, please delete that post. I think its better suited and will get better attention here.

---

### Post by tgalati4 on 2007-05-06
Seems like a hardware problem.  Try reseating memory, cleaning out all of the dust, reseating ribbon cables.

I had an Ubuntu Dapper machine running for 165 days straight.  I had about 100 updates to perform and I had to replace the UPS battery.  I found the power connector to the disk drive had vibrated loose.  Make sure that power and ribbon cables to all drives are tight.  

You can choose not to run the xserver when not needed.  Just type startx at a terminal prompt to restart it.  This will free up some CPU cycles.

Try installing an old, crappy VGA video card.  If this is a headless server, then you will need something to drive VNC with.  If you feel the built-in video is causing a problem, then you can probably turn it off in BIOS.

Try running memtest overnight.  It's located in the options section of the Live CD.

---

### Post by bbarcelo on 2007-05-06
No onboard graphics card, so that's out.
One of the few programs I'll be running requires X server as there is no non-GUI version of the program available.
Went ahead and checked all the cables.

Guess I should have mentioned I already ran memtest on the current RAM configuration several times both now and when I first installed the RAM. Also tried using the only other graphics card I have that's AGP (I have no PCIs) - a Radeon 9800Pro - and seem to be getting the same problem. I was able to CTRL+ALT+F1 once and discover that there was a kernel panic error. I'm still somewhat new to nix but from what I understand this is the equivalent of a blue screen in Windows. I think that the "random lock ups" I have been experiencing are really all kernel panics. Don't really know what to do about that though. Guess I ruled out the nVidia graphics card as being the problem.

I'm feeling like Windows 2003 really offered me better system stability still, though I'm still thinking about trying the previous version 6 build of Ubuntu, just hate to have to reinstall and I like the way version 7 looks (I've heard 6 isn't as nice in terms of ease-of-use). Still looking for alternate solutions however...

-Distraught Ubuntu Fan

---

### Post by nalmeth on 2007-05-06
I think it sounds like a problem with the Nvidia driver.

Have you tried going back to the nv driver to see if it recurs? Do you need the Nvidia driver for any reason?

Do you also have an onboard card, or is the MX420 the only graphics card period?

You could try installing the newer Nvidia driver if you do really need it, there is some documentation on that at doc.gwos.org, and at wiki.ubuntu.com I believe.

EDIT: just saw your new post, I guess that might rule out the graphics problems. I'm not sure how to approach your problem. 
I don't think going back to 6.06 will help anything. Are you using the 64-bit install?

---

### Post by bbarcelo on 2007-05-06
I think I answered most of the questions in my last post, must have both been posting at the same time, so refer to that for the information you're looking for. Didn't make any attempt to do a non-automatic-Ubuntu install of the nVidia drivers to address that.

Also, is there a way to have my xorg.conf reconfigured automatically by Ubuntu (as is done during the install?). I reconfigured X myself but find that I did not do as good a job as Ubuntu did and would like to have it automatically reconfigure X.

EDIT: I am using the 64bit Install.
EDIT2: I took out a stick of RAM as well to see what would happen.. Will post results of this. (Memtest said the RAM was good..)

---

### Post by nalmeth on 2007-05-06
To redo the xorg config, use this:
sudo dpkg-reconfigure xserver-xorg

It will ask a bunch of questions, hit enter for defaults.

---

### Post by bbarcelo on 2007-05-06
Is that what Ubuntu uses though? Just all the default values during its install? Won't this result in not detecting the correct monitor resolutions and/or naming the graphics card or setting the correct amount of video RAM? I'll give it a shot right now, I mean, what's the worst it could do.

Note: Still running on that single stick of RAM.. looking good..

EDIT: Yeah, just defaulting everything didn't produce the same results as when I installed Ubuntu for the first time and it handled creating the xorg.conf file. It did auto-detect my monitor name, graphics card name, video ram, max resolutions, screen placement and all that stuff and it did a hell of a good job. That's what I'm looking to re-run.
EDIT2/Solution to at least one problem: OK, so I figured the Ubuntu LiveCD had to detect all the necessary automatic stuff it does for xorg.conf while just using the LiveCD. Once I had backed up the xorg.conf to a safe location, I exited the LiveCD and attempted ot get back into Gnome. Gnome decided to pull some **** though and give me a video display mode not supported error. I had no idea why this was up, but I consoled with CTRL+ALT+F1 and did killall gdm followed by a startx (after I had gone and replaced the xorg.conf file with the one I made/wanted). X started with Gnome and everything was great. Woohoo.

Taking that one stick of RAM out seems to have done the trick as well, no more random lock up/freezes..

---

### Post by asipi on 2007-05-07
more info need about the background of the problem. did you try looking the logfiles?
e.g.:
.xsession-errors in your home
messages, xorg.log, daemon.log, syslog, and similars in /var/log

somewhere you shoul find more info what is happening in the background
you told us only the symptoms, we should find the reason or cause now then we could go on with the solution

---

