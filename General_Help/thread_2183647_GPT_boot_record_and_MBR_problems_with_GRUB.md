---
title: "GPT boot record and MBR problems with GRUB"
date: 2013-10-25
forum: General Help
---

### Post by tjannx on 2013-10-25
Hello all, 
I've been experimenting with GPT partitioning for a few weeks now on a new hard drive that I bought purely for this purpose. The main reason for this was to see if creating a octo-boot (or larger) system is possible with a GPT scheme. I created a GPT disk through Gparted, created a hybrid MBR with Gdisk, partitioned according to how I wanted my system to look with a large multi boot system, and started installing. Good news, bad news. The good news is, it worked perfectly, and aside from minor problems with the grub screen bugging out a few times, the system is happily running. The bad news is, it worked perfectly and now refuses to boot to my other hard drive which has MBR partitioning on it. The problem began when I decided to get my boot screen looking pretty again (rather than having 64+ entries in it). I downloaded Boot-repair, ran it, and poof, boot screen was nice looking again... but, it brought about this.

I forgot to read a little more ahead on the differences between the MBR and GPT in how they determine where to search for a boot record. Now, when swapping out from my GPT partitioned hard drive to my MBR hard drive with Ubuntu and Windows, I am unable to boot, and am immediately put into the grub rescue console. At the moment, my live usb is at home, which I suppose I could use to reinstall everything, except that requires gettinng onto my other hard drive and reinstalling the systems. Using the Grub rescue commands is getting me nowhere right now. All that is returned from every partition that I try access is "No known filesystem detected."

Things I have tried: 
[http://askubuntu.com/questions/197833/recovering-from-grub-rescue-crash](http://askubuntu.com/questions/197833/recovering-from-grub-rescue-crash)
 [http://askubuntu.com/questions/142300/how-to-fix-error-unknown-filesystem-grub-rescue](http://askubuntu.com/questions/142300/how-to-fix-error-unknown-filesystem-grub-rescue)
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293) - some of the things here (requires a cd though, so not too much good)

The question is, is there anything that I can do at this moment without my live usb to fix this and be able to get into my other hard drive to use windows? I assume that completely reformatting everything during an install would rewrite the GPT partitioning scheme back to a MBR, but... this took me a few weeks to learn everything and finally get running. I'd prefer not to do that.

---

### Post by oldfred on 2013-10-25
Macs use hybrid MBR/gpt partitioning to allow Windows to boot in BIOS mode  in their normal UEFI mode boot. But you have to keep first 4 primary MBR partitions sync'd with the gpt partitions. Never recommended if there is another way.

       [http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)

Windows only boots from gpt with UEFI. Ubuntu will boot from gpt with UEFI or BIOS. Both only boot from MBR with BIOS systems.

I have gpt on my old 160GB drive when I experimented with gpt and installed 10.10. My new drives all are gpt. I even use gpt on my new larger flash drives. But I do not have UEFI yet and my older MBR drive is where I have most of my installs.

      
 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by tjannx on 2013-10-25
Quick update: I have managed a semi workaround using a hard drive dock that I bring with me. After reinstalling grub and running update-grub on my experimental GPT drive, I was able to access the Ubuntu on my other hard drive from the GPT partitioned boot loader. Inserting the hard drive by itself into the computer by itself still creates errors and boots to the grub rescue screen. Any ideas anyone?
And, because I realized that I forgot to give a little more information of what the commands show when I run them in the rescue mode, here is what I get when I have my hard drive dock connected and turn on the computer

grub>
grub> ls
(hd0) *this is the HD in the dock)* (hd1) (hd1,17gpt) (hd1,16gpt) (hd1,15gpt) ....(to save reading time some are ommited, count down 1 with the gpt)   (hd1,1gpt) (hd2) *my sd card*
grub>ls (hd0)
Device hd0: No known filesystem detected-Total size 1250263782 sectors.

Using the set command to set anything on hd0 works just fine, but when I try to access it, I get an error telling me that the partition does not exist. Attempting to run the boot command obviously results in errors as well.

---

### Post by tjannx on 2013-10-25
give me a second... gotta rerun the boot repair now. So MAC's actually go with this as a default partition scheme? odd.

---

