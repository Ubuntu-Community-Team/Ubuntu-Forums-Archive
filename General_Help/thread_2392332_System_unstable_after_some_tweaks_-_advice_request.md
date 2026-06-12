---
title: "System unstable after some tweaks - advice requested"
date: 2018-05-19
forum: General Help
---

### Post by one+one+one on 2018-05-19
I bought a used refurbished laptop a month ago and installed Ubuntu.  A few days ago I converted ubuntu to xubuntu using the instructions here: [https://sites.google.com/site/easylinuxtipsproject/alternative](https://sites.google.com/site/easylinuxtipsproject/alternative).  I've been applying some of the other tips on the site, but I've run into some trouble.  Three or four times, a box has popped up saying things like "Ubuntu has encountered a problem.  Would you like to submit an error report?"

For some reason I seem to be running version 16.04 (xenial) instead of  18.04.  Maybe 18 wasn't out yet when I first installed ubuntu.

I probably did too many things at once before restarting because I'm not sure exactly which one caused the problems.  Before I ran into the problem the first time, I had just reinstalled the Evolution e-mail client, which I had accidentally uninstalled because I didn't realize it was part of the ubuntu default apps that I uninstalled when I converted to xubuntu.  Also the computer said it needed to restart to finish applying some updates.  But I decided to do a couple more things before restarting.  I did items 6, 9, and 11 in the right-side column on the page [Speed up your Ubuntu!]("https://sites.google.com/site/easylinuxtipsproject/speed")
**6. Turn off some startup applications.**  I ran the terminal commands and then went to Session and Startup, Application Autostart tab, but the only thing I turned off was Blueman Applet because I don't currently use any bluetooth things.
**9. Put /tmp on tmpfs.**  I have 8 GB of RAM, so I followed the instructions as indicated to use some of the RAM for temp files.
**11. Speed up your Intel wireless chipset.**  I followed the instructions to turn on Tx AMPDU.

Items 1.1 (not 1.2) and 8 were already done with no problems.  1.1 is the swappiness setting, which I set to a value of 8.  I have an SSD and wanted to preserve its life somewhat by using the swap file less often.

So, I didn't actually have any problems with slowness before doing all this stuff, I just did it because it seemed like a good idea.  But after I restarted, immediately there were problems and at least twice, that box popped up saying Ubuntu has encountered a problem, and asking me to submit an error report.  So, before doing anything else, I restarted again, and it restarted without an error that time, but has occasionally given errors since then.  I have been able to sit at the computer and type all this up using Firefox without any apparent problems, except that the very first time I looked at one of those Linux tips pages after starting the browser, it seemed slow for a bit.  But maybe that was my uMatrix add-on slowing it down.  But when doing other things the problem has happened two more times, and gThumb crashed twice while I was using it to remove about 200 pictures from my camera and put them on my computer.

I am thinking the #9 modification from that Linux tips page is the one I need to undo.  Maybe #11 too - I didn't notice any wireless network slowness before applying the change, and didn't do any comparative benchmark testing, so I could easily undo that without noticing a difference.

---

### Post by kerry_s on 2018-05-19
i think you should do a clean install & stay away from the tweaks.

---

### Post by one+one+one on 2018-05-20
A clean install certainly remains an option, but I think I'll try undoing those last couple of changes first, as I suggested at the end of my first post.

Real quick, can you explain how the #9 tip works, from the [Speed up your Ubuntu page]("https://sites.google.com/site/easylinuxtipsproject/speed")?  I see that I copy a file, tmp.mount, from /usr/share/systemd to /etc/systemd/system, and then run a systemctl command to enable that file.  I have taken a look at the contents of the file, but I don't understand what it does.  And the site says to check if it is working, run systemctl status tmp.mount.  Because I didn't run that before doing the modification, I don't understand what the output is telling me after.  Nevertheless, I'm going ahead and undoing the change according to the instructions.

[SIZE=4]**Before removing the tmp.mount file and rebooting -**[/SIZE]
Here are the contents of the tmp.mount file:
[FONT=courier new]#  This file is part of systemd.
#
#  systemd is free software; you can redistribute it and/or modify it
#  under the terms of the GNU Lesser General Public License as published by
#  the Free Software Foundation; either version 2.1 of the License, or
#  (at your option) any later version.

[Unit]
Description=Temporary Directory
Documentation=man:hier(7)
Documentation=http://www.freedesktop.org/wiki/Software/systemd/APIFileSystems
ConditionPathIsSymbolicLink=!/tmp
DefaultDependencies=no
Conflicts=umount.target
Before=local-fs.target umount.target
After=swap.target

[Mount]
What=tmpfs
Where=/tmp
Type=tmpfs
Options=mode=1777,strictatime

[Install]
WantedBy=local-fs.target[/FONT]


Here is the output from systemctl status tmp.mount:
[FONT=courier new]&#9679; tmp.mount - Temporary Directory
   Loaded: loaded (/etc/systemd/system/tmp.mount; enabled; vendor preset: enable
   Active: active (mounted) since Sun 2018-05-20 06:28:49 +07; 4h 1min ago
    Where: /tmp
     What: tmpfs
     Docs: man:hier(7)
           [http://www.freedesktop.org/wiki/Software/systemd/APIFileSystems](http://www.freedesktop.org/wiki/Software/systemd/APIFileSystems)
  Process: 1047 ExecMount=/bin/mount tmpfs /tmp -t tmpfs -o mode=1777,strictatim

May 20 06:28:49 derpy-lappy systemd[1]: Mounting Temporary Directory...
May 20 06:28:49 derpy-lappy systemd[1]: Mounted Temporary Directory.

[/FONT]
Here is the output from free:[FONT=courier new]
              total        used        free      shared  buff/cache   available
Mem:        8098380     [FONT=courier new]1329188[/FONT]     [FONT=courier new]4655308[/FONT]       [FONT=courier new]56580[/FONT]     [FONT=courier new]2113884[/FONT]     [FONT=courier new]6361560[/FONT]
Swap:       8316924           0     8316924


[/FONT]
[SIZE=4]**Then, after removing the file and rebooting -**[/SIZE]
Here is the output from systemctl status tmp.mount:
[FONT=courier new]&#9679; tmp.mount
   Loaded: not-found (Reason: No such file or directory)
   Active: inactive (dead)
[/FONT]
Here is the output from free:
[FONT=courier new]                            total        used        free      shared  buff/cache   available
Mem:        8098376     1057104     6129512       51208      911760     6705436
Swap:       8316924           0     8316924

[/FONT]

---

### Post by kerry_s on 2018-05-20
tmpfs is already the norm, those tips are from way back. a whole lot of changes since then, all that other stuff will just work against the system to slow things down.

your biggest problem is going to be the mixing of 16 & 18, 16 had unity, 18 has gnome-shell that's the main ui. then there are system things replaced/removed.

my advice pick either 16 or 18 & load that fresh.

---

### Post by one+one+one on 2018-05-20
Do you think I accidentally mixed versions 16 and 18?  I certainly didn't do it on purpose.  I realize that starting with ubuntu and then deciding to switch to xubuntu is sub-optimal.  But maybe when I did the switch, I accidentally rolled back from 18.04 to 16.04 and now I have elements of both?  I really hadn't noticed, if that is the case.  I don't know for sure if I was on ubuntu 16.04 or 18.04 before I followed the instructions on [https://sites.google.com/site/easylinuxtipsproject/alternative](https://sites.google.com/site/easylinuxtipsproject/alternative) to change it to xubuntu.  The title of the page says the instructions will change ubuntu 18.04 to xubuntu 18.04.  I was assuming that since I ended up with xubuntu 16.04 that I must have started with ubuntu 16.04, but I don't know for sure.  If the page is old, as you say, then it may not have been all properly updated for version 18 even though they updated the title.

I've backed up my important things in case I need to reinstall, but everything seems to be working fine since I un-did that change as mentioned in my previous comment.  I just moved and copied files with gThumb while having a youtube video playing in Firefox with about 25 tabs open, with Evolution and Keepass also open, and there were no problems.  So, I'll consider it working for now.  I'll do something a little more involved and make sure it doesn't crash.  If it does, I'll plan on wiping everything and starting fresh with xubuntu.

---

### Post by PaulW2U on 2018-05-20
one+one+one, those instructions are specifically for Ubuntu **18.04** as they only reference GNOME packages. If they were for Ubuntu **16.04** then I would expect them to make some reference to packages with unity in their name. Exactly what **sudo apt-get autoremove** removed is of course unknown as are the names of any packages which were removed indirectly to satisfy dependencies.

It's not possible to roll back from one release to another so if you had 16.04 before then you have it now, likewise with 18.04.

Of more concern is whether the conversion completed successfully and in its entirety or not? I suspect that you have something that looks like Xubuntu but still have a lot of Ubuntu's Unity left over which shouldn't be a problem but those packages will attract future updates. I wonder if you will then run into further problems when installing either Ubuntu and/or Xubuntu updates?

Running each of the following commands in a terminal might throw some light on what you really have:

```
lsb_release -a
echo $XDG_SESSION_DESKTOP
uname -a
```

If your kernel version is 4.15 then it's from 18.04. If your kernel version is 4.4 then it's from 16.04. If you installed the HWE stack then I'm not sure what kernel 16.04 is now using, possibly 4.13.

---

### Post by one+one+one on 2018-05-21
Thank you for the help.  Everything still seems to be running well, even when I downloaded the Hugin panorama photo stitcher and used it to start merging a large set of photos, using up all my RAM and starting to use my swap space.

Here are the terminal commands you asked about.

[FONT=courier new]xxxxxx@derpy-lappy:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.4 LTS
Release:    16.04
Codename:    xenial
xxxxxx@derpy-lappy:~$ echo $XDG_SESSION_DESKTOP
xubuntu
xxxxxx@derpy-lappy:~$ uname -a
Linux derpy-lappy 4.13.0-41-generic #46~16.04.1-Ubuntu SMP Thu May 3 10:06:43 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
xxxxxx@derpy-lappy:~$[/FONT]

---

### Post by PaulW2U on 2018-05-21
Thanks for posting that. I just was interested in establishing whether you had somehow managed to mix 16.04 and 18.04 even unintentionally. It seems not.

---

### Post by one+one+one on 2018-05-21
You said something about HWE stack.  Was that part of those instructions from the linux tips site?  I don't think it's something I would have installed on purpose because I know I have older hardware, so there is no reason to install something that helps the newest hardware work.

---

### Post by one+one+one on 2018-05-21
And thank you for that latest reply too.  I didn't see it until now.  I'm glad I have what at least appears to be a not-mixed-up operating system.

---

### Post by PaulW2U on 2018-05-21
> **one+one+one said:**
> You said something about HWE stack. Was that part of those instructions from the linux tips site?
If you installed 16.04 from one of the later point releases rather than the original release than you would have automatically installed the HWE stack. So probably not something that you did as a result of taking advice from the website.

---

