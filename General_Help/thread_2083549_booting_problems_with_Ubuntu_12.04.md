---
title: "booting problems with Ubuntu 12.04"
date: 2012-11-12
forum: General Help
---

### Post by tedr108 on 2012-11-12
I have installed Ubuntu several times without issue.  Just built a new computer with an Asus P8Z77M Pro mother board with EFI.  I am trying to use EFI for booting, but my computer only boots every third or fourth time, usually locking up at a purple screen.

My partitions:
/EFI partition -- 258MB
/swap -- 20480MB
/(root) -- 25600MB
/home -- rest of disk

Here is a link to boot-repair output ... boot-repair claimed to be successful:  [http://paste.ubuntu.com/1354688]("http://paste.ubuntu.com/1354688")

It's a little confusing because the boot does work on occasion.  When it does not work, besides the purple screen lock, I also can get a notice to go in and change CSM settings under Boot Info in the BIOS.  I've tried every CSM setting under the sun, but may have missed something.

If it is a valid option, I am happy to go "Legacy" and avoid EFI altogether ... this has been rather frustrating.

---

### Post by ercherramon on 2012-11-12
tries to do an update-grub to update your GRUB. it may have altered the order of your partitions.

---

### Post by oldfred on 2012-11-12
I think Boot-Repair tried fixing your install, but you have mixed UEFI files & MBR(msdos) partitions.

With UEFI you have to use gpt partitions, so the efi partition has the correct gpt code, which is set with the boot flag in gparted. It really is a gpt code of ef00.

You can boot Ubuntu in BIOS mode with gpt partitions or with MBR partitions. But if also installing Windows, you can only use UEFI with gpt or BIOS with MBR.

Your old efi partition shows Windows efi files. Did boot repair add those or did you have a Windows install? Are you installing Windows? And in UEFI? Then you would have to reformat hard drive to gpt. 

There may be other UEFI/BIOS settings that make a difference on booting. 

So right now it looks like you are in BIOS mode. Have you turned off UEFI in UEFI menu? That may be part of the issue.

---

### Post by tedr108 on 2012-11-13
> **ercherramon said:**
> tries to do an update-grub to update your GRUB. it may have altered the order of your partitions.

Thanks for the advice.  I did try this and it seemed to update, but still the same issues.  Mostly getting the CSM parameters warning message now when I try to boot.  About the only way for me to get into Ubuntu is to go into the CSM parms, change something unimportant, then F10 to Save and reset.  This must attack the bootloader from a different angle and slip in there!

I'll keep trying things...and reading dozens of internet advice pages!

---

### Post by tedr108 on 2012-11-13
> **oldfred said:**
> I think Boot-Repair tried fixing your install, but you have mixed UEFI files & MBR(msdos) partitions.

With UEFI you have to use gpt partitions, so the efi partition has the correct gpt code, which is set with the boot flag in gparted. It really is a gpt code of ef00.

You can boot Ubuntu in BIOS mode with gpt partitions or with MBR partitions. But if also installing Windows, you can only use UEFI with gpt or BIOS with MBR.

Your old efi partition shows Windows efi files. Did boot repair add those or did you have a Windows install? Are you installing Windows? And in UEFI? Then you would have to reformat hard drive to gpt. 

There may be other UEFI/BIOS settings that make a difference on booting. 

So right now it looks like you are in BIOS mode. Have you turned off UEFI in UEFI menu? That may be part of the issue.

Thanks, Fred ... I'll do my best to answer your questions:

I have not installed Windows on this disk ... may have been boot-repair.  I have, however, run Windows 7 on this machine on a totally separate disk.  I typically install Windows and Ubuntu on separate disks, so I don't have to worry about a Windows update trashing my MBR and Windows/Ubuntu fighting for control over the bootloader.  When I am installing my OSs, I never leave both disks plugged in at the same time.  My machine either defaults to Ubuntu or Windows disk, and I F8 when I want to go to the non-default OS disk.

I get the feeling that, even with separate disks, I have to be careful with the UEFI/Bios settings.

UEFI is on right now, I believe ... this BIOS interface is rather confusing, I must say, but the CSM parameters are on Auto at this time.  I know that I did not consciously turn it off.

You given me some food for thought. I think that I will be able to do better research now that you have told me some of my issues.

I had been reading up on gpt partititions.  Don't quite understand all of these concepts, but will see if I can figure this out.  Thank you for your answer ... it taught me a lot.

---

### Post by YannBuntu on 2012-11-13
Hello

In the B-R log, we see that the BIOS is correctly setup to boot the HDD in UEFI mode:

```
=================== UEFI/Legacy mode :
BIOS is EFI-compatible, and is setup in EFI-mode for this installed-session.
```

We also see:

```
/EFI/Boot/bootx64.efi /EFI/Boot/bootx64.efi.grb 
                       /EFI/ubuntu/grubx64.efi 
                       /EFI/Microsoft/Boot/bootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgfw.efi.grb 
                       /EFI/Microsoft/Boot/bootx64.efi 
                       /EFI/Microsoft/Boot/bootx64.efi.grb
```

The presence of /EFI/Boot/bootx64.efi.grb means that Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi).
Same for bootmgfw.efi and bootx64.efi.

