---
title: "Grub 2.02~beta"
date: 2014-07-20
forum: General Help
---

### Post by ibjsb4 on 2014-07-20
Original Post:
> Re: Trusty to get a beta version of Grub.

After updating my 12o4 installs my grub has reverted back to 199-21 and I wish to be on my 14o4 2.02~beta install of 
grub.

It seems the way to do this is ..
```
sudo dpkg-reconfigure grub-pc
```
And then select the proper partition (this would be sda10).
```
sudo blkid -c /dev/null -o list 
    device        fs_type label    mount point       UUID
    --------------------------------------------------------------------------------------
    /dev/sda1     ntfs    win7     (not mounted)     BE4803314802E7CB
    /dev/sda5     ext4    host     (not mounted)     ac2c4726-9987-477a-82ac-f057cace70ea
    /dev/sda6     ext4    host2    (not mounted)     d455d9c2-d2dc-42a2-9806-6f2c053c4820
    /dev/sda7     swap             <swap>            81459031-d699-4006-b2d2-4e8fea3eeb63
    /dev/sda8     ext4    data     /media/lxqt/data  66f3f7aa-611c-41ae-8b58-5e0ec3b8028b
    /dev/sda9     ext4    qt       (not mounted)     9af46bac-b4ba-41d2-ab2c-83f8af35899c
    /dev/sda10    ext4    lxqt     /                 2c503fbb-572a-4a12-ac7b-3459d4043344
```
I really don't want to hose my grub, could someone confirm this is a working solution.

Thanks
Reply to original post from philinux:
> Re: Trusty to get a beta version of Grub.

This is an old thread from Trusty.

Please post a thread in say General Help. This forum is now on Utopic only.

Cheers.

The exception to this is trusty point release iso testing. 
I totally missed that :rolleyes:
    
PM from Cavsfan (short version):
> If you want to install grub on sda10 just login to the system that partition is on and enter sudo grub-install 
/dev/sda10 that will put it on that install.
```
sudo grub-install /dev/sda10

Installing for i386-pc platform.
grub-install: warning: File system `ext2' doesn't support embedding.
grub-install: warning: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.
However, blocklists are UNRELIABLE and their use is discouraged..
grub-install: error: will not proceed with blocklists.
```

:confused:

---

### Post by oldfred on 2014-07-20
I think cavsfan had a typo or he included the partition. 

You almost always install grub to the MBR of a drive if BIOS and specify the drive anyway if UEFI .

So from your install that you want to have first in grub menu and be the one in charge. Boot into that install and run install to its drive. If drive is sda, note no partition on install command.

 sudo grub-install /dev/sda

If using a live installer you have to mount partition and then install. example with sda5 as partition with install.
      
 sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#  The above command should work but they now suggest this command for grub 1.99 with Natty 11.04 or later - uses boot not root.:
sudo grub-install --boot-directory=/mnt/boot /dev/sda

---

### Post by ibjsb4 on 2014-07-20
```
sudo grub-install /dev/sda
 
Installing for i386-pc platform.
Installation finished. No error reported.
```

Worked perfectly, I am back on beta :)

Thankyou both

---

### Post by Cavsfan on 2014-07-21
> **oldfred said:**
> I think cavsfan had a typo or he included the partition.

Indeed I did mess that up. I don't know what I was thinking! My A/C guy was here over the weekend and it was like 89 inside my house for a while. 
I'll just claim brain overheating on this one. :p
You can't survive in Florida with no A/C or like we did; no more than for a couple of days. And that was not fun by any standard!

> **ibjsb4 said:**
> ```
sudo grub-install /dev/sda
 
Installing for i386-pc platform.
Installation finished. No error reported.
```

Worked perfectly, I am back on beta :)

Thankyou both

You're very welcome!
I've probably done that many, many times and forgot and left the partition in the command. 
You just have to boot into the system you want grub on if you can or through a live cd as oldfred posted.

Glad oldfred spotted that and you're good to go now! :)

I've got 5 linux systems on this hard drive and they're all on **sda** so I log into which ever one I want my grub on. 
Then enter **sudo grub-install /dev/sda** on any of them and it installs grub on that partition (system).

Not quite sure why it says "Installing for i386-pc platform." though as I have a 64bit system and it hasn't done that until recently.
Oldfred, do you know why this is? Just curious.

---

### Post by oldfred on 2014-07-21
I believe it is with 14.04 and the newer grub. If installing in BIOS mode it says i386 and if UEFI it says 
Installing for x86_64-efi platform.

I also noticed that the mod files in grub are in a different directly. 
My BIOS install:
/boot/grub/i386-pc
But UEFI systems have a different path not using i386-pc. 
It showed as an error with mod files not found as grub version difference.

---

### Post by philinux on 2014-07-21
> **ibjsb4 said:**
> ```
sudo grub-install /dev/sda
 
