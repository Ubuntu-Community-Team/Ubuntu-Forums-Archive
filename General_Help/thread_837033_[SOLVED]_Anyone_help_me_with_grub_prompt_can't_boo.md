---
title: "[SOLVED] Anyone help me with grub prompt? can't boot into Ubuntu anymore"
date: 2008-06-22
forum: General Help
---

### Post by breadbin on 2008-06-22
hiya, i was messing with dual booting Ubuntu and win2K and for some reason the way i'd normally do it wouldn't work for me. I set up partition table and made fat32 part for win2k then copied my bootsector onto to add it to the boot.ini file after win2k was installed but somewhere along the line i had to use fixmbr and fixboot and messed up the mbr. 

I can boot with the hardy dvd and tried grub-install and it seemed to work after a little tweaking --root-directory=/mnt seemed to do the trick but just get a grub prompt when i boot. can anyone help me get the ubuntu boot process back please?

i try setup (hd0) and kernel /vmlinuz and then boot but I get tons of errors and it then crashes so its not readig the right image or something. My options now are reinstall hardy and lose the updates I made to my system which were alot. Luckilly I have my home directory on a seperate partition but don't want to undo all the good work I did getting the system the way I wanted it. Hope someone can help.

---

### Post by forestpixie on 2008-06-22
Are you saying you did this with the livecd

> sudo grub
find /boot/grub/stage1
grub> root (hd0,1)
grub> setup (hd0)
grub> quit

Maybe try the supergrub livecd - [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by breadbin on 2008-06-22
sorry I just posted in a panic before I searched and found a great thread about it. I never did the root command. but got it working now thanks! that was easy:)

how do I mark this as being solved?

---

### Post by forestpixie on 2008-06-22
There's a link in my sig - there's a mark thread solved in thread tools above your first post.

---

### Post by breadbin on 2008-06-22
Thanks I must be going blind;)

---