### Post by tjannx on 2013-10-25
As requested, here is the boot-repair summary detailing my devices.
[http://paste.ubuntu.com/6303279/](http://paste.ubuntu.com/6303279/)

---

### Post by oldfred on 2013-10-25
You have Windows on sdb booting in BIOS mode from MBR drive.

You have multiple installs in sda, but show both bios_grub for BIOS booting and two efi partitions for UEFI booting. You can only easily dual boot with Windows if your Linux installs are same boot mode as Windows or BIOS. Only by going into UEFI menu and turning off BIOS/CSM and turning on UEFI could you then boot an install in UEFI mode.
UEFI standard technically allows multiple efi partitions but none have actually worked yet that I have seen. You need to remove one of the efi partitions. Also per UEFI spec the efi partition is supposed to be first. Windows often makes it second or even third after some small partitions, so it still is near beginning of drive. No idea if limited FAT32 driver in UEFI reads very large drives. Probably limited and that is why they made the standard be it must be first.

Only grub2 with 13.10 has the fix to the bug in UEFI installs where it cannot correctly create chain loads to other efi installs. Boot-Repair does.

But note that even if grub has an entry for another system, it must be installed in the same boot mode. Once you start booting in BIOS you cannot switch to UEFI or vice-versa. They are not really compatible. But you can dual boot directly from UEFI menu (only).

Grub often goes berserk in finding other installs so I normally turn off os-prober and only add one entry with a name I understand as the menu entry item.

You also show a menu.lst or grub legacy. it does not work with gpt.

       Using 40_custom & Custom menu
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

   How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)


 #Add menu entry to 40_custom, change example from sda13 to your partition.
Just to have record of current installs:
 sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup

gksudo gedit /etc/grub.d/40_custom
#Turn off prober
gksudo gedit /etc/default/grub
#Add this line
GRUB_DISABLE_OS_PROBER=true
#update grub menu after any change
sudo update-grub

      
 I first saw this from Ranch hand - I think he was testing daily in sda13, so kernel could easily have changed.
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition. example based on sda13 change all 13's to your partition number.
At least for Ubuntu family OS's, they all place symlinks in /, called vmlinuz and initrd.img These point to the most recent versions of the kernel in the /boot folder.
More info:
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

   gksudo gedit /etc/grub.d/40_custom
menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}

---

### Post by tjannx on 2013-10-25
Thank you so much for your help so far :)
I have to unfortunately run off due to the library closing, so I'll have to try this out when I get home. I do know that I can dual boot easily with windows and linux like you said, and I did for a while in fact with the hard drive marked sdb there. (Un)fortunately, curiosity and my desire to tinker got the better of me, thus the multi boot experiment here. Perhaps I'll have to go back in and reinstall everything making sure to put the efi install first and the hybrid mbr bios_grub boot after... but thta still doesn't seem right.
I do have one other question though. How does using a gpt scheme have an effect my ability to load off of a different hard drive? Is grub saved onto the computer in memory as well as the hard drive? Or is it just the fact that UEFI and BIOS are quite different. I suppose that if necessary I can probably backup everything on my first hard drive, get a GPT able windows 7, and reinstall on a GPT partitioned hard drive and go, but.... once again, just wanting to preseve my current setup IF possible. If not, well... I'll get a disk.

I'll post more once I try everything out that you've given me and let you know how it goes.

---

### Post by tjannx on 2013-10-25
I managed to get into my other hard drive by using the multiboot usb that I have at home. It has Super Grub 2 on it, which was able to locate the Ubuntu boot.cfg file and let me load into the hard drive. From the windows/ubuntu dual boot hard drive, I ran boot-repair, hoping it might help. Now, I am locked out of the other hard drive for booting. Seeing as I am at homw, I am going to try a complete reinstall of everything on the hard drive in a slightly different order and try not running boot repair. I am fine having a slightly buggy boot screen while I am installing everything. After that, I'll use the links provided to modify that boot screen. If everything is in working order, I'll document what I did just in case someone else is wanting to experiment with a "super multi boot" system in this way and, perhaps, do a better job than I do :D If it works, I'll mark everything as resolved.

---

### Post by oldfred on 2013-10-26
You may want to keep installs small and have larger data partitions. I dual booted with XP for years and used a shared NTFS data partition. I had my Firefox & Thunderbird profiles as well as other data I wanted to share. I was then able to mount that partition in all my other installs also. Since not using XP now, I add new data into a Linux formatted data partition which I also share in all my other installs. 

After typing the same commands to add mounts, links folders, do configurations, and add additional default applications, it realized I could just list my history and make it a script. Works for me as my installs are all versions of Ubuntu. Other systems would not work.

I use 25GB for my installs but find even my main working install only has used 10GB including my /home inside / (root), but no data except for .wine.

       I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below.

   The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)
Severals posts on size of / and use of linking to data partition.
[http://ubuntuforums.org/showthread.php?t=2137726](http://ubuntuforums.org/showthread.php?t=2137726)

   Opposing viewpoint on separate data partitions - post 14 srs5694:
[http://ubuntuforums.org/showthread.php?t=1738065](http://ubuntuforums.org/showthread.php?t=1738065)
Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

---

### Post by tjannx on 2013-10-31
Hello again!
Just letting you know that I've had a big time crunch lately and havent had the time to actively work on the computer what with work at night, school all day... I'll try once again to get back to this on the weekend. Just figured I'd let you know I haven't just let this hang.

---

### Post by tjannx on 2014-01-22
Ok, I've managed to get my time back, between school and working nights, and am now actually taking a linux class. I have determined a little more about the problem here. As it turns out GPT is not the problem here. Do I create another thread for the updated info, or shall I continue here?

---

