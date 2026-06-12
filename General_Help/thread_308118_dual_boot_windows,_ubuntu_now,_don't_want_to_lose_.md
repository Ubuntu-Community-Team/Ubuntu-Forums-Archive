---
title: "dual boot windows, ubuntu now, don't want to lose anything"
date: 2006-11-27
forum: General Help
---

### Post by Jack of Fables on 2006-11-27
i want to get widows back, but not get rid of all my ubuntu stuff, i have done alot to my theme and everything, so is there a way that i can dual boot windows if i already have linux without loseing anything

---

### Post by Dragen on 2006-11-27
You sure can, but you need to go in to it very carefully.

1.) You need to partition your drive so you have a partition for Windows, and the partition (+swap) for Linux.  Chances are, you only have partitions setup for Linux, and that would require you to RESIZE your partition.  You can use 'gparted' for this by typing:

> sudo gparted

Please note, you will have to UNMOUNT the device you wish to resize.. so if you only have one partition, it's important for you to use your Ubuntu Live CD, mentioned below:

2.) Highly, highly recommend you make sure you have your Ubuntu Live CD for MBR boot repairs.  The reason I say this, is because Windows blows out your MBR when you install it, which forces your system to boot in to Windows.  With the live CD, you can boot in to Ubuntu and do:

> sudo grub
> root (hd0,0)
> setup (hd0)

The above is an example depending on your partitions.  I recommend using TAB while typing root (<tab here> to auto complete and find the correct partition information for re-installing GRUB boot loader.


Please keep in mind, messing around with partitions, is ALWAYS risky, and I highly recommend backing up the files you downloaded and used for your themes, etc.  I have personally used 'gparted' to resize an ext3 filesystem and it worked.  However, I also tried making it work on an NTFS partition with Vista RC2 on it, and Vista exploded.  It didn't like that at all.  The good news was, I was able to mount vista from Ubuntu and transfer my files.  Vista just kept locking up on the disk CRC check during bootup.

So in a nutshell,

1.) Backup stuff you want, need.
2.) Get your Ubuntu Live CD ready to go.
3.) Boot in to your Ubuntu Live CD.
4.) > sudo gparted
5.) Resize your ext3 partition to make room for another partition.
6.) Apply, reboot in to your Windows install disk
7.) Make sure you blast out the right partition during windows install
8.) Install Windows (Windows has now blasted out your MBR)
9.) Now to Dual boot, you need to install GRUB.
10.) Boot in to your Ubuntu Live CD again
11.) Type the following:

sudo grub

root (<hit tab> (find your partition information))

(as an example, it may look something like "root (hd0,0)"

setup (hd0)

12.) GRUB should install.
13.) Reboot and you SHOULD have a GRUB menu to select Ubuntu.  (Windows wont be there yet)
14.) When you boot back in to Ubuntu, now head over to, '/boot/grub' and modify the file 'menu.lst' by typing, 'sudo gedit /boot/grub/menu.lst'.
15.) In here, you want to make sure you have a Windows entry.  You should have an entry at the bottom that looks something like this:

title		Microsoft Windows Operating System
root		(hd0,3)
savedefault
makeactive
chainloader	+1

NOTE: Where it shows "(hd0,3)", make sure you change it to the correct boot partition.  This totally depends on which partition your Windows is installed to.

After you save this file, you should have a GRUB boot menu which allows you to select UBUNTU or WINDOWS without a hitch.  You can also add a splash screen and all that fancy stuff when you get all this working..


Now please bare in mind, I typed this in about 10 minutes off the top of my head, and this procedure works great for me, and many others.  Just go in to this very carefully, and pull up some links on this subject.. You will probably find even more detailed instructions than mine by googling it.  But hopefully this gives you an overview of what to expect.

Good luck, and have fun!

---

### Post by drphilngood on 2006-11-27
You can also use [GAG, THE GRAPHICAL BOOT MANAGER]("http://gag.sourceforge.net/").

---

### Post by Jack of Fables on 2006-11-27
thanks, skimming your reply gave me all i need. just use my live cd, partition my drive (after i back up important stuff) then use the partition i made by resiszing my ubuntu partition, to install windows. now do you think that the same thing would work for installing os x86, but not on the same computer, i don't think this one would handle os x that well.

---

