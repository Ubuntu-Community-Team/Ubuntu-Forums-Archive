---
title: "Manual partitioning woes..."
date: 2013-06-28
forum: General Help
---

### Post by Roasted on 2013-06-28
Hello. I have a Lenovo X130e I'm trying to get working with a GPT partition table. It seems as if no matter what I try, once the installation is complete (Ubuntu GNOME 13.04) and reboot, the system goes into a reboot mode until it ultimately comes up with operating system not found. The BIOS seems very simple with no advanced configurations, but there is a toggle with UEFI/Legacy, which I have been working with.

Originally I tried this partitioning layout with UEFI disabled:

[http://i.imgur.com/8ccltpD.png](http://i.imgur.com/8ccltpD.png)

But it didn't work.

Now, I'm trying this partitioning layout, but this time with UEFI enabled:

[http://i.imgur.com/Pc8dUaT.png](http://i.imgur.com/Pc8dUaT.png)

Problem is, it too goes into a reboot loop once the installation is complete.

My goal: To use a GPT partition table and manually set up my partitions for a successful boot with UEFI or without UEFI, I don't care, just as long as I'm on Ubuntu GNOME 13.04 with a GPT partition table.

So, if the above did not work, what is the missing ingredient? What step did I do wrong? Clearly I have to be missing something... 

Thank you!

---

### Post by dino99 on 2013-06-28
[http://www.google.fr/#q=ubuntu+gpt+grub2&source=lnt&tbs=qdr:y&sa=X&ei=SEfNUZCoGefG0QWPxoGICg&ved=0CB0QpwUoBQ&bav=on.2,or.r_qf.&bvm=bv.48572450,d.d2k&fp=c6186e8a239b59e&biw=1674&bih=925](http://www.google.fr/#q=ubuntu+gpt+grub2&source=lnt&tbs=qdr:y&sa=X&ei=SEfNUZCoGefG0QWPxoGICg&ved=0CB0QpwUoBQ&bav=on.2,or.r_qf.&bvm=bv.48572450,d.d2k&fp=c6186e8a239b59e&biw=1674&bih=925)

---

### Post by Roasted on 2013-06-28
> **dino99 said:**
> [http://www.google.fr/#q=ubuntu+gpt+grub2&source=lnt&tbs=qdr:y&sa=X&ei=SEfNUZCoGefG0QWPxoGICg&ved=0CB0QpwUoBQ&bav=on.2,or.r_qf.&bvm=bv.48572450,d.d2k&fp=c6186e8a239b59e&biw=1674&bih=925](http://www.google.fr/#q=ubuntu+gpt+grub2&source=lnt&tbs=qdr:y&sa=X&ei=SEfNUZCoGefG0QWPxoGICg&ved=0CB0QpwUoBQ&bav=on.2,or.r_qf.&bvm=bv.48572450,d.d2k&fp=c6186e8a239b59e&biw=1674&bih=925)

Thanks, but I was hoping for some actual insight instead of a quick Google search to sites I've already been to. Using the first site in your link as an example, here's what it says:

[COLOR="#FF0000"]BIOS/GPT Notes

If the BIOS is setup to boot the disk in Legacy/mbr mode, installing GRUB2 on a GPT (GUID Partition Table) disk requires a dedicated BIOS boot partition with a recommended size of at least 1 MiB. This partition can be created via GParted or other partitioning tools, or via the command line. It must be identified with a bios_grub flag. The necessary GPT modules are automatically included during installation when GRUB 2 detects a GPT scheme.[/COLOR]

I did another installation today. Legacy BIOS enabled (UEFI disabled), GPT partitioning, and the following layout:

[http://i.imgur.com/h7XG7I1.png](http://i.imgur.com/h7XG7I1.png)

Which according to [COLOR="#FF0000"]requires a dedicated BIOS boot partition with a recommended size of at least 1 MiB[/COLOR] and [COLOR="#FF0000"]It must be identified with a bios_grub flag[/COLOR], suggests that this partitioning setup is correct. Unless, I'm missing something?

Likewise, due to this section here where it says [COLOR="#FF0000"]a GPT (GUID Partition Table) disk requires a dedicated BIOS boot partition with a recommended size of at least 1 MiB[/COLOR], I checked it in the partitioning screen of the installer as seen here:

[http://i.imgur.com/0t98Dvj.png](http://i.imgur.com/0t98Dvj.png)

So all in all, I have no idea what I'm doing wrong... yet I feel like I've read this guide many times...

I ended up doing a few more things:

1) Updated BIOS via bootable CD
2) Repaired Grub2 as per Ubuntu's official documentation
3) Repaired Grub2 via Boot Repair utility

Both failed. Here's the output of Boot Repair:

[http://paste.ubuntu.com/5808171/](http://paste.ubuntu.com/5808171/)

---

### Post by oldfred on 2013-06-28
Is sdb your flash drive or is system an UltraBook that has a small SSD? 

Either of your partition layouts look like they should have worked. You need an efi partition to UEFI boot or a bios_grub partition to BIOS boot. Both will not be used as you cannot install (maybe you can install but not use?) both grub-pc(BIOS) and grub-efi(UEFI). Boot-Repair will convert from one to the other by installing the correct version of grub if you have correct partitions available.

Since you only have one system, you will not get grub menu by default. And many systems have video issues and need nomodeset to fully boot. With BIOS you can hold shift key from BIOS until grub menu appears. Some have reported with UEFI that shift does not work but escape does. You may just have to experiment.

       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Info on other boot parameters
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)

Other Lenovo's. UEFI/BIOS may be similar?

 Lenovo Z580 laptop
[http://ubuntuforums.org/showthread.php?t=2112271](http://ubuntuforums.org/showthread.php?t=2112271)
See post #29 on removing Battery to get it to reset &  boot Ubuntu.
[http://ubuntuforums.org/showthread.php?t=2117760](http://ubuntuforums.org/showthread.php?t=2117760)
Lenovo Ideapad Y500 LiveUSB Problem
[http://ubuntuforums.org/showthread.php?t=2095063](http://ubuntuforums.org/showthread.php?t=2095063)
[http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500](http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500)
[http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358](http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358)
 lenovo u310  - install to SSD
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)
Lenovo IdeaCentre K410 Pentium 64-bit
[http://ubuntuforums.org/showthread.php?t=2129961](http://ubuntuforums.org/showthread.php?t=2129961)
> Discovered that on my Lenovo, if I press F12 repeatedly on startup, it takes me into a Boot Order menu. If I select Windows there, it boots into Windows. I also found that to get into BIOS at startup on my Lenovo tower, you press F1 rather than the F2 I'm used to on other computers.

      
 For the Total space you want for Ubuntu - suggest both efi & bios_grub and then installer will use correct one or you could convert from BIOS to UEFI later:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 250 MB efi FAT32 (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB bios_grub no format (for BIOS boot not required for UEFI)
gpt or MBR(msdos)
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by Roasted on 2013-06-28
Thank you for your detailed response! This is basically what I am looking at. I am not sure how on earth any of this stuff is failing. I tried to install so many times with legacy and got no where, so now I'm going to try UEFI again since you provided some detailed insight. Here is my partitioning layout that I created in the live session on GParted. Note that I wrote a new GPT partition table to it just prior to setting up these partitions.

[http://i.imgur.com/MDhW8pQ.png](http://i.imgur.com/MDhW8pQ.png)

So I take it the EFI partition does not need a boot flag? Just bios_grub for the 1 MiB unformatted partition?

Also, here's another screenshot when I'm in the actual installer just so you can get a last-second glimpse of how things are laid out prior to when the installation takes place.

[http://i.imgur.com/SSju5Gr.png](http://i.imgur.com/SSju5Gr.png)

I noticed it said it was 262 MB in size and maxed at 262 MB. Out of concern, I cancelled the installer and opened GParted. GParted said this was not the case, as it was more like 3.82 or something MB that was in use with the majority unused. Out of precaution, I wrote a new GPT table to the disk and this time made the FAT32 partition 500 MB in size.

[http://i.imgur.com/gkJKlvs.png](http://i.imgur.com/gkJKlvs.png)

Then here's the screenshot from when I was in the partitioning section of the installer so you can see what was on the radar just before I hit "go".

[http://i.imgur.com/m1CGvYf.png](http://i.imgur.com/m1CGvYf.png)

sda = SSD in laptop
sdb = USB drive I'm using as the installation media

Now you can see exactly what I did step by step. GPT table in place, the partitions and their flags outlined above, UEFI is enabled in BIOS... and still, this laptop goes into a boot loop when the installation is completed. It seems as if the only way to get a working install is to use MBR as the partition table. I suppose on one hand I could, but how on earth is GPT not working? I just don't understand... It seems like no matter what I do or what I adjust, an MBR table is literally the one and only possibility for this system to work. I can't wrap my brain around this... 

Do you have any idea whatsoever that may help understand why this Lenovo X130e refuses to boot on a GPT table whether in UEFI or Legacy mode? Legacy/MBR seems to be the only combination that works...

Mental note: Never buy a Lenovo. System76 will see all of my future purchases.

EDIT - Just a thought... would /dev/sdb having a GPT partition table (that I'm installing Ubuntu from) make a difference?

---

### Post by oldfred on 2013-06-28
You do need the boot flag on the efi partition with gpt partitioning for UEFI to see the efi partition as the ESP.

 In GPT fdisk, ESPs have a type code of EF00. In libparted-based tools, you mark the ESP as such by setting its "boot flag." Note that the libparted "boot flag" means something entirely different under MBR, and you should not set the "boot flag" on any OS partition under GPT!

---

### Post by Roasted on 2013-06-28
Thanks for the continued insight. It's appreciated.

I ended up putting in my larger SSD, which is my end goal anyway. I was simply using the smaller SSD as a test bed, but I got frustrated enough I put the larger SSD in with intention to use MBR table, but then I saw you replied, so I'm just using my larger SSD here on out. That's why you might see size differences in the following screenshots, but my goal is identical whether smaller SSD I used earlier or the larger SSD I'm using now.

Here are the steps that I did (BIOS set to UEFI):

1) Used GParted to set up partitions
2) Installed gdisk and assigned the appropriate codes to the partitions
[http://i.imgur.com/JADHpKz.png](http://i.imgur.com/JADHpKz.png)
3) Opened GParted afterwards, just to see how GParted's flags compared to gdisk's flags (visual inspection suggests nothing different)
[http://i.imgur.com/jsxco8J.png](http://i.imgur.com/jsxco8J.png)
4) Then lastly, a screenshot of the partitioning menu before I began the installation
[http://i.imgur.com/Rb4i5UM.png](http://i.imgur.com/Rb4i5UM.png)

Here's an odd note. In the last screenshot, when I selected the FAT32 partition, I didn't have "EFI Boot Partition" as an option. I saw the usual options... like swap, all of the ext's, and fat's, etc... but I didn't see EFI Boot Partition like I once did. I ignored this and continued through the installation.

and.... it still failed.

---

### Post by oldfred on 2013-06-28
When you say failed, is it a grub error from UEFI boot or just a black screen which is probably a video issue. With UEFI install I do not think it matters what you select in combo box on bottom of partitioning screen. With BIOS mode you have to install grub to MBR of sda. But with UEFI you install grub to the efi partition which I think it automatically does. With BIOS/MBR you do not install to a partition so it gets confusing, depending on which way you are installing. And that is not always obvious.

If grub error, post the link to BootInfo report.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by Roasted on 2013-06-28
When the system fires up, I see the Lenovo splash screen. Immediately following that, the laptop turns off. Seconds later, it turns back on, and begins cycling through all of the available boot menu items. I know this because it eventually tries to PXE boot, but with no ethernet cable plugged in, it bypasses that and ultimately says no operating system found.

I decided to put MBR on the larger SSD of the Lenovo so I can at least get it up and running so it's functional. My intention is to keep the smaller SSD handy so I can still do some testing to see if I can get GPT working. The more time that passes with a 100% failure rate with anything I try, the more I'm beginning to think it's a lost cause. It's not comforting to see in the official Ubuntu documentation that the Lenovo EFI is half baked. Couple that with issues I've had with Lenovo in the past at the BIOS level and I find myself just growing intolerant of their tactics. Definitely won't consider another Lenovo, but despite that, this Lenovo is still here, now, and I'd prefer to have GPT running.

Like I said though, no grub errors at all. The screen just goes black and I hear a little chirp from the unit as if it lost power, then it fires back up again. At this point, I'm probably upwards of 28-30 installs that I attempted, using different flags, different partitioning schemes, etc. I exhausted a truckload of web sites regarding the issue and feel much more aware of partition types and their relevant flags now, but even still, no such luck.

On the upside, I'm confident my System76 future is a bright one indeed. :P Thanks for your help. If you have any additional insight or ideas I'd be happy to swap out to the other SSD for continued testing. If something works, I'd blast this larger SSD and set it up accordingly, but right now I'm not overly optimistic about coming to that crossroad.

---

### Post by oldfred on 2013-06-28
Many with UEFI have to update BIOS/UEFI as that is needing corrections as well. Is your UEFI the most current verison from Lenovo.
Other Lenovos have booted but some have had major issues.
       Samsung, Lenovo & Toshiba UEFI issues
[http://mjg59.dreamwidth.org/22028.html](http://mjg59.dreamwidth.org/22028.html)

UEFI code modified to only look for certain efi files to boot. (UEFI standard says not to do that.)

 Lenovo ThinkCentre M92p only boots Windows or Redhat.
[http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg](http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg)
[http://mjg59.dreamwidth.org/20187.html?thread=774619](http://mjg59.dreamwidth.org/20187.html?thread=774619)


 Lenovo Community Bios Access
[http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2](http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2)
Lenovo Active Protection System&#8482; &#8211; for hard drive
 [SOLVED] Lenovo Y580 with working bumblebee on 12.10 - NVIDIA 660M
[http://ubuntuforums.org/showthread.php?t=2137318](http://ubuntuforums.org/showthread.php?t=2137318)

---

### Post by Roasted on 2013-06-28
As far as my Lenovo BIOS, it's as up to date. I just updated it earlier this morning.

We're kind of going down a UEFI based discussion. Just to pump the brakes a second, here's the thing that confuses me the most. If UEFI has some brokenness or issues with certain vendors, that's fine. But what about Legacy BIOS with GPT partition table? How is it Legacy BIOS Is somehow seemingly still broken when GPT is used with no UEFI nonsense in sight? This is what confuses me more than anything else in the UEFI arena...

---

### Post by oldfred on 2013-06-28
I do not have UEFI, but the CSM is a new implementation of BIOS inside or side by side with UEFI, but BIOS has been around long enough it should not be an issue.

I have been booting with gpt and BIOS since 10.10 on my 160GB drive and my SSD. I also use gpt on a 16GB flash drive just to see it it would work and it does. But you have to have the 1MBR unformatted partition with the bios_grub flag or grub will not install correctly. 

Not sure I have seen anyone with BIOS boot issues specific to gpt partitioning. But there are many other issues, some require boot parameters and others are settings in BIOS. But everyone's BIOS is different so it often takes some effort to find correct settings. 

I have to use nomodeset boot parameter on install and on first boot or until I install the nVidia proprietary drivers. Then my system works fine. But first time getting screen turned off, but system still running (I saw flash drive still installing) confused me until I learned I need nomodeset.

---

### Post by Roasted on 2013-06-29
> **oldfred said:**
> 
I have been booting with gpt and BIOS since 10.10 on my 160GB drive and my SSD. I also use gpt on a 16GB flash drive just to see it it would work and it does. But you have to have the 1MBR unformatted partition with the bios_grub flag or grub will not install correctly. 


Hmmm... I'm pretty sure I tried Legacy BIOS + GPT + 1 MB unformatted bios_grub @ the beginning of the disk with no luck... perhaps I'll give it another shot tomorrow, but I am pretty positive I tried that with no success.

---

