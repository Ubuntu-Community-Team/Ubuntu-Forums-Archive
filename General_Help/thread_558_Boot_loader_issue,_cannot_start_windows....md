---
title: "Boot loader issue, cannot start windows..."
date: 2004-10-14
forum: General Help
---

### Post by wurtel on 2004-10-14
Hello everyone, I'm new to linux, so please don't hold my inexperience against me.
I'm pretty pleased with ubuntu, although I had to install it a few times before it acutally worked. 

I have 2 hard drives, win xp is installed on my master drive &amp; ubuntu linux on my slave drive.

First I installed ubuntu linux with both drives plugged in and it recognised I had a windows drive. With this first install grub was installed on my master (win xp) drive (...i think). The boot loader however gave me errors when i had to continue the Ubuntu install after reboot.

So I unplugged the master (win xp) drive and re-installed ubuntu. So this time the grub boot loader went on the slave drive (as it was the only place for it to be installed.)

Now obviously the problem is I can't boot to windows as it's not listed in the ubuntu installs grub.
I've tried unplugging the slave drive (ubuntu) but then grub on my master (win xp) drive gives me an error 21.

I gather somewhere that I should look for a grub.conf file but it is nowhere to be found on both my master or slave drive.

Almost forgot, my master (win xp) drive is not damaged as i can mount and access it from the ubuntu terminal window.

Can anyone please help me to solve this mess? I gather I'd need to get rid of the grub loader on my master (win xp) drive and then add windows to the grub loader on my slave (ubuntu) drive...?

Any help would be greatly appreciated and again my apologies for my inexperience with linux, but i guess everyone has to start somewhere :)

---

### Post by arctic on 2004-10-14
you have to edit your grub-file in order to run windows. in case you have already edited your fstab and then made mount points for windows (and mounted windows of course), you can refer to [http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&amp;chap=10](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&amp;chap=10) this gentoo handbook which covers the configuration of grub. it should be easy then. 
at least i hope that it will be so. 
good luck! :D

---

### Post by oddabe19 on 2004-10-14
Or you can ```
sudo gedit /boot/grub/menu.lst
``` then goto the ```
hidden menu
``` section and comment out the 'hidden menu'. Then adjust the Time section from 3 seconds to 10 if you want.

---

