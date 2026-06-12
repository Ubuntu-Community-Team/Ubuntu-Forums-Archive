---
title: "Updated Linux headers causing grub to fail"
date: 2008-02-13
forum: General Help
---

### Post by AmpoAngelo on 2008-02-13
Alright, I have just updated to the latest version of the linux headers for Ubuntu 7.04, well, I rebooted and more updates came along, so I did those as well, rebooted.  Now I can't even get past GRUB.

In both the normal boot and in the recovery mode it gives the same error.

```

[25.701829] RAMDISK:  Compressed image found at block 0
[25.951911] invalid compressed format (err=2)
[25.952829] VFS:  Cannot open root device "UUID=d96c66e4-7c5e-4c64-903d-f4526e6606da" or unknown-block(0,0)
[25.952922] Please append a correct "root=" boot option
[25.952991] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
[25.953080] 
```

I can't type, can't do anything but reboot.  On my keyboard the "Scroll lock" and "Caps lock" keys are blinking.

Any suggestions?

---

### Post by apetresc on 2008-02-13
> **AmpoAngelo said:**
> Alright, I have just updated to the latest version of the linux headers for Ubuntu 7.04, well, I rebooted and more updates came along, so I did those as well, rebooted.  Now I can't even get past GRUB.

In both the normal boot and in the recovery mode it gives the same error.

```

[25.701829] RAMDISK:  Compressed image found at block 0
[25.951911] invalid compressed format (err=2)
[25.952829] VFS:  Cannot open root device "UUID=d96c66e4-7c5e-4c64-903d-f4526e6606da" or unknown-block(0,0)
[25.952922] Please append a correct "root=" boot option
[25.952991] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
[25.953080] 
```

I can't type, can't do anything but reboot.  On my keyboard the "Scroll lock" and "Caps lock" keys are blinking.

Any suggestions?

Boot into a LiveCD, access your Ubuntu partition, open up /boot/grub/menu.lst, find the right entry, go to the "kernel ..." line, and at the end of that line add the option "root=/dev/hda6" where, of course, "/dev/hda6" is replaced with whatever your actual root filesystem is.

That should work.

---

### Post by AmpoAngelo on 2008-02-13
> **AdrianP said:**
> Boot into a LiveCD, access your Ubuntu partition, open up /boot/grub/menu.lst, find the right entry, go to the "kernel ..." line, and at the end of that line add the option "root=/dev/hda6" where, of course, "/dev/hda6" is replaced with whatever your actual root filesystem is.

That should work.

OK, I am in the menu.lst and I see multiple instances of the word Kernel.

I see this:
```

title    Ubuntu, kernel 2.6.20-16-generic
root    (hd0,0)
kernel    /boot/vmlinuz-2.6.20-16-generic  root=UUID=d96c66e4-7c5e-5c64-903d-f4526e6606da ro quiet splash
initrd    /boot/initrd.img-2.6.20-16-generic
quiet
savedefault
```

But I see it after that with ro single, then the ro quiet comes back up, then the ro single then a memtest setting.

Is this what I edit?

Also, I see a few time it doing this "kopt=root=UUID=..."

So yeah, which one?

---

### Post by apetresc on 2008-02-13
It should be whichever kernel you installed yesterday. I forget what the version number is, but it'll be the one with the largest numerical value. The one you pasted is probably it.

There is already a root=UUID=blahblah line, so replace it. Make the line
```
kernel    /boot/vmlinuz-2.6.20-16-generic  root=/dev/hda6 ro quiet splash
```
(Again, /dev/hda6 is your / partition)
Make the same replacement in all kernel lines with the same kernel version.

---

### Post by AmpoAngelo on 2008-02-13
> **AdrianP said:**
> It should be whichever kernel you installed yesterday. I forget what the version number is, but it'll be the one with the largest numerical value. The one you pasted is probably it.

There is already a root=UUID=blahblah line, so replace it. Make the line
```
kernel    /boot/vmlinuz-2.6.20-16-generic  root=/dev/hda6 ro quiet splash
```
(Again, /dev/hda6 is your / partition)
Make the same replacement in all kernel lines with the same kernel version.OK, I will replace all instances of it.  :)

Only problem, I have no clue which HDA is my / partition.  I never really tend to pay attention to that.  :/

---

### Post by AmpoAngelo on 2008-02-13
OK, I have changed my menu.lst and it isn't working.

This is my fdisk:  [http://pastebin.com/m3c396f54](http://pastebin.com/m3c396f54)

This is my menu.lst:  [http://pastebin.com/m63c278b4](http://pastebin.com/m63c278b4)

Nothing seems to work.  :(

---

