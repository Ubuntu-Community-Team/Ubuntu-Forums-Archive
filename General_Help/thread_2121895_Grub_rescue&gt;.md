---
title: "Grub rescue&gt;?"
date: 2013-03-03
forum: General Help
---

### Post by yesterdays jam on 2013-03-03
Hi everyone,

I recently got a new SDD and installed 12.10 on it. However, I had an older HDD with 12.10 on it as well, and some backed up files. When I boot with the HDD connected, I get a message displayed on my screen saying; 

error: no such device: 28bb4adb-c201-4129-80a7-353d3a6a1da3. 
grub resuce> 

When I don't have the HDD connected I boot fine. I would like to use this drive as storage for media.

Have I made a big mistake by having the OS on two drives? Can I format the HDD (I have backed up all files I want on it), and then just use it as normal?

Thanks in advance

---

### Post by oldfred on 2013-03-03
When both drives are plugged in, are you selecting SSD to boot from? Or is it trying to boot from HD and a partition is now missing? I have 4 drives with different versions of grub in each booting different systems (very confusing). 

You can better understand what is where with this:

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by yesterdays jam on 2013-03-04
There is no option to boot from one drive or the other. I entered ls after grub rescue> and the output was;

(hd0) (hd0,msdos6) (hd0,msdos5) (hd0,msdos1) (hd1) (hd1,msdos5) (hd1,msdos1) (fd0)

I also connected the data cable for the HDD while booted, and it works. I can see the two partitions (one for Ubuntu one for media, and the files that were there before).

I'll follow the suggestions on your links when I get back from work.
Thanks for helping! :)

---

### Post by oldfred on 2013-03-04
Most computers in the last 6+ years will let you choose which drive to boot from. If you can boot from a flash drive you can choose hard drive. All SATA drives have to be bootable from BIOS as they have no jumpers. 

Only some very old Dell computers and those with IDE and boot drive selected with jumpers on hard drive could only boot from primary master. Newer IDE has cable select and then BIOS can choose drive.

---

### Post by yesterdays jam on 2013-03-04
My computer is about 8-9 years old, but I used to have a drive with XP on and I got the choice of which one to boot from. All drives I'm using are SATA.

BootInfo;

[http://paste.ubuntu.com/5586126/](http://paste.ubuntu.com/5586126/)

I couldn't boot from my live CD while having the HDD connected, it just gave me the same error origionally posted. I hope this helps.

---

### Post by yesterdays jam on 2013-03-04
And this is the BootInfo when I connect the HDD after I've booted;

[http://paste.ubuntu.com/5586350/](http://paste.ubuntu.com/5586350/)

---

### Post by oldfred on 2013-03-04
BootInfo looks normal. I do not see any issues. But your second run is not showing a second drive. Does BIOS show drive?

Can you manually boot and totally reinstall grub. Or Boot-Repair may offer that option.

On a system that old SSD may not work well. You need AHCI in BIOS to enable trim. And without trim drive will slow down.
You may be able to do this.
       fred@fred-Precise:~$ sudo fstrim -v /
/: 23267893248 bytes were trimmed
[https://wiki.archlinux.org/index.php/SSD_Memory_Cell_Clearing](https://wiki.archlinux.org/index.php/SSD_Memory_Cell_Clearing)
sudo hdparm -I /dev/sdX
Alternate to discard, call fstrim via cron
[http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html](http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html)

---

### Post by yesterdays jam on 2013-03-04
Boot Repair does give an option to repair most frequent problems, should I give that a go? When you say manually boot and totally install grub, is that just a fresh installation of 12.10? I can't perform that from boot while the HDD is attached, but if I do 'Try Ubuntu' and then connect the HDD before going for the reinstall. That might work?

---

### Post by yesterdays jam on 2013-03-04
I performed the Boot Repair recommended task (reinstall grub on all drives) and it has appeared to work. I get the option to boot from the SSD and the HDD. The BootInfo that I recieved after performing the reinstall is;

[http://paste.debian.net/239833/](http://paste.debian.net/239833/)

For the SSD could I just do; 

sudo fstrim -v /

in terminal? Or do I need to perform something in BIOS?

Thanks so much for your help, I feel like I've made progress with Ubuntu! :)

---

### Post by oldfred on 2013-03-04
Do you have an AHCI setting in BIOS? But XP does not work with AHCI unless you install drivers when installing.
If so turn it on. And add settings to fstab.

If not add a task to cron to regularly run the fstrim command.

 Do SSD need customization?
[http://ubuntuforums.org/showthread.php?t=1981478](http://ubuntuforums.org/showthread.php?t=1981478)
Arch suggests gpt for SSD. Only if installing Windows on older system may you want MBR as Windows only boots from gpt with UEFI. 
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[http://ubuntuforums.org/showthread.php?t=2003022](http://ubuntuforums.org/showthread.php?t=2003022)
[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

---

### Post by yesterdays jam on 2013-03-04
How would I check if I have AHCI in BIOS? I had a look when I booted, but didn't see anything obvious. I don't intend to use windows on this system again. 

Am I right in thinking that I should have my swap space on my RAM instead of the SSD then?

---

### Post by oldfred on 2013-03-04
Swap is substitute RAM. With new SSDs it really does not matter. How much RAM do you have. If 4GB or more you may never use swap anyway, unless you hibernate. Then you need swap equal to RAM in GiB not GB or about 20% more than GB.

       [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
HOWTO: Use swapfile instead of partition and hibernate 
[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946)

---

### Post by yesterdays jam on 2013-03-05
I enabled AHCI in BIOS and got fstrim through util-linux;

jam@angel1:~$ sudo fstrim -v /
/: 58215002112 bytes were trimmed

I'll work out how to perform this frequently.

I have 1GB of RAM, intend to increase to 4GB (the maximum my MB supports).

One last question; could you direct me to somewhere where I can find out how to remove the old ubuntu partition on my HDD? I would prefer to just have this as a media storage drive.

Thanks again for all your help :)

---

### Post by oldfred on 2013-03-05
You can use gparted from Ubuntu LiveCD/Flash or download gparted as lightweight Linux repair CDs.

       [http://partedmagic.com/](http://partedmagic.com/)
[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)

      
 GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

