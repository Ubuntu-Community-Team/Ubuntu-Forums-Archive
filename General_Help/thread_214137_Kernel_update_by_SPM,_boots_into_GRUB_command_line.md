---
title: "Kernel update by SPM, boots into GRUB command line"
date: 2006-07-12
forum: General Help
---

### Post by Pelham123 on 2006-07-12
I updated the kernel via auto update this morning, when I re-started it booted into the following command line:

grub>

I didnt have time to try any commands as I was late for work, there are no grub menu choices, just the command line. I've never used the grub command line, and as I can only access the internet at work now, I'm after a walkthrough to get my Ubuntu back.

Any help, thoughts or advice will be gratefully received.

---

### Post by keith.burgoyne on 2006-07-15
It's funny you mention that...

I updated my kernel two days ago, and the very same issue happened with me. I've been working with Grub to try and get my system working again, but I get some strange errors. I've attempted reinstalling grub through the command line, but there's been no dice.

I've tried a number of different things (keep in mind that hd1 is my linux drive, and hd0 is a windows drive). hd0 is also where the grub boot loader is installed, and /boot/grub is where the grub data files (including menu.lst) are located. Looking at various forums, they say this should be done:

root (hd1,0) #set my linux drive, and the first partition, as the root           
             #filesystem
setup (hd0)  #reinstall grub on the windows drive boot partition
reboot       #restart system


And absolutely nothing happened. The setup command returned a success, but when I reboot I get returned to the same old prompt. 

I tried this:

cat (hd1,0)/boot/grub/menu.lst

And an error was returned, saying that that file was located on a cylinder beyond what my bios can support. The funny thing is, I have not made any changes to my bios! I have been running Ubuntu on my BIOS default settings for a year now -- and there has never been a problem until I recently updated my distro.

Can anyone offer some help? I am pulling my hair out on this one!

---

### Post by Herman on 2006-07-15
Hello, I hope maybe one of these links will help you two,

What to do with GRUB's [Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli")

[How to re-install GRUB from a GRUB shell ]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD")

[How to mount your Ubuntu install with a LiveCD and edit grub's menu.lst]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD")

Regards, Herman :D

---

