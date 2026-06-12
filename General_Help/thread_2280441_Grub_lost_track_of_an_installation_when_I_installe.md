---
title: "Grub lost track of an installation when I installed Ubuntu Server"
date: 2015-05-30
forum: General Help
---

### Post by dora5 on 2015-05-30
I have two hard drives, each 250 G, one originally had Ubuntu and the other originally had Mint.  

I shrank the partition containing the Mint install, leaving approximately 50 G of free space.

I was supposed to eventually end up with one hd containing my Ubuntu desktop installation, 250 G, one hd containing my abt 200 GB Mint installation and my about 50 GB Ubuntu Server installation.

Then I attempted to install Ubuntu Server in the free space.   

In the process of installing Ubuntu Server, I "automatically partitioned" the free space.   I intended to install Ubuntu Server on the free space.

Thing never explicitly asked me where to install it.

It asked me whether to make the 55 GB partition bootable, and informed me unexplained catastrophic things like BIOS might bomb would happen if I said yes, so I said no.   I don't know if BIOS can handle just one bootable partition on the drive or what.

Eventually it told me it found two "OTHER" installations, Ubuntu 14.04 something, and Mint, and asked me if I had all of them or wanted to abort the installation and start over, so I said yes.   It was telling me it had two "other" installatoins plus the one it was installing.

It rebooted and found only Ubuntu plus the Ubuntu options that were there, and Mint.   Then automatically booted into Ubuntu Server.   

OK, I booted into Mint to find out what the f... .

Now, because I had trouble telling my Mint and Ubuntu installations apart, I put an empty folder in the /home/dora folder of each, one named "UBUNTU" and the other named "MINT INSTALLATION".

So, I still have all three of my operating system installations, but the boot loader is only finding both of the operating systems on just one of the hard drives.

My preferred OS is Ubuntu Desktop.  The one GRUB/ bootloader/ whatever can't find.   

How do I fix the boot loader/ GRUB?

While waiting for the answer I'll see if maybe asking for the boot menu when booting maybe finds the OS on the other hard drive.   

I did all of this because the bash tutorial I am trying to do required installing Ubuntu Server.   Wanted it in Oracle WhateverBox, but Oracle WhateverBox has been down all day for "maintenance", don't know if they didn't pay their server access fees or what, and what I found that called itself Oracle WhateverBox is clearly not the same thing.  Don't know why not just learn bash in Ubuntu, don't see what requires server about it, and for sure when I bought the course it didn't say I'd need Server to do it.  

