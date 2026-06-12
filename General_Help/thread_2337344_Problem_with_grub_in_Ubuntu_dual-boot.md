---
title: "Problem with grub in Ubuntu dual-boot"
date: 2016-09-16
forum: General Help
---

### Post by trubsee on 2016-09-16
Hi guys, sorry if this question is a repeat but I have tried a few things online and I am really after a directed solution now.

Basically I am having the problem where when I run grub I get the message minimal bash-like line editing is supported instead of being able to select my boot. This is my first time dual-booting ubuntu (I have used previously as a sole OS). I initially had some troubles with acer's bios not displaying the desired efi files. I am unable to run the full boot-repair due to partitioning the hard drive but I did get the boot log[FONT=arial, sans-serif] [SIZE=2][http://paste2.org/Oc1Gnsjk](http://paste2.org/Oc1Gnsjk).

Any advice is welcomed, I am still quite new to OS systems and lower level details. [/SIZE][/FONT]

---

### Post by oldfred on 2016-09-16
Did you swap drives?

But with Acer have you set "trust" on the Ubuntu/grub .efi boot files in the ESP on sda?
Also have you updated Acer UEFI to newest version from Acer? Some older threads say to downgrade UEFI, but others say newest works ok. Best to make sure your have newest.
       Acer Trust Settings - details:
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757) 
            Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392) 
            Acer Aspire E15 will not dual boot, many details
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)

---

### Post by RobGoss on 2016-09-17
On of my machines are** Acer**, after a number of attempts trying to get Ubuntu installed on this machine I was never able to get my machine to 'Trust" other OS's for this machine. So I did managed to get Ubuntu installed but as far as booting was concerned I had to use Rerind in order to boot the different OS's I have on this machine, you are welcome to take a look and see if this is something that will work for you [http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)

Acer is the only machine I had this trouble with

---

### Post by trubsee on 2016-09-17
Thanks, this problem is now fixed.

---

