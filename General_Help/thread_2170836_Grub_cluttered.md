---
title: "Grub cluttered"
date: 2013-08-27
forum: General Help
---

### Post by 3dmatrix on 2013-08-27
When we install Ubuntu the grub menu is very clean, nice and clear. As subsiquent upgrades keep happening the grub becomes more and more cluttered. I barely have 3 butable OS but i have dozens of entries in my Grub menu. Can any one suggest how i could clean my grub menu. I am not very comfortable with the grub 2 system.

---

### Post by Dennis N on 2013-08-27
It is possible to make a custom menu. You may want to try this after you "study up" on how its done.

A Good How-to:  [https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

---

### Post by VMC on 2013-08-27
I believe you want to edit "40_custom", found in "/etc/grub.d/". 
I don't use this stuff anymore so I could be wrong. Someone will come along and instruct you.

---

### Post by oldfred on 2013-08-27
If it just is the added kernels, you can use synaptic or command line to remove extras. I like to keep current & one older one just in case.

       Determine your current kernel:
uname -a
uname -r
In synaptic search for linux-image to choose to delete old ones
Also command line in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)
cd /boot
ls vmlinuz*
sudo apt-get purge  linux-image-[version]-generic linux-image-[version]-generic
Multiples, just be sure not to delete your current kerne.:
sudo apt-get purge linux-image-3.5.0-{XX,XX,XX,XX,XX,XX}-generic
Example:
sudo apt-get purge linux-image-3.5.0-{17,18,19,21,22,23,24}-generic

If you have other installs in other partitions you can create a simple boot entry in 40_custom and turn off os-prober.
      
 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
Older thread
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

Or you can just have grub call a config file that has all the boot stanzas you want.

 Total Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)
[http://ubuntuforums.org/showthread.php?t=1483827](http://ubuntuforums.org/showthread.php?t=1483827)

---

### Post by 3dmatrix on 2013-08-27
Is there any easy way to just remove those few extra kernel entries in grub without removing the kernel. I just wish it looks a little more clean.

---

### Post by Bucky Ball on 2013-08-27
*Thread moved to **General Help**.*

---

### Post by Crusty Old Fart on 2013-08-27
> **3dmatrix said:**
> When we install Ubuntu the grub menu is very clean, nice and clear. As subsiquent upgrades keep happening the grub becomes more and more cluttered. I barely have 3 butable OS but i have dozens of entries in my Grub menu. Can any one suggest how i could clean my grub menu. I am not very comfortable with the grub 2 system.
If you'd like to remove some of the kernels in your grub menu, the first thing you need to do is determine which kernel is the one the system uses.
The following command will tell you:
```

uname -sr

```
Then you can use the synaptic package manager to search for your installed kernels and remove the ones you don't want anymore as well as their headers.

This may be unrelated, but If you want to edit your grub file, you should make a copy of it first:
```

sudo cp -p /etc/default/grub /etc/default/grub_original

```
Then you can edit the grub file with:
```

sudo gedit /etc/default/grub

```
After you save your changes, you need to run the following command to update grub:
```

sudo update-grub

```
If you hose this up, you can revert back to your original grub file with the following commands:
```

sudo cp -p /etc/default/grub_original /etc/default/grub
sudo update-grub

```
If you want some more help with any of this, please post the output from the following command:
```

cat /etc/default/grub

```
Good luck,

Crusty

---

### Post by Crusty Old Fart on 2013-08-27
> **3dmatrix said:**
> Is there any easy way to just remove those few extra kernel entries in grub without removing the kernel. I just wish it looks a little more clean.
Not to my knowledge.

---

### Post by oldfred on 2013-08-27
If you use the customized grub by cavsfan, you create partition boot entries that boot the links in the partition. Then you have no specific entries by os-prober.

Cavsfan documented it better and has added a lot of other customization to his instructions.

 I first saw this from Ranch hand
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition. example based on sda13 change all 13's to your partition number.
At least for Ubuntu family OS's, they all place symlinks in /, called vmlinuz and initrd.img These point to the most recent versions of the kernel in the /boot folder.
More info:
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

  >  menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}