!!(*&(!!!!!

Thanks!

Dora

---

### Post by oldfred on 2015-05-30
Did you try:
sudo update-grub

Did you install with Something Else. When you have more than one install or more than one drive, you should always use Something Else and often better to create partition(s) in advance.
Some have managed to share /home but others have issues. Much better just to create a shared data partition and have all data in the shared data partition, then no chance of one install overwriting configurations of the other install. 

May be best to see current details. Should be able to run from any one of your installs or from the live installer (but not server installer as it is not live).
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by Bashing-om on 2015-05-30
dora5; Hello;

I read that ubuntu (14,04) is installed and that you desire  that ubuntu 14.04 be the controlling boot authority.
To that end we (RE-)install grub such that 14.04 controls booting.
Now we need to know what is really and actually installed where.
Boot up and show the output of terminal commands:
```

sudo fdisk -lu
sudo parted -l
sudo blkid

```

It might be a tremendous help if the partitions were labeled:
```

sudo tune2fs -L "ubie1404" /dev/sda1

```
where whatever is in the quotes is the description you desire for the target (here sda1) partition.
Repeat as required to label all the partitions ( swap is labeled by the system)

Once we have the system booting as you desire, we do a tweak to make sure the arrangement is not changed.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by dora5 on 2015-05-30
Can't boot into the Ubuntu installation so can't provide the information requested in the second reply.   

It never once asked me if I wanted to do "something else".  I DID do the manual installation.  This was Ubuntu Server, not Ubuntu Desktop.

I do have more information.  I disabled the drive that contains the Mint and Ubuntu installations with their GRUB that can find them, in BIOS.  Then I rebooted and it booted into "error: no such Device:  and a long string of identifying information of the hard drive.   
Entering rescue mode...  
grub rescue>

I guess that the Ubuntu Server installation ate GRUB right off of the Ubuntu Desktop installation hard drive.   

So I guess the question is, how do I now rescue GRUB?    It seems to be expecting me to rescue GRUB, but I've no clue how.

Thanks!

Dora

---

### Post by Bashing-om on 2015-05-30
dora5;

 Panic not. Just proceed in a calm and orderly fashion.

All we need is a terminal from some linux . From there we can make do.

If by no other installed means, then we boot up the liveDVD of ubuntu 14.04 and get the info we need.

We can work this out from any linux terminal.

Keep in mind;
[INDENT][INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT][/INDENT]

---

### Post by oldfred on 2015-05-30
Grub rescue is saying the grub in the MBR, is not the grub it is trying to boot. Did you install boot loader to sda and are booting sdb or something similar?

       Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt 
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)


 grub rescue:

 Adjust drive, partition to your install:
ls (hd0,5)/  # Do you see 'vmlinuz' and 'initrd.img' ?


ls # Do you see (hd0), (hd0,5) ? If so, run the next command. Change if not hd0,5.
configfile (hd0,5)/boot/grub/grub.cfg

If not try this:

   set prefix=(hd0,5)/boot/grub
set root=(hd0,5)
linux (hd0,5)/vmlinuz root=/dev/sda5 ro
initrd (hd0,5)/initrd.img
boot

---

### Post by dora5 on 2015-05-30
It's fixed!

I tried several solutions online.  The one that worked was reinstalling grub using my kubuntu install dvd.

The instructions that worked were in a page full of suggestions, so I'm just going to copy it:

                     

                     
            [TABLE]
[TR]
[TD="class: votecell"][/TD]
[TD="class: answercell"]      Re-install your GRUB.

  
[LIST=1]
[*]Boot using a live cd of ubuntu. 
[*]Open a terminal and run the command
sudo fdisk -l
It lists the complete partition table of the hard disk. In there,  identify which partition you have got your linux installed on. You can  identify it using the drive size you had allocated for it and looking at  the last column of the output which will be extended or Linux for all of your linux partitions. The partition will most probably be something like /dev/sda5 or something. Remember this partition. 
[*]Create a temporary folder in your home directory (Note: You can  make the temporary folder anywhere you want. I&#8217;m using the home folder  just for the sake of explanation). I&#8217;m calling it temp for now. So that temp folder&#8217;s path will be/home/ubuntu/temp`. 
[*]Mount your linux partition there. That is, assuming that you found your linux partition to be /dev/sda5, you mount that at the temp folder by doing the following command  
  sudo mount /dev/sda5 /home/ubuntu/temp 
[*]If you want to check whether you have mounted the correct partition, go to your home folder and open temp. You will be in the / directory. In there you will find home, in which your home folder&#8217;s name will be there. Once you&#8217;ve confirmed you have mounted the correct partition, do step 6. 
[*]You have to install grub by showing the system where to read the  data from the hard disk at the beginning. Don&#8217;t worry, just run the  following command
  sudo grub-install --root-directory=/home/ubuntu/temp /dev/sda
  The /dev/sda corresponds to your hard disk name. Replace it by whatever the command sudo fdisk -l command showed you. 
[*]You&#8217;re done. You may restart your system. 
[/LIST]
     [/TD]
[/TR]
[/TABLE]


I only fixed GRUB for the hard drive that lost its GRUB.   I guess I'll have to switch back and forth in BIOS from now on.

Alternatives were to reinstall grub from the repair grub screen, which I only partially got to work, and use a grub repair utility that must be installed to a USB drive and I don't have one free.   

Now, since the bash tutorial I'm trying to do is mostly bash programming, how much do you want to bet I can just do it in terminal in Ubuntu desktop.   Sigh. 

Thanks, y'all!   I really appreciate the fast and helpful efforts at help!

Dora

---

### Post by dora5 on 2015-05-30
I tried two different versions of what Oldfred suggested.  I only got as far as the next step where you reboot into something else, and then the instructions wouldn't work.  Specifically I was supposed to cd to /boot to replace some files, and I wasn't even in the root directory and couldn't get there.

---

### Post by Bashing-om on 2015-05-30
dora5; Yepper;

That is the way to go.

What you want to do now that grub is installed is insure that it is the controlling authority, and from it boot all other systems:
```

sudo update-grub

```
This will invoke '30_os-proper' to seek out all other operating systems and chainload them onto this master grub.

Now to prevent any other system taking over this master role ( an update to any other kernel/grub ) I suggest that you turn off '30_os-prober' in the other linux systems .

You want to make sure that you are able to boot either hard drive; then if either boot breaks you can boot the other hard drive. 

[INDENT][INDENT]just my thoughts
[/INDENT][/INDENT]

---

