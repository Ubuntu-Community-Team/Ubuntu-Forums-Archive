---
title: "faking / remounting root FS for ubuntu installers?"
date: 2008-05-13
forum: General Help
---

### Post by ndizazzo on 2008-05-13
I've been trying to compile all versions of Ubuntu onto a DVD for my own personal use, but have been running into some issues getting the Ubuntu installers working correctly.

Here are the details:

I've laid out the DVD filesystem as follows:

/
/isolinux (contains boot loader files with modified Ubuntu boot loader)
/amd64
/x86
/jeos

under each of the directories is a complete image of each installation CD (copied using cp -rT /media/cdrom0/ ./x86 etc.). I then modified the isolinux.cfg file (in /isolinux) to launch the appropriate installer (kernel /x86/install/vmlinuz, and so on).

The problem is, once the installer has launched, it looks for the installation files at the root of the CD media, for example:

1) It looks for /cdrom/.disk, when it's actually in /cdrom/x86/.disk
2) It looks for /cdrom/install, when it's in /cdrom/x86/install
etc.

Is it possible to fool / remount the filesystem or use some other form of hackery to achieve having multiple distributions install from one DVD?

Any help is much appreciated!

---

### Post by pointone on 2008-05-14
You could possibly try:

```
mount --bind /cdrom/<version> /cdrom
```

---

### Post by ndizazzo on 2008-05-14
I thought of something like that, but it needs to happen automatically for every version of the installer on the DVD before the installer is kicked off. It's possible to drop out of the installer into another terminal and run that command, but I would need it to happen automatically, so that would mean editing the installer or having some "pre-installer" script run after the kernel is loaded. 

Is there a specific place to do this?

---

### Post by ndizazzo on 2008-05-15
I've been looking through the documentation for kernel parameters, but I don't think there will be anything there that will help...

I'm also poking around the initrd.gz file to see if there's anything that can be done there.

If anyone has any more ideas, please let me know!

---

### Post by pointone on 2008-05-15
It's most likely that you'll need to edit the actual compressed filesystems and add an init script that does this.

---

### Post by ndizazzo on 2008-05-16
So far:

1) I've edited the compressed initrd.gz image by extracting it to a working directory.

2) I've edited (./var/lib/dpkg/info/cdrom-detect.postinst) and added the line:

```
mount --bind /cdrom/x86 /cdrom
```

in two places where the cdrom is mounted successfully.

3) I've tarred and re-gzipped the initrd image and put it on my disc image, but when the kernel tries to mount the initrd.gz image, it gives a kernel panic:

```
Kernel Panic - not syncing: VFS: Unable to mount root fs on unknown-block (104,1)
```

I assume this is because I havn't recreated the initrd.gz file correctly.

I suppose:

```
tar zcvf initrd_new *
gzip -c initrd_new > initrd.gz

```

is not the way to do it :)

Does anybody know how?

---

### Post by ndizazzo on 2008-05-20
For those interested, I've accomplished what I am trying to do! 

[LIST=1]
[*]I created the DVD structure as I've mentioned above, each distribution is in a subdirectory of the root of the DVD.

[*]I unpacked each of the initrd.gz files (this creates the root file structure in the tmp_initrd directory) using:
```
mkdir tmp_initrd; cd tmp_initrd; gunzip -cd ../initrd.gz | cpio -i
``` 

[*]I spent a few hours digging for where the cdrom is actually mounted, it is done in the following dpkg postinst script: ```
/var/lib/dpkg/info/cdrom-detect.postinst
```

[*]I added this mount command in the file AFTER the cdrom had been successfully mounted: 
```
mount --bind /cdrom/<VERSION> /cdrom
```

[*]I recompiled the initrd image using:
```
find . | cpio -o -H newc | gzip > ../newinitrd.gz
```
[/LIST]

The installer kicks off by loading the linux kernel, and the new initrd.gz file is loaded into the ramfs, with a subdirectory of the DVD automatically mounted as the root DVD directory. The Ubuntu installer no longer complains about not having the correct disc!

Thanks pointone!

---

