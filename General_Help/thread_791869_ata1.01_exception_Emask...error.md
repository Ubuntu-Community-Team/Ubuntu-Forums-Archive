---
title: "ata1.01 exception Emask...error"
date: 2008-05-12
forum: General Help
---

### Post by Finster101 on 2008-05-12
Hi,

Just recently I started experiencing my desktop freezing. When it does, my drive light will stay on solid and my cooling fan seems to go into overdrive.   I can't move the mouse pointer  and keys like Ctrl+Alt+Backspace don't work. It seems that it is getting progressively worse and these freezes are happening more often.  Once, I was able to switch to text term (Ctrl+Alt+F1) and got the following errors repeating over and over:

ata1.01: exception Emask 0x0 SAct 0x0 Err 0x0 action 0x0
ata1.01: (BMDA stat 0x65)
ata1.01: cmd 25/00:08:e7:96:1b/00:00:17:00:00/f0 tag 0 cdb 0x0 data 4096 in

My system was working fine for a long time.  I'm really not sure what this error means.  So does this mean my hard drive is failing or drive controller went/is going bad?  I have been doing the suggested upgrades, could one of those be causing this?  I'm not even sure if this is definitely a hardware problem or is a software driver is the cause so forgive me if I posted this in the wrong forum.

I've searched for solutions to this problem but the pages I've found seem to be getting a slightly different error message: mine action 0x0 vs. there's action 0x2 frozen

Any suggestions?  What should I do?

Info:
Ubuntu 7.10
My default boot kernel is 2.6.22-14 generic
computer:emachines T3406
processor: 2.93Ghz celeron D 340
video: Intel Extreme Graphics

Thanks
Brian

---

### Post by Finster101 on 2008-07-23
I hate to follow up to my own question but I really need someone that knows more than me to help me with this problem.  I am unsure if it is the disk drive or the computer itself.  I would hate to buy a new drive, get it all setup and come to find out that it is the drive controller or motherboard causing this problem.  

I just have this machine sitting around for months now and I'd really like to be able to fix it.  Someone please help.

Anyone?

Thanks

---

### Post by ssavelan on 2008-09-16
> **Finster101 said:**
> I hate to follow up to my own question but I really need someone that knows more than me to help me with this problem.  I am unsure if it is the disk drive or the computer itself.  I would hate to buy a new drive, get it all setup and come to find out that it is the drive controller or motherboard causing this problem.  

I just have this machine sitting around for months now and I'd really like to be able to fix it.  Someone please help.

Anyone?

Thanks

I am wondering about a similar problem myself..

---

### Post by kbehel on 2008-11-30
Anybody get anywhere on this problem. This just started happening 
to me and I haven't changed anything in my system for months.

thanks,

Kevin

---

### Post by Dan Burgess on 2009-01-27
I'm trying to install Ubuntu 8.10 on a new system and I'm getting this error as well.  This board would be much more helpful if people actually posted replies with useful information.

---

### Post by zacorbul on 2009-02-24
Same thing here; I just bought a new mobo and I thought to do a clean install....same error as you guys ata1.01:exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen


Since I didn't have this problem before, I'm thinking it migh be the mobo.

If anyone knows what this problem is about, please live a line or two.

---

### Post by dsmithnc on 2009-02-27
I'm far from an expert, but I unstalled by ATI driver today and I thank solved the freeze problem.  I have a separate ATI Radeon board installed because the onboard video crashed some time ago. 

As to why it should be happening only with 8.10 I don't know, didn't seem to have that problem with 8.04.

On the upside of the new install, my D-link usb adapter worked as soon as the pc booted, no screwing around with NDIS wrapper, etc.

Dick

---

### Post by Tundro Walker on 2009-04-17
I think this has someting to do with the new libata driver (?) library they're using in the new kernel.  For some reason it's either crapping out or taking its time auto-detecting SATA (and for me, IDE) drives.  

If you edit your main boot option's "kernel" line to get rid of "splash quiet", and instead use "debug", it'll show you all the boot lines that are running during boot and (theoretically) create a boot debug file.  (I haven't been able to get it to make me the debug file, though.)

The boot process should try to mount/use the drive(s) listed in /etc/fstab.  However, for some reason the new libata delays this, so it can't mount or read or something (?) the drive right away like it should.  So, the initramfs process fails with a "can't detect root drive" error or something.

It then proceeds to probe your computer for other devices it might boot from.  For me, I'm using an old i-opener that has a built-in 16mb FDD, and a usb stick 1gb FDD.  It polls through those with the same "frozen" error lines, and finally starts probing the HDD again, but still won't boot from it.

Initramfs looks like it drops to command-line once, but keeps booting.  Then, after about a minute or two it's as if my machine has locked up.  But if I hit ENTER, I get dumped to the (initiramfs) command-line, where I can type "exit" to get out of it and the system boots normally.

I'm not really sure how to resolve this.  [One source]("http://www.ubuntu.com/getubuntu/releasenotes/810#Boot%20failures%20on%20systems%20with%20Intel%20D945%20motherboards") says to add "rootdelay=90" to the end of your "kernel" line(s) in the /boot/grub/menu.lst.  However, that's supposedly only for specific motherboards.  Another source says that it could be your computer trying to boot up in RAID format.  Don't really think that's the case, though ... not for me anyways, since I don't have mdadm installed or dmraid installed. (I did a command-line install).  [Another source]("https://bugs.launchpad.net/ubuntu/+bug/353812") says it might be a BIOS setting of AHCI instead of ATA.

This only started happening after I updated to the latest kernel, which has been using libata.  libata is the newer, better something or other to use, but it's still new enough to have and/or cause bugs and issues.  So, I'm not sure if there's a way to fix this.  But you should be able to work around it.  It's just a pain watching the comp take 3 minutes to boot, and me having to manually intercede to get it to do so.

---

### Post by wolkig on 2009-04-19
I have just created a similar problem (the 'frozen' variety) by trying to 
replace one of my hard disks. Before the operation everything worked fine.
Here are the specifics:

 new disk is  SAMSUNG SP0802N 80GB 

The disk is partitioned & formatted under Windows/Dos as FAT32 (=vfat) 
as one primary partition. Disk works fine under Windows!! 
Samsung's HUTIL program reports no disk errors!!!

Ubuntu versions 8.04 and 8.10 (from live CDs) both display the ATA.....error....frozen etc messages on boot up. 
When booting from another hard disk (8.04) the system boots after endless
error messages and does not recognize the new disk. Also Gparted does not
see it!

Interestingly, booting from Ubuntu 7.10 live CD causes no problems, 
the new disk is recognized and usable !!!!!!!!!! Gparted saw it too.

So it looks to me like a problem with (S)ATA or similar in the kernel
introduced after 7.10. Maybe a timing thing, since the new disk is the
only 7200 rpm disk in my system??

Reading suggests to try the kernel switch 'noapic' --- no success here.

Any suggestions anyone?

---

