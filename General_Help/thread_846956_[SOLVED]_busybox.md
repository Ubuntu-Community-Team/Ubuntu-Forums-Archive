---
title: "[SOLVED] busybox"
date: 2008-07-02
forum: General Help
---

### Post by kouakou on 2008-07-02
I am trying to install ubuntu on my one TB HDD. I am getting the following message

BusyBox v1.1.3(Debian 1.1.1.3-5 ubuntu 12)
Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

I have a 40GB hard drive which when connected works just find with the rest of computer.....I have googled to Hell and back but tdhere seems to be no solution....
Help!!!

---

### Post by ar0n on 2008-07-02
I had this problem when my computer had 2 hdds with /boot/ directory and after a kernel upgrade grub update scanned for the stage files and added the new entry in menu.lst to boot from my primary hdd.

So check that your root setting in your menu.lst is correct.
If thats correct try to start your system up in single user mode and examine the kernel bootup to get some information about the problem.

---

### Post by kouakou on 2008-07-02
I have two hard drives but I am trying to get rid of one of them. if I connect the 40Gb I am able to boot .....what I am trying to do is run a fresh install only on the 1 TB drive because using the 40gb I cannot use my dvd drive since both are IDE....that slave and master thing doesnt seem to work.....
help!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!1

---

### Post by danwood76 on 2008-07-02
This happens when the initramfs loads but it doesnt find the kernel.
It could be caused by a bad line in your menu.lst, possibly stating the wrong root or something.

If you are trying to migrate to a different hard disk it might just be worth doing a fresh install.
This will give you better results and should just work once the install is complete.

With regards to your DVD drive and HD on the same IDE issue, make sure the DVD drive is set to slave on the jumpers and the HD to master.
Sometimes the diagrams are upside down, they normally have some kind of registration mark on the diagram so you get it up the correct way.
Do you not have a second IDE connector you can plug the drive directly into?

---

### Post by kouakou on 2008-07-03
as far as the HDD is concerned, I was trying to do a fres install that is where  am running into that error I have completely removed the 40GB drive but still it wont load the installer ....could it be the cd....
unfortunately the board I have has only one IDE controller....a friend of mine told me to get another but I am ye to find any...
Anyway thanks for the help....if it does not work I guess I can do without a dvd drive

---

### Post by kouakou on 2008-07-03
thanks all....I fixed it....it only took me two days....woo hoo

---

### Post by aBitLater on 2008-07-03
share the joy!  How'd you fix it?  I'm having the same problem, trying to install by booting to Install CD on my Toshiba Portege 3500 Tablet PC.

---

### Post by chuckdraws on 2008-07-04
I'm having this exact problem, but not from the cd.  I installed Ubuntu and it worked fine.  I shut down teh computer, and when I tried to start it back up, it's throwing me the same error.  And how would I access the menu.lst file?

Cheers.

---

### Post by wolfen69 on 2008-07-04
> **chuckdraws said:**
> I'm having this exact problem, but not from the cd.  I installed Ubuntu and it worked fine.  I shut down teh computer, and when I tried to start it back up, it's throwing me the same error.  And how would I access the menu.lst file?

Cheers.

boot to the live cd to access your files.

---

### Post by goemon_h on 2008-10-08
If you've made it to busybox and you have an 'alternate' install cd handy, it's not a big deal to reinstall the system, even on a system with no cd-drive that doesn't support usb booting.  Here's what I do on my old (cd-less) laptops I get.  

1.  After booting into busybox, mount your external usb drive that contains the live cd.  For me it was 'mkdir ./mountpoint && mount -t iso9660 /dev/sdb1 ./mountpoint'

2.  Once you have your live cd mounted, mount your internal hard disk.  For me it was 'mkdir ./hddmount && mount -t ext3 /dev/sda1 ./hddmount'

3.  Copy over the live cd to your hard disk like 'cp -r ./mountpoint ./hddmount'

4.  reboot

5.  When it hits grub, hit escape, then hit e and alter the boot line to point to your new initrd.gz you copied from the live cd. I believe it's under /install/ or /linuxlive/ or some such folder. so it'll look like '/hddmount/install/initrd.gz' Then boot.

Anyway at this point the installer will load up into memory, find your usb cd drive (which I assume is still plugged in) and select is as the package repo.   You can then install as normal, reformat your internal hard disk, and you never needed usb-cd boot support in your bios.  Hope this helps.

---

