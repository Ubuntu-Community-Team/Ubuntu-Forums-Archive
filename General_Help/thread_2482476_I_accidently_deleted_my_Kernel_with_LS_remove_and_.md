---
title: "I accidently deleted my Kernel with LS remove and now my Ubuntu is a black screen"
date: 2023-01-01
forum: General Help
---

### Post by raderall on 2023-01-01
Yeah I need to reinstall it, But I have important game saves on it. and a few other files that are practically irreplaceable and would take too long to recreate if lost. Someone gave me these set of instructions following!




You can boot a live system from a USB drive, mount the root filesystem of your desktop somewhere (/mnt is the traditional place), chroot into it, then apt install linux-generic inside the chroot.
Setting the chroot is a bit involved:

[LIST]
[*]lsblk # and find the device name of your root partition, e.g. for me it's /dev/nvme0n1p5 
[*]mount /dev/whatever /mnt 
[*]mount --bind /etc/resolv.conf /mnt/etc/resolv.conf # so network will work in the chroot 
[*]mount --bind /proc /mnt/proc 
[*]mount --bind /sys /mnt/sys 
[*]mount --bind /dev /mnt/dev 
[*]chroot /mnt 
[*]mount /boot || true # needed only if /boot is a separate partition 
[*]apt install linux-generic 
[*]exit # from chroot 
[*]reboot 
[/LIST]
[FONT=&amp][COLOR=#000000]There's a longer description of the process in the Ubuntu Wiki ([/COLOR][[COLOR=#000000]https://help.ubuntu.com/community/LiveCdRecovery[/COLOR]]("https://help.ubuntu.com/community/LiveCdRecovery")[COLOR=#000000]), with some branches irrelevant to your particular problem.[/COLOR][/FONT][COLOR=#000000]
TBH I'm very surprised the system let you remove the package of the running kernel without scary warnings requiring special confirmation.[/COLOR][COLOR=#D7DADC][FONT=&amp]
[/FONT][/COLOR][COLOR=#000000]So yeah will this restore my customized Xubuntu desktop with all my stuff on it?[/COLOR]

---

### Post by Tadaen_Sylvermane on 2023-01-01
It will fix  the kernel. You should make sure and update-grub as well.

```
apt install linux-image-generic
``` is the proper package.

---

### Post by ian-weisser on 2023-01-01
Files that are truly valued are backed up.

If you succeed with your attempt to restore your system bind-mounting from a Live environment --without really understanding what you are doing-- you will be lucky.

There is nothing wrong with those instructions, but they do assume a certain level of skill. You are likely to encounter questions or problems that are unforeseen.

---

### Post by oldfred on 2023-01-01
If it is just reinstalling kernel (and grub) it may be easier to use Boot-Repair.
It has an advanced mode where you can choose install (in case you have more than one) and choose drive to install boot loader. Also check install kernel &  it should update.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

But I also agree, it any is valuable, you must have backups. What if hard drive failed tomorrow.
Note drive always fails just before you plan to do a backup.

---

### Post by raderall on 2023-01-01
Thank you! ian. I'm going to need a second linux OS to be able to get into this Ubuntu and backup important files. I'm thinking Puppy Linux on my Compact flash card. Bionic Pop I hear isn't able to run alot of appimages and programs the other Puppys are, So if you know of a better one that's still very Similar and still quite a small OS can you please tell me. I mean I could just use this Windows 11 I'm on now and that trick with the powershell, but both OS'es are on the same NVMe. Maybe I can label them different somehow in the Hard Disk Utility and get into that this way. Well what should I do here to create a backup?

---

### Post by raderall on 2023-01-01
Can I install that from the GNU GRUB? Or The Tty1 without having to put than on a usb? Do you know what to press to get into those in the boot options menu? and just what codes?

I just looked into that. Maybe you can, but it's quicker and easier to run the Repair Kit, From the USB via the bios.

---

### Post by raderall on 2023-01-01
It won't work! you just put the files on the usb and it's completely invisible in the bios and does not start up if you let it go past that into the main menu or whatever. Rufus says the new version is not compatible with that kit and the Ubootin and that other one do not have this repair boot listed in the checklist so how do you use it? I Guess the answer is to go into powershell from this Windows 11 sector and get into the files and back them up to here. then reformat the usb that it is now Impossible to get this kit on as Rufus is the only thing that can put it on. anything else on your list needs to have it in it's programmed list. Listing it as Xubuntu was a dud. So back to getting Xubuntu on it and putting these codes in the installation package. But first I need to get into the Xubuntu and the only entry is through the Win11 PowerShell Terminal. So what codes do I need to put into this?

Well I'm going to have to do what the expert said. It should and odds are it will. [COLOR=#000000]going to put some notes here for me to view on my android while I'm fixing this on my usb. 

[/COLOR]chr=/mnt 
lsblk # to check the list, view the different parts. the Ubuntu has greater space 299.38 GB, Win11 has 176.83 GB, all the other partitions are in the MB.

Reformat my usb again, and put Xubuntu back in it. and this should all now work.

---

### Post by oldfred on 2023-01-02
Use Windows tools for Windows & Linux tools for Linux.
Best to always have both a USB flash drive with Ubuntu live installer and Windows repair flash drive for current versions you have installed.

Use Ubuntu live installer of your current version to make repairs.

---

### Post by raderall on 2023-01-03
Would Xubuntu live installer work? I see no option in the instructions to do a repair install instead of the default completely wipe everything or create a new partition, a second ubuntu desktop universe environment ect.

Point is, it's the best option to get into my Xubuntu desktop from my Win11 boot and back up my files just in case.

---

### Post by deadflowr on 2023-01-03
> Use Windows tools for Linux & Windows tools for Linux.

My brain exploded.

---

### Post by oldfred on 2023-01-03
Major typo
Windows tools for Windows & Linux tools for Linux. 

There are no auto fix tools, other than possibly knowing how to use Boot-Repair and other Linux commands.
You cannot fix Linux from Windows and attempting may damage it more.
Any Linux live installer should work, but best to use same version as you have installed.

---

### Post by raderall on 2023-01-03
Okay I figured this out, the Live usb menu looks very different than the guides and pictures on the youtube videos. I however need to get into the Home Folder and my username, Say "A1" and "Guest". I looked at my files in the "Try "Xubuntu" They are both looked I do not have permission to get into them. What do I punch into that terminal to get in so I can copy to the plugged in drive and then do this?
 t

---

### Post by oldfred on 2023-01-03
The files in your install are user 1000, but the live installer is user 999, so you do not have ownership.
You should be able to mount read only manually and copy the files.
If mounted unmount with umount. Where X is drive &  y is partition like sda2.

sudo umount /dev/sdXY
sudo mkdir /media/temp
sudo mount /dev/sdXY /media/temp -o umask=000

umask=000 sets the permissions of files and folders to 777 or rwxrwxrwx. Which is normally too permissive.

---

