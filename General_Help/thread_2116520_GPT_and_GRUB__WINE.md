---
title: "GPT and GRUB / WINE?"
date: 2013-02-16
forum: General Help
---

### Post by JiuJitsu500 on 2013-02-16
So check this and tell me how stupid I am, or what I did wrong if you're polite.

I had some severe issues with Precise, and the very day 12.04.2 was released I screwed up my Win7 install - like a boss I decided to get drunk and be a computer wizard. Who wouldn't? :popcorn:

Anyway, I decided to re-do everything. I went through live media and backed up anything important to an external HDD, and re-formatted both SSD's in my laptop - one NTFS and one Ext4. I also then remembered windows likes to make it's own little ~100MB for itself and said "screw it, I'll fix it at Windows install."

So, needless things aside, I installed Win7 SP1 on one SSD, and completely set it up the way I wanted and needed it to and it work(ED) like a champion of old. Then I installed the true master of the world, ubuntu - with so far NO problems. Then, the world came to a halt.

I noticed that 12.04.2 (fresh install made from the .iso day of release) as promised BEFORE release had the GRUB 2.00...ubuntu07 or whatever like Quantal - which it DID NOT at install or the updates thereafter so far.

I wanted to upgrade the bootloader for this ubuntu SSD (my other one still had Windows BL on it) because GRUB was NOT recognizing my Windows install - which I wanted because I'd always selected OS from GRUB on boot and I do frequently switch OS when I need to turn in a project to a professor, play video games, or do something I can't really do in ubuntu (very limited things).

All that aside, I followed [THIS]("http://www.liberiangeek.net/2012/07/how-to-install-grub-2-00-in-ubuntu-12-04-precise-pangolin/") website to "install GRUB 2 in ubuntu 12.04" which SEEMED to work until reboot. It wouldn't boot ubuntu at all, and I didn't try to boot into windows yet. So, I insert live media - and mount all sorts of jazz in the live's /mnt, then chroot that beast, and re-install all of grub. FAIL. Do it again, except -purge the crap out of GRUB (with an apt-get remove grub*), and re-install (with the reverse command). BOOM! Boot into ubuntu like a boss with GRUB 2.

I do not like GRUB 2, it sucks and won't do what I want it to, even after update-grub2, grub-pc, or grub. No update works and it still times out with 3 seconds (no matter what I set it to, nor do any parameters like 'elevator=noop' or the Core i3/5/7 parameters, etc). THEN, I decide, screw it - it'll work if I want windows, I'll just have to press ESC and stuff within 3 seconds - cool beans. Until I remembered that ANY update-grub I do will NOT register that other ssd. At all.

SO, I remembered then that this time when I installed windows it ised a GPT, which made 3 partitions - one is flagged to boot (/sdb1 the 'system'), one is unknown type in gparted (/sdb2), and one is NTFS with the win7 install (/sdb3). The bootloader is also gone when I try to boot from that ssd from BIOS. Thus, fail at Win7 boot.

SO... got ubuntu over here not recognizing a damn thing on the other hard drive (due to GUID or GPT???), and windows bootmgr missing (seems like the bootloader is missing period as it will not boot - though did before the GRUB ordeal from it's own bootloader). I prefer the bootloaders separate so my windows bootloader can boot ubuntu if GRUB failed - and I never got to that point of doing that yet.

Windows is still there, just 3 partitions instead of he standard 2 and is GPT (guid?) rather than msdos - and ubuntu still boots and works like a boss. I'm also kinf o thinking this is windows recognizing it's an SSD, but also thinking that I've used this same media before (first time was from USB, this time was from DVD - which may be why) so I don't know what's up with the windows part.

I can deal with it IF I can make ubuntu (grub2) recognize the drive for windows OR at least tell grub where to point so it can chainload windows.

AGAIN - Ubuntu boots fine from a crap bootloader, but windows does not from GRUB (even if I press ESC to get to the screen) or from it's own bootloader booted directly from BIOS.

I've tried the ~/grub.d/40_custom "title='Windows 7' {......" blah blah" but it didn't work.

MY QUESTIONS THEN ARE:

Suggestions on:

1) how to point GRUB correctly and make it show the screen every time at boot (update-grub2, update-grub-pc, and update-brub all seem to have no affect)

