---
title: "Weird one: hda is reading sda and I need hda back"
date: 2007-06-04
forum: General Help
---

### Post by drfox on 2007-06-04
Here's a weird one: I bought a Dell with XP on it. The MB only supported SATA. I took an IDE drive out of my old computer and, with the help of an adapter, got it mounted as SDA1. Well, Dell has an issue with timers and APIC, and they wouldn't support Ubuntu because they didn't supply it to me. So, I've sent the computer back. 

In the meantime, I'm trying to remount my HD on my old computer, and when I run GPartEd, my disk reads sda1 instead of hda1. Is there anything I can do to get Ubuntu to recognize my drive?

Larry

---

### Post by jimbob on 2007-06-04
I assume you've taken the adapter off and now have the HD connected via an IDE cable?

There is nothing wrong with Ubuntu calling the drive sda1 as long as it can mount it and read/write to it.

You may have to adjust your /etc/fstab and /boot/grub/menu.lst to reflect any changes in the UUID or hdax versus sdax, etc.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by drfox on 2007-06-04
> **jimbob said:**
> I assume you've taken the adapter off and now have the HD connected via an IDE cable?
There is nothing wrong with Ubuntu calling the drive sda1 as long as it can mount it and read/write to it.
You may have to adjust your /etc/fstab and /boot/grub/menu.lst to reflect any changes in the UUID or hdax versus sdax, etc.
&#65279;

I've done all that except name the drive sd0 in grub/menu.lst

The thing is, the grub menu never comes up for me to edit it at boot; therefore I think the BIOS is confused whether the drive is IDE or SATA :(
In Disk utilities, it sees an IDE drive, but at boot ???

Larry

---

### Post by drfox on 2007-06-05
Fixed it! It turns out it was a grub problem.
I followed this thread (How to install Grub from a Live Ubuntu CD):

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Thanks, Catlett!   :D

Larry

---

### Post by mikewhatever on 2007-06-05
Happy for you, but the link you posted leads nowhere.

---