Installing for i386-pc platform.
Installation finished. No error reported.
```

Worked perfectly, I am back on beta :)

Thankyou both

Glad you got that sorted so simply
:p

---

### Post by ibjsb4 on 2014-07-21
> **philinux said:**
> Glad you got that sorted so simply
:p

Just glad I asked; who know what kind of heart break I would of had with my idea :D

---

### Post by Cavsfan on 2014-07-22
> **oldfred said:**
> I believe it is with 14.04 and the newer grub. If installing in BIOS mode it says i386 and if UEFI it says 
Installing for x86_64-efi platform.

I also noticed that the mod files in grub are in a different directly. 
My BIOS install:
/boot/grub/i386-pc
But UEFI systems have a different path not using i386-pc. 
It showed as an error with mod files not found as grub version difference.

I'm in 14.10 right now and I notice that I do indeed have this /boot/grub/i386-pc and I don't have windows 8 so no UEFI. 
It just sort of threw me off because I had never seen that before but a few times recently while I have a 64 bit system and thought something was wrong.

> **philinux said:**
> Glad you got that sorted so simply 
:p

It would have been sooner if I hadn't been asleep at the wheel. :p Luckily Oldfred pointed out my mistake.

> **ibjsb4 said:**
> Just glad I asked; who know what kind of heart break I would of had with my idea :D

Take a gander at the green link in my signature and you could have a simple custom grub screen with any picture you want (sized at your default resolution) with custom colored fonts.
It will display whatever you want it to display for each OS as whatever you put between the quotes is what appears at boot time.

My grub screen on Mint 17 (Mint has an added file **06_mint_theme** that sets the colors of the box and the the menu entries in the box),
Then the bottom and top have another color:

[[IMG]http://www.zimagez.com/miniature/20140629115939.jpg[/IMG]]("http://www.zimagez.com/zimage/20140629115939.php")

My grub screen on Ubuntu 14.04 which has just 2 colors: normal and highlight, but still overwhelmingly beautiful ;):

[[IMG]http://www.zimagez.com/miniature/20140501grub2.jpg[/IMG]]("http://www.zimagez.com/zimage/20140501grub2.php")

It's not near as complicated as it looks. When Ranch hand first showed me that I was like "I don't think I can do that". But after a while I seen it's not really that hard.
The more I looked at it the simpler it got. I now have 6 OSs on this box and can customize a new one with my eyes closed practically. 
Copying the custom **/etc/grub.d/06_custom** file from another OS makes it even simpler for me.

There are only about 4 files involved and not much changes to make except in **/etc/grub.d/06_custom**

Here is mine from Utopic 14.10:

[PHP]#!/bin/sh
echo 1>&2 "Adding Precise Pangolin 12.04 LTS, Trusty Tahr 14.04 LTS, Utopic Unicorn 14.10 LTS (Devel Branch), Mint 13 Maya LTS, Mint 17 Qiana LTS and Windows 7"
exec tail -n +4 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Precise Pangolin 12.04 LTS" {
    set root=(hd0,2)
        linux /vmlinuz root=/dev/sda2 ro quiet splash
        initrd /initrd.img
}
menuentry "Precise Pangolin 12.04 LTS (Recovery Mode)" {
    set root=(hd0,2)
        linux /vmlinuz root=/dev/sda2 ro single
        initrd /initrd.img
}
menuentry "Trusty Tahr 14.04 LTS" {
    set root=(hd0,6)
        linux /vmlinuz root=/dev/sda6 ro quiet splash
        initrd /initrd.img
}
menuentry "Trusty Tahr 14.04 LTS (Recovery Mode)" {
    set root=(hd0,6)
        linux /vmlinuz root=/dev/sda6 ro recovery nomodeset
        initrd /initrd.img
}
menuentry "Utopic Unicorn 14.10 (Devel Branch)" {
    set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro quiet splash
        initrd /initrd.img
}
menuentry "Utopic Unicorn 14.10 systemd (Devel Branch)" {
    set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro quiet splash init=/lib/systemd/systemd
        initrd /initrd.img
}
menuentry "Utopic Unicorn 14.10 (Devel Branch) (Recovery Mode)" {
    set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro recovery nomodeset
        initrd /initrd.img
}
menuentry "Mint 13 Maya LTS" {
    set root=(hd0,7)
        linux /vmlinuz root=/dev/sda7 ro quiet splash
        initrd /initrd.img
}
menuentry "Mint 13 Maya LTS (Recovery Mode)" {
    set root=(hd0,7)
        linux /vmlinuz root=/dev/sda7 ro recovery nomodeset
        initrd /initrd.img
}
menuentry "Mint 17 Qiana LTS" {
    set root=(hd0,8)
        linux /vmlinuz root=/dev/sda8 ro quiet splash
        initrd /initrd.img
}
menuentry "Mint 17 Qiana LTS (Recovery Mode)" {
    set root=(hd0,8)
        linux /vmlinuz root=/dev/sda8 ro recovery nomodeset
        initrd /initrd.img
}
menuentry "Windows 7" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1CFC7A8DFC7A60C6
    chainloader +1
}[/PHP]

---

