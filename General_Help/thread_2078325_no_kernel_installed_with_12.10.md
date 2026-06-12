---
title: "no kernel installed with 12.10?"
date: 2012-10-30
forum: General Help
---

### Post by linuxhippy on 2012-10-30
I am having trouble getting XUbunto 12.10 64 bit version installed on my AMD64 Athalon Desktop.  I downloaded the iso and it checked out with the sha1sum.  I then burned it as an image file in XUbuntu 12.04.  I have my harddrive partitioned into many slices and always do fresh installations while keeping my original installs.

So, I installed this on a new partition and got an error during installation that my cd was messed up and the installer would not continue...it suggested that I clean my cd burner and re-try.  I decided that it would be faster just to do a harddrive install using the iso file.

I googled around and found an Ubuntu page that explains how to do a harddive install from Linux here: [https://help.ubuntu.com/community/Installation/FromLinux]("https://help.ubuntu.com/community/Installation/FromLinux")

I followed the instructions under the section "Live CD".  I modified grub and got it to install from my harddrive with no errors.  Then I rebooted and found that it didn't modify grub.  I went into XUbuntu 12.04 and found that it didn't install a new vmlinuz file.  

What do I do now to boot my new system?

---

### Post by hal8000 on 2012-10-30
Ubuntu installation instructions are here:

[http://www.ubuntu.com/download/help/install-desktop-latest](http://www.ubuntu.com/download/help/install-desktop-latest)

I have also installed the 54bit version but using Ubuntu (if I want Xubuntu I just install Xfce4).


Boot from the live Xubuntu CD and mount your / partition, then list the contents of /boot

 ls -lh  /boot
total 24M
-rw-r--r-- 1 root root 826K Oct  9 20:54 abi-3.5.0-17-generic
-rw-r--r-- 1 root root 145K Oct  9 20:54 config-3.5.0-17-generic
drwxr-xr-x 5 root root 4.0K Oct 26 23:33 grub
-rw-r--r-- 1 root root  15M Oct 26 23:33 initrd.img-3.5.0-17-generic
-rw-r--r-- 1 root root 173K Oct 11 15:10 memtest86+.bin
-rw-r--r-- 1 root root 175K Oct 11 15:10 memtest86+_multiboot.bin
-rw------- 1 root root 2.8M Oct  9 20:54 System.map-3.5.0-17-generic
-rw-r--r-- 1 root root 4.9M Oct 17 16:04 vmlinuz-3.5.0-17-generic

The above shows the default kernel and initial ramdisk image installed by Ubuntu 12.10

I would first check you have those files, then see if grub2 has created a stanza to load Ubuntu.
What was 2 simple lines in grub legacy has become very complicated in grub2. Again when / is mounted you would have to type:

less /boot/grub/grub.cfg

Burried deep with grub.cfg will be a stanza that contains menu entry for
Ubuntu (Xubuntu) in your case, followed by partition, kernel and an initrd.
This will also state the kernle name and initrd that Xubuntu is trying to boot.


Sample is shown below:



menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menu
entry_id_option 'gnulinux-simple-19bfec2a-7fcd-462d-a4b8-a5bdf0f422dc' {
recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-
efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  19bfec2a-7fcd-462d-a4b8-a5bdf0f422
dc
        else
          search --no-floppy --fs-uuid --set=root 19bfec2a-7fcd-462d-a4b8-a5bdf0
f422dc
        fi
        linux   /boot/vmlinuz-3.5.0-17-generic root=UUID=19bfec2a-7fcd-462d-a4b8
-a5bdf0f422dc ro   quiet splash $vt_handoff
        initrd  /boot/initrd.img-3.5.0-17-generic
:


To fix the problem again from the live Xubuntu CD, see if you can load the kernel from Ubuntu sources and manually place it in /boot
Its more complicated and will require some linux experience, but aside from reinstalling I cannot think of another way to solve this.

---

### Post by linuxhippy on 2012-10-30
Got it to boot by copying the vmlinuz file from my installation partitionn which was the file from the installation cd in /casper.  I copied it to the new installations directory of /boot.  Then in XUbuntu 12.04 I rebuilt and installed grub:

sudo update-grub
sudo grub-install /dev/sda

Then I rebooted and Ubuntu 12.10 was in the GRUB selection and booted ok.  Once logged in I did an update.

Unfortunately, I cannot get 12.10 to make a GRUB file that will boot itself.  It will only boot frum the GRUB file that 12.04 makes and then 12.10 is not the default boot choice.  I knew how to re-arrange the boot order in GRUB1 but GRUB2 will take my looking into it.  I'm sure it's doable, though!

---

