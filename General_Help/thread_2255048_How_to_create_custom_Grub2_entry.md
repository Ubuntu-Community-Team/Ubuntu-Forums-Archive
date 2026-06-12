---
title: "How to create custom Grub2 entry?"
date: 2014-12-01
forum: General Help
---

### Post by Mike_Walsh on 2014-12-01
Evening, everybody.

Admins; sorry if this is in the wrong forum! Please relocate if necessary....thanks.

I think I asked a variation on this a couple of months ago, but I honestly forget....memory's not what it was, these days. I run Ubuntu 14.04 Trusty as my main OS. My main, and sole hard drive, contains the following:

1)[COLOR=#cc3300] Ubuntu 14.04[/COLOR] on [COLOR=#ff0000]sda1[/COLOR]
2) /home on [COLOR=#ff0000]sda3[/COLOR]
3) Linux-swap on [COLOR=#ff0000]sda4[/COLOR]
4) On [COLOR=#ff0000]sda2,[/COLOR] the remaining partition, I've installed Puppy Linux 'Tahrpup' 6.0.

I discovered, a couple of months back, when I installed a different version of 'Puppy' to a partition on sda, that running 

> sudo update-grub

has absolutely NO effect. GRUB2 simply CANNOT 'see' Puppy. And so, having installed Puppy to the partition that I used at the time, there was NO WAY to boot into it; as far as GRUB was concerned, there was nothing there.

I've been researching this recently, and I understand that it's possible to add custom entries to GRUB. From what I can figure out, as long as GRUB knows where to find vmlinuz, and initrd, then it OUGHT to be able to boot the distro installed on the specific partition, but.....I'm perfectly willing to be corrected on this. You're never too old to learn!

I do find it hard to believe that with all these various distros constructed around various different versions of the same kernel, they STILL have a hard time of it being able to 'see' each other. 'Sudo update-grub' detects an 'unknown Linux distro' on sda2.....but appears not to be able to do anything with it.

What I would like to know (and I'm perfectly willing to provide whatever information might be needed), is how you actually write a custom entry, in such a way that GRUB understands it, and is able to act on it. I've had a look at this wiki:-

[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

I seem  to have one anomaly, which I don't understand the reason for. I don't appear to have an /etc/grub.d/40_custom file at all. I DO, however, have a 42_custom file that looks to be identical.

All of this notwithstanding, I do understand, and appreciate, that for something like GRUB to work correctly, the syntax, etc., has to be absolutely spot-on. This is why I'm asking for a wee bit of assistance with the possible construction of such a 'custom' entry.

One other query, which is related to this thread. Will Ubuntu work with ANY other boot-loader apart from GRUB2? Puppy comes with something called Grub4DOS, which claims to be able to detect, and construct a boot menu around, ANY distros it can find. Not knowing sufficient to be able to accept OR refute such a claim, I thought it best to ask for some advice from the people who ought to know more about this than I do.....the very knowledgeable members of this forum.

Or would it be possible to install Puppy's boot-loader into it's own partition, and then construct the menu in such a way as to be able to ('chainload'?) to it, from the main GRUB menu?

Even the members of the Puppy Forums admit that an undertaking such as this, while possible, is a MAJOR pain in the nether regions..! ANY advice would be much appreciated.

If you don't ask, you don't get..... ;)

Regards,

Mike.

---

### Post by yancek on 2014-12-01
Entries you can try in  your 42_custom file are below.  Run sudo update-grub after saving the change.  The first is just a simple chainload entry which will only work if you have a bootloader installed on the Puppy partition.  I've never used Grub4Dos, it's just a modified version of the original Grub.  The second entry below I used to boot Puppy from Grub2,

> menuentry 'CHAINLOAD PUPPY' {
insmod ext2
set root=(hd0,2)
chainloader +1
}

You will need to change the UUID in both locations in the entry below to whatever sda2 is on your machine.  You can get that with the blkid command.

> menuentry "Puppy-Lupu"{
        insmod part_msdos
        insmod ext2
        set root='(hd0, msdos2)'
        search --no-floppy --fs-uuid --set=root 47891df9-aa27-4df9-99ac-aa96276780ac
        linux /puppy/vmlinuz root=UUID=47891df9-aa27-4df9-99ac-aa96276780ac
        initrd /puppy/initrd.gz
} 

---

### Post by Mike_Walsh on 2014-12-02
@Yancek:-

Thank you very much for the reply.....and for the thought that must have gone into it. When you say you used the second entry to boot Puppy from GRUB2, did you actually try this for real?

Not expecting any sort of reply to this one, I went ahead, took the plunge, and installed and configured Grub4DOS onto my system. I shall keep your suggestions in a safe place, just in case I decide to do things differently; Grub4DOS isn't as PRETTY to look at as GRUB2, but at that stage of boot, it's not really 'eye-candy' I'm after.....we'll see. Thanks for working it out for me, anyway. Very much appreciated.

I WAS a wee bit apprehensive about doing this. After 6 months of careful tweaking, adjusting (even 'coaxing', at times..!), I've now got 'Trusty' exactly how I would like to keep it for the next 2-3 years. I was afraid that all my hard work would be for naught, and need re-doing from scratch, simply due to having 'messed up' GRUB to such an extent that the system would no longer be accessible...

I needn't have worried. 

Having never manually installed GRUB before (& not knowing how complex or otherwise that procedure might be), the installation of Grub4DOS seemed pretty straight-forward. So, for anybody else out there who, like me,  

a) is 'oddball' enough to want to try and run Ubuntu AND one or more of the Puppies, and

b) having experienced how fast the Puppies are on a flashdrive, wants to try them out on your hard drive (because of the much higher read/write speeds with an HDD), this is how I went about it:_

[COLOR=#ff0000]--------------------------------------------------------------------------------------------------------------------------------------[/COLOR]

You either have an existing Ubuntu installation, or you're installing a new one. If new, then install Ubuntu FIRST.

Then:-

1) Create a partition (primary OR logical, depending on what you want).

2) Install Puppy to this partition as a FRUGAL install. Rather than installing all the various 'folders' in the normal way, this keeps ALL the puppy files together in one folder. Sounds crazy, I know, but this is how Puppy works.

3) Having installed Puppy, locate the Grub4DOS installer in the setup menu. Bottom-left corner; 'Menu'>'Setup'>'Grub4DOS installer'.

4) Launch the installer, and follow the instructions carefully. It's quite self-explanatory; just make sure you tell it to install Grub4DOS to the MBR of the drive you've just installed Puppy on.

[COLOR=#ff0000]&#8203;-------------------------------------------------------------------------------------------------------------------------------------[/COLOR]

If you're in too much of a rush to remember this part of the procedure, or simply forget about it, don't worry. Puppy uses a 'Live-CD' in very much the same way as the 'buntus do. Simply run Puppy from the 'Live-CD', and install Grub4DOS from there.

The only difference you notice with the 'Grub4DOS' boot menu & start-up procedure is that where GRUB2 hides all the system stuff from you, with the former you get to see it all! But I NOW have what I've wanted for a while; a dual-boot setup with Ubuntu AND one of the 'Puppies', with the option to choose which I want.....and it WORKS. \\:D/

And even with an old, single-core Athlon 64, it FLIES; its feet don't touch the ground! I'm WELL chuffed with it. :D


Regards,

Mike. ;)

---

