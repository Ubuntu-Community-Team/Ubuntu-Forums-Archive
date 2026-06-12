---
title: "Install (grub/initrd) failing"
date: 2013-10-26
forum: General Help
---

### Post by thespirit3 on 2013-10-26
Hi All,

I've spent a day on this and it's driving me nuts.

Fresh install of 13.10 to an SSD disk.  No matter how I try to install, booting fails (loading initrd... lots whizzes past then kernel panic, tried to kill init).

One post online suggested this was a problem when installing using custom partitioning.  I've tried all options now and can't get past this.  I've also tried installing direct from the boot media and also 'try before installing' then running the installer.  

In a desperate attempt to get something working I tried reinstalling 13.04 but this fails in the same way.  I have a feeling I upgraded from 12.x to 13.04 so perhaps I escaped any installer issues.

On my last attempt I removed all partitions (again!) from the destination disk and allowed the installer to decide the partitioning scheme.  This is less than ideal (swap on an SSD) but I was desparate. 

The boot-repair info can be found here:  [http://paste.ubuntu.com/6307147/](http://paste.ubuntu.com/6307147/)  - on some occasions it has indicated that core.img can not be found, however on this install it all looks ok.

In previous installs I've tried regenerating the initrd, trashing the MBR, reinstalling grub on both MBR and primary partition ... without any success.

Can anyone see why my installs are constantly failing?   It must be something simple but I'm failing to spot it.

Any help appreciated.   I've never had this much trouble with a simple install before :(


Steve

---

### Post by richardsdma on 2013-10-26
my personal opinion: when it comes to reinstall grub, i always go for rescatux. just boot the live session and install grub on dev/sda.

---

### Post by mansonfan78 on 2013-10-26
Is this a brand new ssd or did you have something installed on it before?  Have you tried installing an older Ubuntu, like 12.04 or 12.10?

---

### Post by thespirit3 on 2013-10-26
Old SSD, previuosly had 13.04 (upgraded from 12.10).   As this is failing so consistently I feel there's something more going on here.

I did trash the MBR with a 'dd' to make sure no previous grubs were installed there - I've also trashed/recreated partitions which I believe should remove any traces of grub there too.

The lines from the boot-repair log make me believe, at least on this occasion, that things are mostly OK:-

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 94 for .

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 13.10 
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img

Yet, it still fails.  I've tried installing 13.10 and 13.04;  I've not tried anything earlier.

It seems odd there's no other reports of this online - my hardware is fairly standard/old (AMD Phenom II, 40Gb SSDs).


Steve

---

### Post by thespirit3 on 2013-10-26
After running 'boot-repair' and letting it work its magic the following log is produced:

[http://paste.ubuntu.com/6307419/](http://paste.ubuntu.com/6307419/)

This looks no different to me so I'm guessing it hasn't spotted any errors.

Interestingly (perhaps?) boot-repair when started asks if SDA is a removable disk.   It doesn't ask this about SDB (also SSD).

---

### Post by oldfred on 2013-10-26
I do not see anything wrong. Boot-Repair runs the grub install and it returns no error. But then you seem to have something with Kernel or initrd? So that sounds like it is not configuring itself during install correctly.

Are you installing 64 bit or 32 bit version?
Verified md5sum on ISO?
Is BIOS set for AHCI?
Not sure if any other BIOS settings may be needed or not.

---

### Post by Bashing-om on 2013-10-26
thespirit3; Hi !

See oldfred's last .

Let me take a stab at this, You have not said how you have partitioned the disk(s).
If GPT then, as I understand it, one must have a separate small boot partition and install grub thereon;
If the partitioning is MBR (msdos), then install grub to the MBR sector on the device "sda".

Boot process; bios -> grub (stages) -> initramfs -> written back to hard drive.
And everything has to be in the expected place for it all to work.

[INDENT][INDENT]it is all a process
[/INDENT][/INDENT]

---

### Post by oldfred on 2013-10-26
I see drive as MBR, but to Bashing-Om's point. 
Was drive every gpt or RAID? Left over meta-data or backup gpt partition table cause issues.

---

### Post by thespirit3 on 2013-10-27
Good point regarding AHCI. I've just checked the BIOS and it's set to IDE, not AHCI.  I've never checked this in the past as things have 'just worked'.

I too wonder if some leftover grub installs have caused problems, but a 'dd' and checking the grub boot lines would indicate this is the 13.10 install.

I've now switched the BIOS to AHCI and will try installing again :)

---

### Post by oldfred on 2013-10-27
Windows7  may need a driver also, but you can just add it after booting with IDE setting if it does not boot.

My XP needed to be reinstalled with a new AHCI driver, so I finally turned it off. I was able to change back to IDE, boot Windows (and Ubuntu) and then turn it back on and boot only Ubuntu. But that much hassle confirmed I did not really need XP anymore.

---

### Post by thespirit3 on 2013-10-27
Both AHCI and IDE modes cause problems.  Googling motherboard (Asus M4A89TD Pro) shows a few others having similar issues (for example [https://bugs.launchpad.net/ubuntu/+bug/1241589](https://bugs.launchpad.net/ubuntu/+bug/1241589)).

Out of frustration I tried Mint and Debian; both failed in similar a fashion.  I've not tried a non Debian based distro.

I've also read that removing all but one HDs from the system may work.  It doesn't.

I've also tried installing to an older (non SSD) HD with the same results.

The BIOS has been updated to the latest available too.

I'm all out of ideas!

This is the latest boot-repair output: [http://paste.ubuntu.com/6312490/](http://paste.ubuntu.com/6312490/)

---

### Post by thespirit3 on 2013-10-27
Oddly enough, the last install (after a boot-repair) worked but AFAIK I did nothing different this time to any other time.

So in summary: The installer still failed but boot-repair fixed things.

Totally random.

---

### Post by oldfred on 2013-10-27
Seems a bit strange now that you have no sda, but sdb, sdc & sde.
With my desktop I do get drives normally in port order from motherboard, but I skipped one port. Using a flash drive becomes sde, but if I reboot it becomes sdb and all other drives move up one. 

Boot-repair default is to install grub to every drive. I prefer to have Windows boot loader in Windows drive. You can use boot repair, but uncheck auto repair, check update MBR and in the Advanced choose which system to install to which MBR.

I do not know what else to suggest. Kernel issues usually are related to a bad download, but you have tried several. Are there any other BIOS settings. Some that do not seem to apply may.

---

### Post by thespirit3 on 2013-10-27
Well the latest install (after a boot-repair) is working so I won't fiddle any more.  I'd love to get to the bottom of this but I fear once broken I'd lose another couple of days fixing it again.

One install failed with grub reporting no such disk (by UUID) found.  However, from within an OS the UUID was clearly listed and correct (matching grub).
Another install (I think Linux Mint) seemed to install an EFI kernel.   If anyone else experiences such problems perhaps these are good places to start looking.

Thanks for your help - but at least for now, things are working!

---

### Post by oldfred on 2013-10-27
Some BIOS, but I have not see it with UEFI, have issues (or maybe grub2) with large / (root) partitions. Most often seen with USB external drives so may be combination of USB, BIOS & grub not seeing kernel or grub files beyond 100GB in a large /. I normally suggest smaller / anyway with separate data or /home partitions.

But if it is working that is a good thing.

---

