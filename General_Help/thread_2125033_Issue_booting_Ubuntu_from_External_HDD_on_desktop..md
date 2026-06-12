---
title: "Issue booting Ubuntu from External HDD on desktop. Works fine with laptop?"
date: 2013-03-12
forum: General Help
---

### Post by Tonakai on 2013-03-12
Hi guys,

First off, I am unsure as to whether or not this is the correct section for this post. If not, sorry.

I've got a 1TB External HDD that I installed Ubuntu onto. I have three partitions; 250GB FAT32, 250GB Ext2, 500GB NTFS.

The partition with Ubuntu installed (250GB Ext2) is set as the primary partition, and set to "logical". I have been using Ubuntu for the past few days on my Laptop with no issues booting (from the bios menu I located my ExHDD and placed it as the highest priority) and all has been well. After deciding to move back to my desktop environment I plugged in my HDD, placed the exact same driver as the priority in the BIOS of my PC, and when it boots I get the GRUB RESCUE prompt.

I know fully well that my PC is able to boot from USB, so the cause of this I cannot fathom. 

Any help would be appreciated, thank you.

---

### Post by Yu Jin X5 on 2013-03-12
Well I have heard of this before go to bios and set it to boot from the external because right now on the desktop it will most likely be booting from your hard drive. i.e set it as your only boot. Hope you figure it out
Yu_Jin_X5

---

### Post by Tonakai on 2013-03-12
Thanks for the quick reply, but I'm booting from my USB Device and not from my HDD. I've checked and triple-checked that to make sure.

---

### Post by Yu Jin X5 on 2013-03-12
[http://goo.gl/jte5K](http://goo.gl/jte5K)

---

### Post by Yu Jin X5 on 2013-03-12
perhaps?

---

### Post by Tonakai on 2013-03-12
I'm rather begrudged to attempt that as it would most likely remove the  modifications I have spent days doing. I have also been searching google  and it appears my grub install is corrupt for some strange reason  (considering the external harddrive still works on my Laptop. Anyhow, I  have been attempting this through: ```
sudo -i
mount /dev/sdb2 /mnt
grub-install --root-directory=/mnt/ /dev/sdb2
``` (obviously changing the drive to my own)

However I am getting an issue stating: > root@ubuntu:~# grub-install --root-directory=/mnt/dev /dev/sdb2
/usr/sbin/grub-bios-setup: warning: File system `ext2' doesn't support embedding.
/usr/sbin/grub-bios-setup:  warning: Embedding is not possible.  GRUB can only be installed in this  setup by using blocklists.  However, blocklists are UNRELIABLE and  their use is discouraged..
/usr/sbin/grub-bios-setup: error: will not proceed with blocklists.

---

### Post by Tonakai on 2013-03-13
Booted Ubuntu from my Laptop and updated GRUB, but it's still the same: 

```
Error: Uknown File System
Grub Rescue
```

---

### Post by Tonakai on 2013-03-16
Just did a fresh install using my PC to install Ubuntu onto my HDD hoping that would help but still nothing.

---

### Post by Tonakai on 2013-03-16
Okay to make sure again I modified my boot prio' in the Bios and get the same issue then I manually booted from every device in my boot list, all of which lead to Windows aside from my HDD that gave me the Grub issue again.

---

### Post by oldfred on 2013-03-16
You do not install grub to a partition or sdb2 but to the MBR of the external drive or sdb. BIOS jumps to MBR to boot and will never see a PBR  or partition boot sector.

This can automate the repair and show details.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

With the new very large drives, it is better to have / (root) in a small 25GB ext4 partition and then separate /home or /mnt/data partition(s) to use the rest of the space you want to use for Ubuntu.
      
 Install to external drive. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)

---

### Post by Tonakai on 2013-03-20
Hi there, thanks for the reply. 

> **oldfred said:**
> You do not install grub to a partition or sdb2 but to the MBR of the external drive or sdb. BIOS jumps to MBR to boot and will never see a PBR  or partition boot sector.

