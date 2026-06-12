---
title: "error during ubuntu boot"
date: 2006-12-11
forum: General Help
---

### Post by hellfried on 2006-12-11
i have just installed open suse 10.2 on the 3rd partition of my 160G hd. i have winxp on the first and edgy eft on the second. during the suse installation i elected not to install the grub loader on mbr. instead after the installation i went into edgy and added suse to the grub/menu.lst. the following is how my menu.lst looks like -  

t[I]itle		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title           OpenSUSE 10.2
root            (hd0,2)
chainloader     +1[/I]

with this i have suse as an option on my ubuntu grub. however now whenever i am finished with suse and when i want to reboot into ubuntu i get an error during bootup. i am asked to hit 'ctrl d' in order to continue booting. after i do that everything is fine and i get into ubuntu. during this, i am told that a log of this error is kept in /var/log/fsck/checkfs and this is it:

[I]Log of fsck -C -R -A -a 
Mon Dec 11 17:36:49 2006

fsck 1.39 (29-May-2006)
fsck.ext3: Unable to resolve 'UUID=dd614dba-d098-4b30-a202-ce5f7ac18a81'

fsck died with exit status 8

Mon Dec 11 17:36:49 2006
--------------[/I]

any idea how i can get rid of this error message?

---

### Post by Herman on 2006-12-11
Hello hellfried,
You can press 'enter', then 'Ctlr+d' to get past that and continue booting up.
 
Just open a terminal in Ubuntu and run this code (following) to lsit all your partitions along with thier UUID numbers, it works best when the terminal window is expanded to full size first. (Click the middle button 'maximize window', in the top right-hand corner),
```
ls /dev/disk/by-uuid/ -alh
``` Now you can see the uuid numbers corresponding to each filesystem (partition). Just leave that terminal open for now.
You need to check to make sure your /etc/fstab file is edited with the correct uuid numbers, and when it is corrected, you will no longer receive the error message next time during boot-up.

Click to open a different workspace (one of the brown squares in the bottom right of your screen), and open another terminal. Open your /etc/fstab file, ```
sudo gedit /etc/fstab
``` Now you can see the partitions listed in /etc/fstab.  You might need to edit your ubuntu's /etc/fstab with the details for your new Suse filesystem (partition).
That should cure your problem.

If you are still uncertian, read this web-page, [Filesystems and Mounting Page.]("http://users.bigpond.net.au/hermanzone/p10.htm")
And if your still have questions, post back here and sooner or later someone will help you.
Regards, Herman :D

---

### Post by hellfried on 2006-12-11
thanks for the reply. will try it when i get home from work today.

---

### Post by hellfried on 2006-12-13
thanks it worked beautifully

---

### Post by Herman on 2006-12-15
You are welcome, and thanks for the good feedback too.

---

