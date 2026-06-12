---
title: "problem with booting, lightdm fails to load"
date: 2013-11-16
forum: General Help
---

### Post by Psmiffy on 2013-11-16
When I boot I get the Ubuntu flash screen with the 5 dots, then I get a black console screen saying: starting lightdm display manager ... Stopping send an event to indicate Plymouth is up. 
From there I can't do anything except reboot.
If I try to boot into recovery, 99 times out of 100 it crashes / hangs and I can get no further.

When I did get in I could log in succesfully and see the ls listing but could not get anything started.

This started happening about a week ago after running update.

Any ideas or advice would be appreciated.

---

### Post by ibjsb4 on 2013-11-17
Wonder if disabling  Plymouth would do any good.  You of course need to get back in again.  Got a live CD laying around?  Could use that to gain access.

You could disable plymouth in grub by removing 'splash' in /etc/default/grub.  The line would be GRUB_CMDLINE_LINUX_DEFAULT

---

### Post by Psmiffy on 2013-11-18
Thanks, I will give that a try tonight and see if it works.

---

### Post by ibjsb4 on 2013-11-18
Don't forget to update grub after.

```
sudo update-grub
```

---

### Post by Psmiffy on 2013-11-18
The grub file doesn't exist ...

---

### Post by Bashing-om on 2013-11-18
Psmiffy; Hi !
My input while the others are off-line.
It is possible that grub is corrupted. Can you boot from the liveDVD ->shift key as soon as bios screen clears -> language screen, escape key to accept the default ->boot options screen: here, what results when you choose "boot from hard disk" ?

Maybe you entered the command - sudo update-grub - incorrectly, else;
Maybe looking at (re-)installing grub.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by Psmiffy on 2013-11-19
Hi Bashing-om

I think the grub got "mislaid" somewhere in the update, we updated to 13.10 but in the grub boot menu it was still showing 13.04.

I managed to boot up with the live cd, but then there WAS no grub file to edit, which is why the update-grub failed.

I made a backup of all our files then when I went to install from the Live CD it offered to re-install and repair the installation so I tried that option.  Sadly and maddeningly the stupid ass power saving mechanisms kicked in and shut down the laptop after 95% of the processing.  I will try again tonight and see if I can keep the stupid thing awake long enough to get it working.  if not I will do a full clean install.

Thanks again for the advice.

---

### Post by Bashing-om on 2013-11-19
Psmiffy; Hey,

If it is merely a grub installation issue, one may easily (re-)install grub; either from the liveDVD or -if the install boots - from the installation.
All this is required is to know for sure where to install grub to.
From the liveDVD -> "try ubuntu" -> terminal (ctl+alt+t);
Terminal codes"
```

sudo fdisk -lu

``` The line with the "*" character is the boot drive and the root partition.
From the above we know where to install grub onto in a standard install, where there is no separate /boot partition.
Install grub:
```

sudo mkdir /mnt/work
mount /dev/sda1 /mnt/work
sudo grub-install /dev/sda
sudo umount /mnt/work

``` Which I fully expect to be sufficient to install grub onto the MBR of the 1st Hard Drive. This is assuming that ubuntu is installed on that first Hard Drive (SDA), adjust accordingly.

Reboot into the install and to terminal, check that grub is all happy and to ensure GRUB 2's menu is up-to-date.:
```

sudo update-grub

```
Reboot once more, just to see that all is good now.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by Psmiffy on 2013-11-20
What ho!

Confusion reigns in my household I can assure you.  I started the "reinstall" before i got your message so I thought it best just to let it run, and now I have a number of other problems.
1) the trackpad on the laptop that worked on the previous install and also worked on the live-dvd now no longer works (Fortunately I have a spare external mouse, that works)
2) the wifi that worked on the previous install and also worked on the live-dvd now no longer works, and as such i cannot get on to the internet.  No where can I get to the option to turn WIFI on anywhere, and it won't detect any of the neighbourhood networks the way it used to.

I should probably do a fresh install tonight, or I might try install Linux mint for a change, see how that goes.

---

### Post by Bashing-om on 2013-11-20
Psmiffy; More the pity !

Yeah, at this point try and (re-)install. Be aware many times there are no WIFI drivers - and others - available until after the system is installed AND updates are conducted to detect and locate and install the proper drivers. That means that the install should be done with  a wired 'net connection.

Let us know how it is going, and how else we can assist.

[INDENT][INDENT]cheers, and best foot forward
[/INDENT][/INDENT]

---