This can automate the repair and show details.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Having read this; I attempted to install GRUB to sdb, which is still producing the same error. I have run BootInfo and here is the URL it created: [http://paste2.org/p/3233463](http://paste2.org/p/3233463)

You will notice that Lilo is installed on sda. This is because a short while ago I accidentally replaced my Windows MBR with Grub but it wouldn't boot Windows from there, so I used Lilo to rectify this issue. Also sdb has now been relabeled to sde (though I'm not entirely sure why). You will also notice that I'm using Mint at present. That is simply because I hoped that attempting a distro other than Ubuntu may work; though I was clearly wrong. 

> **oldfred said:**
> 

You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

I attempted to use this to rectify the issue, however the Grub Error remains. It's getting slightly annoying considering all I wish to do is install a linux-based distro onto a partition of my Harddrive and for it to work on both my PC and Laptop. It's strange to me that it still boots perfectly well from my Laptop (even though I had made sdb2 my boot device upon installation), yet the Desktop PC is still having issues.

> **oldfred said:**
> [COLOR=#000000]With the new very large drives, it is better to have / (root) in a small 25GB ext4 partition and then separate /home or /mnt/data partition(s) to use the rest of the space you want to use for Ubuntu.[/COLOR]

How would I go about doing this?

Thank you for your help.

---

### Post by oldfred on 2013-03-20
External drives may change order depending on when you mount or unmount and remount. It is now after your flash drive. 
So you have to check which device it is mounted as when using any commands that are device related.

Did you run the Boot-Repair suggested repair?

Script or grub seems confused. It is looking in both partition one & partition two? Not sure if script or the issue with your FAT32 partiiton which cannot be mounted. 

>  Grub2 (v2.00) is installed in the MBR of /dev/sde and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in [COLOR=#ff0000]partition 1[/COLOR] for ([COLOR=#ff0000],msdos2[/COLOR])/boot/grub.


You also have some Linux files in your Windows main install, which may confuse Windows??
> sda3: ___________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    [COLOR=#ff0000]Operating System:  Ubuntu 12.10 [/COLOR]
    Boot files:        [COLOR=#ff0000]/etc/fstab[/COLOR] /Windows/System32/winload.exe



I do not recommend FAT32 for any larger partitions. It is ok for small devices like small flash drives or camera cards.
But it does not support files over 4GB, not has a journel so chkdsk may not work or will take longer. Since Linux cannot mount it, it may need chkdsk from Windows repair console.

Also the same for ext2. It is for small partitions like a separate /boot, if you have a separate /boot which is not 
needed for most desktops. You want ext4 as it has journel. Ext3 is ok but ext4 has been around long enough that there
are no real issues.

---

### Post by Tonakai on 2013-03-20
> **oldfred said:**
> External drives may change order depending on when you mount or unmount and remount. It is now after your flash drive. 
So you have to check which device it is mounted as when using any commands that are device related.

Did you run the Boot-Repair suggested repair?

I did, but it didn't seem to help at all.

> **oldfred said:**
> 

Script or grub seems confused. It is looking in both partition one & partition two? Not sure if script or the issue with your FAT32 partiiton which cannot be mounted. You also have some Linux files in your Windows main install, which may confuse Windows?? It seems to boot up alright. I'm not sure how I'd go about fixing this to be honest.

> **oldfred said:**
> I do not recommend FAT32 for any larger partitions. It is ok for small devices like small flash drives or camera cards.
But it does not support files over 4GB, not has a journel so chkdsk may not work or will take longer. Since Linux cannot mount it, it may need chkdsk from Windows repair console.

Also the same for ext2. It is for small partitions like a separate /boot, if you have a separate /boot which is not 
needed for most desktops. You want ext4 as it has journel. Ext3 is ok but ext4 has been around long enough that there
are no real issues.

This is actually because I use my HDD to boot my game backups on my Wii and Wii U. Fat32 is required sadly otherwise I would not use it. 

I also read that guide about dual booting with two separate drives that you linked. It answered my question about having separate partitions for the /boot and / but when I attempted to run linux I get an error stating that there is no filesystem and again back to grub rescue so I'm not really sure how to proceed. Any suggestions?

---

