---
title: "Live CD that load _everything_ to RAM"
date: 2007-01-26
forum: General Help
---

### Post by amitz on 2007-01-26
Hi guys and gals,

What is the cleanest way to create an ubuntu 6.06 live CD that load everything into RAM. What I mean is that even the /usr, /bin, and /sbin is also loaded into RAM. The purpose is threefolds:
1. To make the applications run faster since there will be no HD access.
2. To minimize wear on CD-ROM drive since the live CD is only used for booting only. After everything is loaded into RAM, the CD can be released from CD-ROM drive.
3. Damn, I forgot the third reasons :) 

I'm thinking of editing the bootcd configuration file in /etc/bootcd/bootcdwrite.conf but there seems to be no option to have everything loaded to RAM.

All help will be appreciated. Thanks!

---

### Post by amitz on 2007-01-27
Found out that based on [http://wiki.linuxquestions.org/wiki/Live_CD_distributions](http://wiki.linuxquestions.org/wiki/Live_CD_distributions) , I can do:
<start quote>
We will first recreate the /usr directory so that it is no longer read-only. First we need to create the ramdisk and a mount point to mount it.

    mke2fs /dev/ram3
    mkdir /root/ram3
    mount /dev/ram3 /root/ram3 

    Note: The size of the ramdisk will be limited by the value you specify for RAMDISK_SIZE when you created the Live CD. You may have to create additional ramdisks to bypass this size limitation. 

Now copy the contents of /usr to /root/ram3 and mount /dev/ram3 to /usr.

    cp -R /usr/* /root/ram3
    mount /dev/ram3 /usr 
    umount /root/ram3 

    Note: Do NOT umount /root/ram3 before mounting it to /usr. /dev/ram3 shares its space with /dev/ram1 and /dev/ram2. Unmounting /dev/ram3 can overwrite some of the contents; hence this step is last. 
<end quote>

But I don't where to put such code in ubuntu, maybe a file equivalent to "autoexec.bat"?

---

