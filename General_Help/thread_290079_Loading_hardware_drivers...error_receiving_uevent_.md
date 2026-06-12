---
title: "Loading hardware drivers...error receiving uevent message: No buffer space available"
date: 2006-10-31
forum: General Help
---

### Post by hardkaare on 2006-10-31
im getting this error in my boot log 

Nov  1 00:54:25 rcS:  * Loading hardware drivers...                             error receiving uevent message: No buffer space available

My laptop takes forever botting up, over 1 min. :-(

can someome explain what it is and how to remove it!

Solved with todays update of restricted modules!

---

### Post by octoberdan on 2007-06-25
I'm having the same problem, but an upgrade did not fix the problem. Anyone else experiencing this? Running 7.04 on an Acer Aspire 5100-5030

---

### Post by NZ-Wanderer on 2007-07-25
I too am recieving this error...

Loading Kubuntu Feisty tonight, and got the following:

Loading Hardware Drivers
Error Recieving uevent message: No Buffer Space available..

Does anyone have any kind of suggestions on what this is or how to fixc it from happening again please, or at least tell me if it is something to worry about :) ???

---

### Post by atfrase on 2007-07-26
Yeah, happens to me too, but it seems like not every boot and it doesn't seem to affect boot time (although my machine is pretty fast, so maybe it would just be even faster otherwise, I dunno).

---

### Post by NZ-Wanderer on 2007-07-26
well I solved the problem by doing a complete re-install of Kubuntu (it needed one anyway) :)
not exactly the best way of solving it, but at least I don't get it anymore :)

---

### Post by gummih on 2007-09-24
I'm stuck at this too :confused:
Nobody knows how to fix this?

---

### Post by disraeli on 2007-10-16
This happened to me today as well. It has never happened before. Here is what I did today that might have caused somehow the message to pop up:

- I removed the following services from bootup: brltty, pcmciautils, bluetooth
- I rebooted to windows for moving ~3GB data from the linux home partition to the NTFS partition

I'm gonna investigate this and report progress here

EDIT: I rebooted and the message isn't there anymore. BAH

---

### Post by _doug_ on 2007-12-04
I'm also having this problem with ubuntu 7.10 64 bit, does no one know of a solution to this?
i'm running on an HP pavilion dv6000 laptop with an AMD TL-56, 2 gig of ram and nvidia go 6150 graphics.
i can't ever get ubuntu to load, is there anything i could try??

---

### Post by virgil on 2007-12-19
[QUOTE=
i'm running on an HP pavilion dv6000 laptop with an AMD 
i can't ever get ubuntu to load[/QUOTE]

Had exact same problem.
This worked for my dv9401ca.

[http://www.computer-essence.com/Projects/hp-dv9410us-debian.html](http://www.computer-essence.com/Projects/hp-dv9410us-debian.html)
[http://www.computer-essence.com/Projects/laptop-details.html](http://www.computer-essence.com/Projects/laptop-details.html)

Open /boot/grub/menu.lst 
Near the bottom of the file there should be some line similar to :

    kernel   /boot/vmlinuz-2.6.18-5-amd64 root=/dev/sda3 ro

Change it to :

    kernel   /boot/vmlinuz-2.6.18-5-amd64 root=/dev/sda3 noapic irqpoll noirqdebug ro


On the iso CD of ubuntu there is a windows executable installer that will create a /boot/grub folder on the windows partition.
After it's created you can edit it and then reboot.  You will have the ubuntu loader using this config file for the time of installation.

After installation you will have to modify the root/grub/menu.lst in the Linux partition.

Until it's modified on disk you can modify it "on the fly" at startup with the loader menu options.
e to edit
enter to save
b to boot the modified config

Escape will loose the modif.

---

### Post by rosbif22 on 2008-03-07
> **_doug_ said:**
> I'm also having this problem with ubuntu 7.10 64 bit, does no one know of a solution to this?
i'm running on an HP pavilion dv6000 laptop with an AMD TL-56, 2 gig of ram and nvidia go 6150 graphics.
i can't ever get ubuntu to load, is there anything i could try??

Same laptop, same specs (technically, mine is the dv6058cl, I think),
same problem

Virgil, your advice worked perfectly! Many thanks...I've spent forever trying to figure this out.

---

