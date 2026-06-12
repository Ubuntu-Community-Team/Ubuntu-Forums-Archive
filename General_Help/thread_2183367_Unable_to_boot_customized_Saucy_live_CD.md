---
title: "Unable to boot customized Saucy live CD"
date: 2013-10-24
forum: General Help
---

### Post by maddog39 on 2013-10-24
I put together a customized version of the Ubuntu livecd for myself to perform various tasks on my systems from a live USB key using UCK and UNetbootin. My current builds of this ISO are done with UCK 2.4.7 on Ubuntu 12.04 LTS and work fine. A few days ago I decided to try to make the jump to building on Ubuntu 13.10 except I can't get my Ubuntu 13.10 based ISO's to boot, at all. The stock Ubuntu 13.10 ISO works just fine on my USB thumb drive, and boots as expected on all my systems. After I make my changes using UCK and write it to the tumb drive with UNetbootin, it fails to boot with the dreaded: "(initramfs) Unable to find a medium containing a live filesystem".

Console output during boot failure (I'm guessing not really relevant though):
```

/sbin/udevadm: line 1: ELF: not found
/sbin/udevadm: line 3: syntax error: unexpected "("
/sbin/udevadm: line 1: ELF: not found
/sbin/udevadm: line 3: syntax error: unexpected "("
/sbin/udevadm: line 1: ELF: not found
/sbin/udevadm: line 3: syntax error: unexpected "("

BusyBox v1.20.2 ...
...

(initramfs) Unable to find a medium containing a live filesystem
/sbin/modprobe: line 2: syntax error: unexpected word (expecting ")")
/sbin/modprobe: line 2: syntax error: unexpected word (expecting ")")

```

casper.log  (last few lines; inside initramfs environment):
```

(initramfs) cat casper.log
...
calling: test-builtin
error reading /ib/udev/hwdb.bin: No such file or directory
load module index
unload module index
mount: mounting /dev/sdf1 on /cdrom failed: Invalid argument
mount: mounting /dev/sdf2 on /cdrom failed: No such device
/init: line 7: couldn't open /dev/sr0: no medium found
/init: line 7: couldn't open /dev/sr0: no medium found
(initramfs) Unable to find a medium containing a live filesystem
/sbin/modprobe: line 2: syntax error: unexpected word (expecting ")")
/sbin/modprobe: line 2: syntax error: unexpected word (expecting ")")

```

Things I've tried to resolve / investigate the issue with no success:
[LIST]
[*]Rebuilding the ISO without any package / kernel updates (would normally perform update && dist-upgrade) 
[*]Reverting to stock isolinux/txt.cfg 
[*]Compared stock initrd.lz to modified initrd.lz: found no modifications except updates to casper.conf (default username, etc) 
[*]blkid in the initramfs environment correctly identifies all devices and filesystems 
[*]any kind of mount performed inside initramfs env. results in: "failed: Invalid argument" 
[/LIST]

So basically, I'm really stuck, and having a hard time pinpointing exactly what the problem is / where it originates from. Does anyone have any idea how I can get my custom disk images to boot?

Thanks!

---

### Post by Githlar on 2013-11-09
I had the same problem (minus the 'unexpected )' errors). For some reason they added crazy redundant UUID assertions in Saucy's Casper, making it nearly impossible to remaster your own if you don't know what you're doing. I had to follow the code manually line-by-line until I figured out exactly what was going wrong.

The problem is that there is a default UUID stored in the initrd.lz. If the UUID of the disk you're booting doesn't match that (it won't) and it's not in one of a couple of places it will not mount your disk.

There are a few way to get around this:

1. Add 'ignore_uuid' to the boot parameters (ugly)
2. Add a boot paramter UUID=[your disk's UUID] (see next)
3. Add a file in the .disk folder called casper-uuid-[something], or just edit casper-uuid-generic and add the UUID of your disk there (can be found from /dev/disk/by-uuid). The file should only contain one line -- the UUID --, and no newline at the end.
4. Remaster the initrd.lz and remove the /conf/uuid.conf file so it defaults to blank (disabled):
[LIST]
[*]Copy initrd.lz out of the disk image into its own directory.
[*]cd to the directory and enter this command: cat initrd.lz | unlzma | cpio -i; rm initrd.lz
[*]rm conf/uuid.conf
[*]find . | cpio -H newc -o | lzma -9 > initrd.lz
[*]Then simply copy the initrd.lz to where you want it.
[/LIST]

The only problem with options 2 and 3 is that if you re-format your USB and copy the files back over to it (or to somebody else's USB), it won't work until you update the UUID. Using the first or last method is a sure-fire way making sure you don't run into that issue.

Another issue I ran into is that I dd'ed the ISO onto my drive the last time. It then reformatted it using gparted, which left 2047 sectors before the start of the first partition. And because there's another partition in that space from the ISO (the EFI partition), Casper kept finding the FAT in that area and following the data to garbage areas preventing it from booting.

---

