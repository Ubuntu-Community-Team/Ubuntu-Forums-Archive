---
title: "Problems booting Live CD"
date: 2007-07-17
forum: General Help
---

### Post by Arnold_Trembley on 2007-07-17
I'm a newbie.  I have tried some other live CD's (Knoppix, Mepis 6.5, PCLinuxOS) and they boot on my HP Pavilion a336n, but neither Ubuntu 7.04 or Kubuntu 7.04 will boot.  They were purchased from on-disk.com.

They both fail the same way.  First there is an error message about "no tty", then I get a message that looks like this (copied by hand):

(initramfs) [ 332.162017] ata2.01: failed to set xfermode (err_mask=0x4)
This more or less repeats a couple of times until I get the following message:
(initramfs) [ 408.399925] ata2.00: failed to set xfermode (err_mask=0x40)
after that, it just sits there doing nothing.

I do get the initial splash screen and the PF1 thru PF6 options before this happens.  I've tried changing the video mode, but it doesn't help this problem.

My cpu is a 2.60 GHz Intel Pentium 4
512MB DDR SDRAM
80GB disk (Maxtor 4R080L0)
DVD-Rom 16x (Samsung) - where I mount the live CD
CD-RW 48x (Sony)
Intel (R) 82845G/GL/GE/PE/GV Graphics Controller

Any help would be greatly appreciated.

With kindest regards,

---

### Post by confused57 on 2007-07-17
Maybe you can find a solution in this thread:
[http://ubuntuforums.org/showthread.php?t=421588](http://ubuntuforums.org/showthread.php?t=421588)

---

### Post by Arnold_Trembley on 2007-07-17
> **confused57 said:**
> Maybe you can find a solution in this thread:
[http://ubuntuforums.org/showthread.php?t=421588](http://ubuntuforums.org/showthread.php?t=421588)

Thanks for the link.  I printed off the whole thread and I will try the "modprobe piix" command per the instructions.  What does "modprobe piix" do?

I also had the "can't access tty; job control turned off" message.

I'm running WinXP-SP2 Home, and trying out several Live CD's.  I don't know at this point if I will try to install Linux until I've had a chance to play around with a few distributions.

Thanks again!

---

### Post by confused57 on 2007-07-18
> **Arnold_Trembley said:**
> Thanks for the link.  I printed off the whole thread and I will try the "modprobe piix" command per the instructions.  What does "modprobe piix" do?

I also had the "can't access tty; job control turned off" message.

I'm running WinXP-SP2 Home, and trying out several Live CD's.  I don't know at this point if I will try to install Linux until I've had a chance to play around with a few distributions.

Thanks again!
You might also read the solution by Pumalite in this thread:
[http://www.linuxforums.org/forum/ubuntu-help/97726-boot-problems.html](http://www.linuxforums.org/forum/ubuntu-help/97726-boot-problems.html)

It's probably a good idea to try out a few other distros, such as PCLinuxOS, Mandriva, Fedora, etc...see which you prefer, before installing.

Someone else might know what the piix module is...

---

