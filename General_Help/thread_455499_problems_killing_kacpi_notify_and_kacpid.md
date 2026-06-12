---
title: "problems killing kacpi_notify and kacpid"
date: 2007-05-26
forum: General Help
---

### Post by ethana2 on 2007-05-26
If I understand correctly, acpi is some kind of power management system.  Now, I'm on a desktop with no CPU throttling or anything like that at all.  I don't need those.  The reason they caught my attention though is this:

Every minute or so, my PC will freeze for a few seconds, have 100% CPU usage for a minute, freeze again, be normal for around a minute, and do it again.  This cycle happens constantly.  I have determined via system monitor (showing all) that kacpi_notify and kacpid are the CPU gobbling culprits.  I try commands like (as su) "kill 31" and "kill 32" but nothing happens.

I want these modules gone forever, and I'll take all the help I can get to do that.  (Aaah!  It just did it again!)  First, am I wrong in wanting to be completely rid of these modules, and second, what do I have to do to kill them in their sleep?  Or active state, whenever...

---

### Post by Billy the Kid on 2007-05-26
Have you tried "sudo killall kacpi_notify"?

---

### Post by ethana2 on 2007-05-26
Yes, but to no avail. :(

---

### Post by ethana2 on 2007-05-26
Occasionally it almost seems like that works, but even when it does, they pop back up again after a minute or so.  If they are kernel modules, I can unload and blacklist them or something, right?

---

### Post by Billy the Kid on 2007-05-26
It looks like "Lockjaw" has had the same problem, and found a solution: 
[http://ubuntuforums.org/showthread.php?t=399619](http://ubuntuforums.org/showthread.php?t=399619)

---

### Post by ethana2 on 2007-05-26
Why, thank you very much.  apm=off is it?  I'll try that.  I added acpi=off to the kernel parameter line a while ago.  Anybody who sees this thread, just follow the above link.  I'll be back to confirm its effectiveness for myself soon.

---

### Post by ethana2 on 2007-05-26
Seems to be working.  Those two processes are no longer running at all.  Excellent.  How do I mark this thread as solved?

---

### Post by Beholder87 on 2008-02-11
hi guys, my problem here is kind of different, but the same....
it is the SAME as described here: [http://www.linuxquestions.org/questions/linux-newbie-8/kacpid-eats-cpu-xp-and-ubuntu-dual-boot-problem-615219/](http://www.linuxquestions.org/questions/linux-newbie-8/kacpid-eats-cpu-xp-and-ubuntu-dual-boot-problem-615219/)
i tryed to use what this guy did: reboot on recovery mode, but i doesn't worked for me to kacpid.
**my ubuntu works fine until** i reboot and start windows, and then reboot again and start ubuntu. after the **reboot from windows**, the process: Kacpid, eats a lot of my CPU!!!

ok i tryed to insert that in my grub:
> **Lockjaw said:**
> Well, I opened up /boot/grub/menu.lst and added "acpi=off" and "apm=off" to my usual kernel line:

kernel /boot/vmlinuz-2.6.20-14-generic root=UUID=ba4ad4dd-a223-46db-92c8-836b50d0308b ro **acpi=off apm=off** quiet splash


Ok so far ok, my computer rebooted well, but when the system (ubuntu) was starting, it showed an error message("Bus 0000, etc......" -> something like that), but it's to fast that i cannot see it very well and then it goes on and start to load ubuntu...
When the OS is totally loaded, (after i insert password and everything...), my [b]Internet Connection doesn't work[b]!!!!!!
it's like the **kacpid is required for my NIC Card to work**.... and then when i'm rebooting my computer again, it shows another error and then it reboots. something like: "error IRQ channel, etc....," i don't know...

i tried to reboot a few times to test removing the 2 options that i inserted in grub before: acpi, apm.
->when i removed the option acpi=off from grub, the computer was the same: kacpid eats cpu and network is working
->when i removed the option apm=off from grub, the process kacpid wasn't eating cpu (because it was off), and i couldn't connect to the network .

so my conclusions are:
-> if i use apm=off or not, it doesn't matter, the same happens with it on or off.
-> if i use acpi=off, then the process doen't eat cpu, but i can't have access to the internet (the network connection icon ->it's on the side of the control volume, it keeps trying to connect to the network and it never stops to tring to configure... )
-> if i do not use the option acpi=off, then the problem is that the proccess keeps eating my cpu......

you can also take a look in what this guy said/wrote: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/56246/comments/8](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/56246/comments/8)
font: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/56246](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/56246)

do you have any ideas?
thank you
=)

p.s.: sorry about my english (I'm still learning ^^)

---