The fact that partitioning is MsDos (not GPT) should not be a problem, as the UEFI specs don't require GPT (@Fred: i sent you a PDF with recent UEFI official specifications). And your case shows us that it is possible to use UEFI on MsDos.
However, UEFI on MsDos is not common (it is the first time I see it), and may not be reliable. This would explain why it sometimes fails to boot in your case, but the problem may be something else.

If i were you, i would format the disk GPT via Gparted, then reinstall Ubuntu, and see if this solves the problem.

---

### Post by tedr108 on 2012-11-13
> **YannBuntu said:**
> If i were you, i would format the disk GPT via Gparted, then reinstall Ubuntu, and see if this solves the problem.

Thanks, I will do this.

Since Gparted is not a part of the Ubuntu 12.04 bootable install CD (I tried), do I install Gparted on a USB stick and run it from there while the CD is actively running on my desktop?  Then, I assume that I still use "Something Else" as the install option, but when I go into it, the partitions will already be set up nicely.  Is that correct?

Out of curiosity, if I install Ubuntu from a CD-Rom and choose "Something else" and do the partitions as shown in the OP, is that GPT or not?  If it is, then I can only assume that the install of 12.04 does not reformat the boot sector to protect Legacy setups ... it is not even possible to "Format" in the EFI partition area of the install. I always remove all partitions and recreate them, but when I do this, some of the boot sector is still "used"...not a good sign, probably.

Sorry if I am using the wrong terminology above ... all of my Ubuntu installs over the last couple of years (mostly for Android development) have run so smoothly, that I am still a noob when it comes to much of this.  Everything worked, so I stayed ignorant of what was going on behind the scenes.

Really appreciate you responding here...

---

### Post by oldfred on 2012-11-13
I just booted 12.04.1 liveCD and gparted is part of it. As far as I know it always has been part of the liveCD, but not normally installed by default as you cannot edit the partition you are booted into.

I have BIOS but use gpt. I have created my gpt partitions with gparted. Under device, create partition table, advanced, choose gpt not the default msdos (MBR) partitioning.

You can download gparted on its own liveCD.