When you get that working you turn off os-prober and have no extra entries.
       In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or turn off executeable bit
sudo chmod a-x /etc/grub.d/30_os-prober
sudo update-grub

---

### Post by 3dmatrix on 2013-08-28
Ok, I will try and see if i can do all that !

---

### Post by Quackers on 2013-08-28
There used to be a utility called ubuntu-tweak that did that with a GUI. I think it's still around.

---

### Post by Dennis N on 2013-08-28
This will create a similar custom menu keeping the UUIDs for your devices, which may be preferable. There are reasons for having them.

[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

Involves just copy and paste of the generated entries from grub.cfg to your custom entry file(s) and editing the descriptions. Maintainance free if you follow the last part of that tutorial. You can disable the OS prober as well.

I used his technique, and create a separate file for each OS entry rather than one file for all. Your choice, of course.

Good luck.

---

### Post by JKyleOKC on 2013-08-28
> **Quackers said:**
> There used to be a utility called ubuntu-tweak that did that with a GUI. I think it's still around.It is, and it has a PPA that cn be added to one's sources.list to get updates.

---

### Post by 3dmatrix on 2013-08-28
Is it advisable to directly edit the grub file in /boot/grub/ or is it risky  :)

---

### Post by JKyleOKC on 2013-08-28
You can edit it, but it can be quite risky because any error can make your system unbootable. If that happens, you can recover by using a live CD, but it's a bit complicated.

If you do want to take the chance, be sure to make a backup copy of the grub.cfg file first, in the same directory, so that you can restore it should that become necessary. Then do your editing, cross your fingers, and hope it works properly.

If it doesn't, boot with the live CD, come back here, and ask for the instructions on undoing your edit. Good luck!

---

### Post by Crusty Old Fart on 2013-08-28
> **3dmatrix said:**
> Is it advisable to directly edit the grub file in /boot/grub/ or is it risky  :)
It is not advisable.
It is risky.
It may also be a really bad idea.

It is advised to edit the following grub file:
```

/etc/default/grub

```
And then run the following command to have the system change your grub configuration in the files it needs to update:
```

sudo update-grub

```

---

### Post by deadflowr on 2013-08-28
> **3dmatrix said:**
> Is it advisable to directly edit the grub file in /boot/grub/ or is it risky  :)

No it is not advisable.
The main reason, aside from possibly borking it, is that it will be overwritten the next time grub is updated.
Which usually happens every time a new kernel version is installed.

As advised earlier, just make a custom grub menu.
Follow the tut
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
and probably read through any problems others have come across
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

It's actually a lot easier than it seems.

---

### Post by VMC on 2013-08-28
> **3dmatrix said:**
> Is it advisable to directly edit the grub file in /boot/grub/ or is it risky  :)
The grub purest can and have told you not to edit grub.cfg, but since you brought up the subject, that's the only way I do it. 
And have done it that way for years. 

Depending on your experience, any so called "borking" is easily fixed.

For one thing, I keep several copies of my grub.cfg at hand, and my partition tables never change. If they did I would re-create the file.
Even if grub gets updated with a new kernel or program update, and a new grub.cfg gets inserted, I just go behind it back and copy mine in its place.

This is so easy and what's displayed - menuing, colors, etc. , I control.  You just have to maintain your UUID's. Here's my grub.cfg jus so you know:

```
    default=0
    timeout=11
    menu_color_normal=white/blue
    menu_color_highlight=light-cyan/cyan

menuentry "Windows" {
        insmod part_msdos
        insmod ntfs
        set root='(hd0,msdos1)'
        search --no-floppy --fs-uuid --set=root 3464AFFC64AFBF4C
        chainloader +1
}
menuentry "KDE" {
        insmod part_msdos
        insmod ext2
        set root='(hd0,msdos6)'
        search --no-floppy --fs-uuid --set=root 333ea2a9-69c1-4f60-a39c-acfee7fc46ee
        linux /vmlinuz root=UUID=333ea2a9-69c1-4f60-a39c-acfee7fc46ee ro modeset=0 splash quiet
        initrd /initrd.img
}
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root ee55c25c-fff8-4b60-8ff4-be9748d7eedc
    linux /vmlinuz root=UUID=ee55c25c-fff8-4b60-8ff4-be9748d7eedc ro quiet splash
    initrd /initrd.img
}
submenu Loop-Backs-ISO {
    default=0
    timeout=11
    menu_color_normal=white/black
    menu_color_highlight=black/white
    
  menuentry "ISO" {
    set root='(hd1,msdos1)'
    set isofile="/ISO/kde-saucy-desktop-amd64.iso"
    loopback loop (hd1,msdos1)$isofile
    linux (loop)/casper/vmlinuz.efi boot=casper maybe-ubiquity iso-scan/filename=$isofile noprompt noeject
    initrd (loop)/casper/initrd.lz
  }
  menuentry 'Ubuntu (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root ee55c25c-fff8-4b60-8ff4-be9748d7eedc
    echo 'Loading Linux 3.5.0-38-generic ...'
    linux /vmlinuz root=UUID=ee55c25c-fff8-4b60-8ff4-be9748d7eedc ro recovery nomodeset 
    echo 'Loading initial ramdisk ...'
    initrd /initrd.img
  }
  menuentry "Clonezilla" {
    insmod part_msdos
    insmod ext2
    gfxpayload=1024x768x16,1024x768
    set root='(hd1,msdos1)'
    linux /boot/vmlinuz boot=live live-config noswap nolocales edd=on nomodeset ocs_live_run=\"ocs-live-general\" ocs_live_extra_param=\"\" ocs_live_keymap=\"NONE\" ocs_live_batch=\"no\" ocs_lang=\"en_US.UTF-8\" ip=frommedia nosplash live-media-path=/boot bootfrom=/dev/sdb toram=filesystem.squashfs
    initrd /boot/initrd.img
  }
  menuentry "PartedMagic" {
    insmod part_msdos
    insmod ext2
    gfxpayload=1024x768x16,1024x768
    set root='(hd1,msdos1)'
    linux /boot/pmagic/bzImage64 root=/dev/sdb directory=boot edd=off load_ramdisk=1 prompt_ramdisk=0 rw loglevel=9 max_loop=256 vmalloc=288MiB
    initrd /boot/pmagic/initrd.img
   }
  menuentry 'Parted Magic' {
    set root=(hd1,1)
    linux /boot/pmagic/bzImage64 root=/dev/sdb directory=boot edd=on
    initrd /boot/pmagic/initrd.img
  }
}
```
This menu has white on blue text on first page and white on black for the submenu second "ISO" page.
When grub2 first came out, I too use to stick with scripts, but soon realized, I can control it better myself - and do.
There's always an alternative...

---

### Post by JKyleOKC on 2013-08-28
I agree that it's not advisable, but it **is** possible.

The simplest way to achieve your goal is to use **grub-customizer**, which is a GUI that does the editing for you in the correct way. See the how-to at [http://www.ubuntugeek.com/how-to-install-grub-customizer-in-ubuntu-13-04.html](http://www.ubuntugeek.com/how-to-install-grub-customizer-in-ubuntu-13-04.html) for details.

---

### Post by Bucky Ball on 2013-08-28
Sheesh, what's the matter with Grub Customizer???

[http://ubuntuforums.org/showthread.php?p=10340183](http://ubuntuforums.org/showthread.php?p=10340183)

Works fine for me making the Grub look how I like. Think you can delete through it also (not in Ubuntu so can't look right now). ;)

---

