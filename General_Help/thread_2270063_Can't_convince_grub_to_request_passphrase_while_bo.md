---
title: "Can't convince grub to request passphrase while booting with encrypted root partition"
date: 2015-03-19
forum: General Help
---

### Post by eleedom on 2015-03-19
I ended up corrupting a partition when I hard powered down my laptop after it would not restore from a suspended state.  While trying to bring the machine back to life I ran boot-repair a few times and while it eventually did seem to fix the corrupted filesystem It also mannaged to mess up my grub config.  I can now boot to a liveusb and decrypt and mount my root partition but have had no luck getting grub to recognize my root partition is encrypted when i try to boot from my hard disk.  it will boot, load the kernel and then fail out to a prompt because it cannot find my root drive.  it never asks for a passphrase like it used to, so I am thinking it is looking for my root drive but not finding it because it is on an encrypted volume.

The installation is a vanilla install of ubuntu 14.04 with the full disk encryption option checked.  i have an unencrypted boot partition /dev/sda2 and an eccrypted partition /dev/sda3 that has my root drive on it.  This is the grub menu entry that I am trying to use to boot fron the /boot/grub/grub.cfg file:
```
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-bb35b0e3-7198-4c6b-8590-1ae19e0efe12' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  cdf0792a-58b2-4d7f-b853-f2a0efc8b5c1
        else
          search --no-floppy --fs-uuid --set=root cdf0792a-58b2-4d7f-b853-f2a0efc8b5c1
        fi
        linux   /vmlinuz-3.16.0-31-generic root=/dev/mapper/ubuntu--vg-root ro cryptdevice=/dev/sda3:ubuntu--vg 
        initrd  /initrd.img-3.16.0-31-generic
}
```

as you can see i have set the cryptdevice=/dev/sda3:ubuntu--vg param in the kernel command line args.  ubuntu--vg is the volume group that the root logical volume lives on. 
r```
oot@ubuntu:/# lvdisplay
  --- Logical volume ---
  LV Path                /dev/ubuntu-vg/root
  LV Name                root
  VG Name                ubuntu-vg
  LV UUID                svyDfV-qCPL-Q7B5-Pz0N-rENB-zeg8-gQLSCf
  LV Write Access        read/write
  LV Creation host, time ubuntu, 2015-02-06 11:04:27 -0500
  LV Status              available
  # open                 1
  LV Size                229.82 GiB
  Current LE             58834
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:1
   
  --- Logical volume ---
  LV Path                /dev/ubuntu-vg/swap_1
  LV Name                swap_1
  VG Name                ubuntu-vg
  LV UUID                2cTdos-nm6o-J8Hr-YDac-eL97-Iqtl-an5uI9
  LV Write Access        read/write
  LV Creation host, time ubuntu, 2015-02-06 11:04:27 -0500
  LV Status              available
  # open                 0
  LV Size                7.91 GiB
  Current LE             2025
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:2


```
 I am a tad unclear if this is the correct value to place after the encrypted device in the cryptdevice phrase.  still, can't see how this would affect being prompted for the passphrase.  it could only be validated after the volume is decrypted.

I have been able to mount the root drive and other filesystems to a mount point in the live session and chroot to it.  from there i have been able to reinstall grub-efi and run update grub with new parameters but i still cannot boot from the hd install

this is my core question.  what do i need to do prompt the kernel/grub (cryptdevice is supposedly passed to the kernel but i could not find it mentioned in the kernel params in the documentation i found, so is it actually the kernel that uses this parameter, or does the boot loader intercept it and take care of the decrypting itself before it passes execution to the kernel?) to recognise it is dealing with an encrypted volume and ask for a passphrase?  I have tried inmod lvm and cryptodisk.  that seemed to make no difference.  i saw some mention on some arch linus forums about adding encryption modules to the mkinitcpio config but my understanding is that in ubuntu this handled as part of the package installs and regardless i can't see how anything could have affected the kernel and initrd images that are in the boot dir since the time the machine stopped booting.
none the less i did run update-initramfs to see what happens a got this output:
```
root@ubuntu:/# update-initramfs -u -k 3.16.0-31-generic
update-initramfs: Generating /boot/initrd.img-3.16.0-31-generic
cryptsetup: WARNING: invalid line in /etc/crypttab for sda3_crytp - 
cryptsetup: WARNING: invalid line in /etc/crypttab for sda3_crytp -
```

not sure what those warnings are all about. here is my crypttab:
```
root@ubuntu:/# cat /etc/crypttab 
sda3_crypt UUID=6f3a73fa-a4a3-4556-88bc-5d650e6bb2a2 none luks,discard

```

does anyone have any suggestions?  they would be much appreciated. please let me know if i can provide any other information.

---

### Post by oldfred on 2015-03-20
If you look at this thread:
[http://ubuntuforums.org/showthread.php?t=2103864](http://ubuntuforums.org/showthread.php?t=2103864)
And his pastebin.
[http://paste2.org/BNeBxCJs](http://paste2.org/BNeBxCJs)

His linux line is :
	linux	/vmlinuz-3.2.0-29-generic root=/dev/mapper/sda1_crypt ro   quiet splash $vt_handoff

---

### Post by eleedom on 2015-03-20
Sounds like he is possibly experiencing something similar to my issue.  i would suggest that he needs to add the "cryptdevice=" phrase to his command line.  this may solve his problem, at least that is what i have seen others do and have success.  although the looping behavior he is seeing may be orthogonal to the encryption issues.

---

### Post by eleedom on 2015-03-20
could anyone clarify if the process that should be doing the mount of the root file system is the kernel, the boot loader or the initrd/initramfs process?  if the later, is the busybox prompt that i am dumped into after the failure to boot the same process as the one that is to decrypt and mount the filesystem?  if so, is it possible for me to run that command in the prompt just to make sure it will succeed? if so, what is the command?

---

### Post by oldfred on 2015-03-22
Found this, some more info on stanza:
[https://wiki.archlinux.org/index.php/GRUB#Encryption](https://wiki.archlinux.org/index.php/GRUB#Encryption)


This is standard partition manual boot. You then can use your encrypted commands.


If you do not get grub menu as you only have one install, you should be able to hold shift key from BIOS with BIOS boot or use escape key with UEFI boot.
When you get to grub menu, you can change to grub's command line and manually add each boot line or any you want to try.
 See post #10 by drs305 
[http://ubuntuforums.org/showthread.php?t=1916698](http://ubuntuforums.org/showthread.php?t=1916698)

      
```
 set prefix=(hd0,5)/boot/grub
set root=(hd0,5)
linux (hd0,5)/vmlinuz root=/dev/sda5 ro
initrd (hd0,5)/initrd.img
boot


```

---

