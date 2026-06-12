---
title: "Unable to access the Grub Menu (so that I revert back to my original kernel)"
date: 2017-05-16
forum: General Help
---

### Post by zoe-scutterbug on 2017-05-16
Hi folks
I&#8217;m a very basic level user, with minimal code knowledge and a poor memory, who has returned to linux after a 8 year break. As a user I have one big flaw, I try new stuff but I don&#8217;t have a real clue what I am doing.

I recently installed Ubuntu 16.04 xenial on a ZOTAC ZBOX-EN1070
Desktop: Cinnamon 3.4.0 (Gtk 3.20.8) dm: lightdm
System: Kernel: 4.8.0-51-generic x86_64 (64 bit gcc: 5.4.0)

One of the tools I added to my system was the Ukuu (Ubuntu Kernel Upgrade Utility) 

For a week I ignored its little update messages, but I read a few places that it was ok to update your kernel on new fast machines and that it was easy to revert back by accessing the grub menu by pressing the shift key during boot. Silly me I did not test that I could access the grub menu.

So last night I used the Ukuu and selected what it and a couple of other sources said was the latest Kernel stable release 4.11 and pressed the button.

When I now try to boot up. I get very briefly three lines about ACPI problems and the nothing.

I have repeatedly tried holding down the shift key (both left and right as I was not sure) but I can not access the grub menu. (Previously i could not enter the BIOS by pressing F2&#8230;but thats also one the bluetooth buttons on my keyboard)

My keyboard is the Logitech K810 bluetooth illuminated keyboard which the box states it was designed for windows 8. This maybe i problem, it had to be set specially at the little shop that helped me install my system (I did not trust myself). 

I would be grateful for any ideas.
Maybe tomorrow i should buy a cheap keyboard and try again.

Thank you in advance

---

### Post by Dennis N on 2017-05-16
If your system is UEFI, [advice on the forums]("https://ubuntuforums.org/showthread.php?t=2345616&p=13579808#post13579808") says the ESC key might be used instead of Shift to display the grub menu. 

Information [here]("http://ubuntuhandbook.org/index.php/2017/02/ukuu-install-latest-kernels-ubuntu-linux-mint/") says the "mainline" kernels that the utility installs are for testing purposes - I would stick with the kernel version provided by the ubuntu repositories.

Looks like a nice computer - I have a Zotac myself, but older, and I love it.

---

### Post by ajgreeny on 2017-05-16
Yes, try repeat tapping of Esc rather than holding it down immediately after power-on and you may be lucky.

It took me many attempts to get to the grub menu at one point when I needed to so I eventually edited the /etc/default/grub file to ensure that the menu always showed for 2 seconds, but of course you need to get into grub first to get to a working system and be able to make that edit; even if you edited it from a live OS you still need to boot to the system in order to run command sudo update-grub.

Assuming you eventually do manage to get to grub and boot to an older kernel, these are the edits I made.
```
GRUB_DEFAULT=0
#Next line will make the countdown time show menu by default
GRUB_TIMEOUT_STYLE=menu
#Next line changed from 0 to x for x second delay
GRUB_HIDDEN_TIMEOUT=2
#Next line changed from true to false to allow delay countdown to show
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_TIMEOUT=2
GRUB_DISTRIBUTOR="Xubuntu-14.04"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```

---

### Post by zoe-scutterbug on 2017-05-16
Thanks (sorry for the delay replying)
Thanks for all the suggestions
Tried the escape key, no luck.

I guess stage one is I will buy a new keyboard to see if its just my keyboard (which is known to have issues with ubuntu)

zoe

---

### Post by zoe-scutterbug on 2017-05-17
New keyboard (was a Silly purchase). But with it pressing Escape i  can enter the BIOS and via F8 I can also enter the BIOS and once enter  the Grub menu, briefly tonight ...which is positive, but then I rebooted  before I thought to fix properly or just make the grub options visiable  or slow the process down etc and now i cant access again. (my trouble i  can never remember what I did, to get grub up).


zoe

---

### Post by oldfred on 2017-05-17
Sometimes cold boot, or full power down works better.
If laptop, also remove battery. Once unplugged also hold power switch for 10 sec or so and then reboot pressing correct keys to get into UEFI or BIOS.

Many new UEFI systems have a fast boot setting. That is different than the Windows fast start up.
And it assumes no hardware or configuration changes and immediately starts boot process, and then you do not have time to press any key at all.

---

### Post by zoe-scutterbug on 2017-05-17
F8 works it gets me to a short list offering to boot my only version of ubuntu on my ssd, a second option that repeated the first option and thirdly to enter the bios. 

The first time i got to this boot menu, i choose the second option and went straight to the GRUB menu. From the Grub menu, I choose the old kernal. Entered my system. Did a couple of unimportant things. Rebooted too soon. Now though i can get to this boot menu ... i can not get into my grub again.

---

