---
title: "Free up space in /boot"
date: 2013-02-21
forum: General Help
---

### Post by Ubun2to on 2013-02-21
I want to update the kernel to the latest in the repos, but apparently /boot does not have enough space.
I let the installer auto-partition space because I could not figure out how to do partitioning myself and retain full-disk encryption when I installed 12.10.
I have all of the images, headers, and image extras from 3.5.0-17 through 3.5.0-23 installed (according to Synaptic). What do I need to remove to free up space?
Also, when 13.04 is released, will I be able to do custom partitioning and full disk encryption? 255 MB is not my preferred /boot size (usually I make it 1 GB).

---

### Post by fuorviatos on 2013-02-21
Show us please the content of your boot directory.

> du -hs /boot

---

### Post by Ubun2to on 2013-02-21
> **fuorviatos said:**
> Show us please the content of your boot directory.

```
~$ du -hs /boot
189M	/boot
```

---

### Post by fuorviatos on 2013-02-21
Sorry, I've passed you the wrong argument. It should be 

> du -hc After running this, become root and invoke > mount|grep boot

---

### Post by ajgreeny on 2013-02-21
To see how many kernels you have at the moment open a terminal and run ```
grep "menuentry " /boot/grub/grub.cfg | cut -c 1-100
```and report the output back here.

---

### Post by schragge on 2013-02-21
> **Ubun2to said:**
> I have all of the images, headers, and image extras from 3.5.0-17 through 3.5.0-23 installed (according to Synaptic). What do I need to remove to free up space?You can uninstall the old kernels in Synaptic.

---

### Post by Impavidus on 2013-02-21
Yes, uninstall the old ones using synaptic. Just everything labeled 3.5.0-17 through 3.5.0-21. This way you'll keep the latest one and one older one, so you'll have something to revert to in case the latest one gets corrupted somehow.

---

### Post by Ubun2to on 2013-02-22
> **ajgreeny said:**
> To see how many kernels you have at the moment open a terminal and run ```
grep "menuentry " /boot/grub/grub.cfg | cut -c 1-100
```and report the output back here.

```
~$ grep "menuentry " /boot/grub/grub.cfg | cut -c 1-100
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnu
	menuentry 'Ubuntu, with Linux 3.5.0-23-generic' --class ubuntu --class gnu-linux --class gnu --clas
	menuentry 'Ubuntu, with Linux 3.5.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --
	menuentry 'Ubuntu, with Linux 3.5.0-22-generic' --class ubuntu --class gnu-linux --class gnu --clas
	menuentry 'Ubuntu, with Linux 3.5.0-22-generic (recovery mode)' --class ubuntu --class gnu-linux --
	menuentry 'Ubuntu, with Linux 3.5.0-21-generic' --class ubuntu --class gnu-linux --class gnu --clas
	menuentry 'Ubuntu, with Linux 3.5.0-21-generic (recovery mode)' --class ubuntu --class gnu-linux --
	menuentry 'Ubuntu, with Linux 3.5.0-19-generic' --class ubuntu --class gnu-linux --class gnu --clas
	menuentry 'Ubuntu, with Linux 3.5.0-19-generic (recovery mode)' --class ubuntu --class gnu-linux --
	menuentry 'Ubuntu, with Linux 3.5.0-18-generic' --class ubuntu --class gnu-linux --class gnu --clas
	menuentry 'Ubuntu, with Linux 3.5.0-18-generic (recovery mode)' --class ubuntu --class gnu-linux --
	menuentry 'Ubuntu, with Linux 3.5.0-17-generic' --class ubuntu --class gnu-linux --class gnu --clas
	menuentry 'Ubuntu, with Linux 3.5.0-17-generic (recovery mode)' --class ubuntu --class gnu-linux --
menuentry "Memory test (memtest86+)" {
menuentry "Memory test (memtest86+, serial console 115200)" {
```
I'm going to remove 3.5.0-17-3.5.0-21.

---

### Post by Jasoni on 2013-02-22
I'm using a BASH script for automating that.
This removes all those old versions but leaving the very latest untouched

dpkg --get-selections | \
  grep 'linux-image*' | \
  awk '{print $1}' | \
  egrep -v "linux-image-$(uname -r)|linux-image-generic" | \
  while read n
  do
    apt-get -y remove $n
  done

Of course if you are trying this, it's all yours own risk.
For me it has worked just fine.
Using 3.2.0-37-generic-pae at the moment.
This has worked also on earlier releases.

---

### Post by schragge on 2013-02-22
@**Jasoni**
Actually, this would do the same as your script
```

sudo apt-get -y remove '^linux-image-[0-9]' linux-image-`uname -r`+

``` But it's always a good idea to keep at least two kernels: the last and the second to last, just in case. Neither your script, nor the command above keep the second to last kernel. It's OK with me, since I've got CentOS installed on the same PC in a dual-boot setup, so I always have an alternative kernel to boot, even when I don't have a live CD/USB at hand.

---

### Post by Ubun2to on 2013-02-22
I removed the kernel images and extras up to 3.5.0-21, so I have 2 extra kernels to fall back on. Freed up 605 MB of space and I finally have the latest kernel installed.
However, I am keeping the headers. I forget which headers I had to install, but my SD card reader did not work without it.

---

### Post by ajgreeny on 2013-02-23
I only keep the header packages that correspond to the kernel number packages, so I keep headers 3.2.0-38 and 3.2.0-37 for my similarly numbered kernels.  Those header packages are fairly small, however, so will not take a great deal of room even if you leave the lot.

---