OR

2)install the GRUB that used to be there (it's black now, I'd like the purple one back OR the quantal one that recognized guid or gpt)

OR

3)re-install the windows bootloader so I can just choose windows by changine the boot device temporarily from the BIOS POST (win7 install disc doesn't see anything wrong, and possibly for another forum all together)

Preferably I'd like the computer to boot - see my ASUS screen - then go straight to GRUB from quantal (from BIOS setting to boot from ubuntu drive first) - where I then have 10 seconds (I know how to change /etc/default/grub) - to choose Ubuntu or Windows...

I don't think specs are important as it's nothing hardware related, just something I did very wrong. I'm finding this request very hard to find... (oxymoron???) :p

Finally now -

a minor issue since I have multiple laptops - Wine, since updating (I mean fresh install of 12.04.2) will NOT install. I'd like it for rosetta stone and a few other apps that are not native to linux (I'm US military so I need a reader for military forms - of which linux has NONE). I have the ppa for wine 1.5, but it will not install without removing xorg-lts-quantal, and a crap load of other seemingly-necessary packages... Suggestions on this?

---

### Post by oldfred on 2013-02-16
When you installed Windows, did you do it from UEFI menu or BIOS? If UEFI then Windows installs in UEFI mode on gpt partitioned drive. But Windows only boots from gpt with UEFI.

OR if installing in BIOS mode and you have BIOS set to boot from other SSD, Windows will put the (hidden) 100MB boot partition on the drive set in BIOS to boot. If other drive and then you installed Ubuntu to other drive then you may have overwritten 100MB partition. It can be repaired. 

Also if system is both UEFI & BIOS you need both systems installed in same mode either both UEFI or both BIOS to be able to dual boot. 

Has it gotten complicated yet??

Best to see details. Then we can sort out what is where and best course to follow. If just simple repairs Boot-Repair may auto fix. But it will not fix missing Windows boot files, for that you need the Windows repair CD or flash.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by JiuJitsu500 on 2013-02-18
BEautiful, and thanks for the reply. I'm glad you seem to think it's an easy fix - which for once makes me feel good that I may have not screwed up big time (bootloaders generally are easy fixes though)...

I'm away from my laptop at the moment, I'll be back on Tuesday - but for now I should provide the info. Normally I would install Win7 from a USB made in linux or windows, I've done this a number of times with only 2 partitions showing up (so windows has it's own bootloader on it's drive, while I boot from ubuntu and GRUB).

This time though I didn't have the USB with me (let a friend borrow it), so I made a DVD like old school mode. When it installed from USB on any drive I've odne it on, it's never used 3 partitions, always 2 - but the DVD is using 3 exclusively so I don't know what's happening there.

I'm using BIOS, I have no UEFI at all or even a mode to emulate it except in a VM. So booting from the DVD should have done all the same things - which it did except that one odd partition in between the win bootloader and the system itself.... hmmm.... a mistake thinking it's a UEFI system? 

Regardless, all three partitions are still there, nothing is wrong other than it won't freaking boot. GRUB on the other drive with ubuntu still boots fine, but grub itself won't see the windows drive. When I'm booted though, I can mount and do anything I like with that drive.

So GRUB doesn't see it, and windows won't boot... but every partition is all still there with data in them all - but that one in the middle is not recognized by GParted or anything, they all only see a partition of unknown format.

I'll be back to my house on Tuesday and post those results. Thanks again, and if the BIOS only things helps with a little further explanation, or anything else can be noted, then I'll do it. I don't want to re format my entire laptop again. damn bootloader. 

Maybe I'll install GRUB on the windows drive and (re-writing the MBR I'd assume) it'll see ubuntu and windows and I can boot stright from that.... hmmm....

---