[http://partedmagic.com/](http://partedmagic.com/)
[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)

If drive has no partitions, Ubuntu will use gpt by default if drive is something over 1TB. Not sure if it defaults to gpt with UEFI but it should. But again you can boot in either BIOS or UEFI mode and that does make a difference on how it installs.

---

### Post by tedr108 on 2012-11-13
I typed gparted at the desktop, I thought that it did not find it while on live CD.  I'll try again next time ... it makes sense that gparted would be there.

OK, used Gparted Live from a CD and formatted my drive gpt.  When I went to install 12.04, I did the "Something Else" option ... although the partitions showed up, they did not seem to be labeled correctly, so I added /home and /, etc.  Anyway, everything installed and I still can't boot ... locking up at the purple screen or giving me this error:  /dev/disk/by-uuid/6612eb.... does not exist.  I'm beginning to think that there is simply something wrong with my disk.  The first time I booted Gparted Live, it did not find my hard drive ... the next time it did.  Maybe something similar is going on with my booting process and it is not finding the drive.  I am going to try this on a different drive altogether.

Is that how you are supposed to do it?  Use Gparted, then go to Something Else on the install?  

Haven't been able to get this new setup to boot at all yet ... so sort of stuck.

Anyway, I've got no idea what is going on at this point.  And, I'm a little worn out from 2 days of constant reinstalls, EFI/Bios settings changes and whatnot ... think I need a break.

Thanks to everyone who tried to help.  When I can get a new drive, I'll give it a go and hopefully figure this thing out.

---

### Post by tedr108 on 2012-11-13
Just ran the Live Ubuntu 12.04 CD again and was able to get to Gparted as stated.  The partitions look good except that 1Mb "bios_grub" (or whatever) partition at the beginning is unknown format.  Once I get a new disk, I'll do it this way, instead of running the Live Gparted CD.

---

### Post by tedr108 on 2012-11-13
Woohoo!!!! I hope...

OK, ran the Ubuntu 12.04 Live CD again and double checked Gparted.  The / and /home labels were not showing up on their respective partitions, so I re-entered them and shut down and rebooted.  I just shut down and restarted 3 times in a row ... it succeeded each time!

Now, I will say that a "restart" does not work ... it locks up on the purple screen.  However, a complete shut down and start has been working.

Thanks to all who helped me out ... (and those who were silently giving me moral support behind the scenes!)

(P.S.)  Reboot appears to be working now, too.

---

### Post by YannBuntu on 2012-11-14
> **tedr108 said:**
> The partitions look good except that 1Mb "bios_grub" (or whatever) partition at the beginning is unknown format. 

I think it's normal. (the BIOS-Boot partition must have no filesystem, see [https://help.ubuntu.com/community/DiskSpace#BIOS-Boot_or_EFI_partition_.28required_on_GPT_disks.29](https://help.ubuntu.com/community/DiskSpace#BIOS-Boot_or_EFI_partition_.28required_on_GPT_disks.29) )

If you are not sure, I think it is easier to:
1) use Gparted to just format the disk in GPT  (create no partition)
2) let the Ubuntu installer create all partitions (including the BIOS-Boot one) for you, by choosing the "Install Ubuntu on the entire disk" option.

---

### Post by tedr108 on 2012-11-14
> **YannBuntu said:**
> I think it's normal. (the BIOS-Boot partition must have no filesystem, see [https://help.ubuntu.com/community/DiskSpace#BIOS-Boot_or_EFI_partition_.28required_on_GPT_disks.29](https://help.ubuntu.com/community/DiskSpace#BIOS-Boot_or_EFI_partition_.28required_on_GPT_disks.29) )

If you are not sure, I think it is easier to:
1) use Gparted to just format the disk in GPT  (create no partition)
2) let the Ubuntu installer create all partitions (including the BIOS-Boot one) for you, by choosing the "Install Ubuntu on the entire disk" option.

Thanks, I'll probably just do that next time ... would have saved me a ton of trouble.  The only reason I partition myself is so that I can make a big swap (2.5x RAM, which is overkill, I'm sure) and a big /root folder (25GB).  I do occasionally compile Android ROMs, which can take a long, long time, so I thought a big swap might help.  It would be interesting to see what the automatic partitioning comes up with.

After all was said and done, I now know the 2 main things I did wrong:  1) did not included the "bios_grub" partition at the beginning and 2) did not have the disk formatted GPT.  I'm pretty sure that #1 was the killer.  This was my first experience with an EFI setup ... had to learn some things the hard way.  :mad:

That's a great link you sent me, by the way.  Not sure how I missed that one in all my research...

---

### Post by tedr108 on 2012-11-17
Sorry to drag this up again, but thought this was worth noting...

Although some of the things I did to get my Ubuntu 12.04 up and running helped with stability in booting, I finally figured out the real problem:

**I was formatting the boot partition as ext2, rather than ext4.  Not good!**  Once I found out that it should be ext4, no failed boots ever ... not even with msdos, rather than gpt, formatting.

Too bad I did not mention the ext2 formatting in the OP, I'm sure a number of you would have caught that right off.  Not sure when that started to be an issue ... always had ext2 on past PCs/laptops, even with 12.04, and never had problems.

Also, from what I read, it seems that I could not do a pure EFI boot because even Win7 requires some legacy stuff.  So, I think my Ubuntu is probably booting Legacy, rather than EFI, but not sure.  Don't really care at this point.  My Ubuntu is booting very quickly.

Thanks for all the help.

---

