---
title: "Grub help!"
date: 2008-04-30
forum: General Help
---

### Post by Serpreme on 2008-04-30
Currently i am modifying my initrd file that gets loaded by the menu.lst. 
But sometimes i find that i need to make some changes to the initrd file, which usually result in me needing to recompress it.
Now what i am wondering how to do is;
1) Find the existing initrd file
2) And modify it via a script for schedule maintence.

---

### Post by danwood76 on 2008-04-30
What you should do is edit the files that go into making the ramdisk.
These are located /usr/share/initramfs-tools.

then run:
```

sudo update-initramfs -u

```
To rebuild the file and have it palced in your /boot dir

What are you exactly trying to get out of the initrd?
Its intended to only initialise hardware in the system before the kernel starts to load.

---

### Post by Serpreme on 2008-05-01
Hmm good infromation!
I'm working for a company right now that uses a initrd file to load script files that check a image server for updates and then places them if need be.
So 99% of all the work is done through this initrd file and these scripts that are part of it.

What i am trying to do is have a script access a FTP, pull down a script that will give it parameters and allow me to make modifications to the initrd file.

Thanks for the info!

---

### Post by Serpreme on 2008-05-06
Alrighty, i figured out i need to mount the partition to access it.
Go me. Learn something new everyday. 
So now i just need to make a script to download --> mount --> replace the initrd file --> i suppose.
I tried recompressing the current content of the initrd in ram, and it gave me about 3x files then normal.

---

### Post by danwood76 on 2008-05-07
You could setup a script so that when the linux system boots it updates the initrd for you, unless space isnt really an issue.

Never really tried what your trying to do.

---

### Post by Serpreme on 2008-05-07
Hmm it "updates" initrd, as in, it takes the current existing state in ram, and smacks on the partition where it resides?

Or it takes another initrd, and swaps it?

---

### Post by danwood76 on 2008-05-07
Are you actually trying to rebuild the initrd or are you just downloading an image?

If your downloading an image you could just copy the image by ftp and update the menu.lst to boot the new initrd and then issue a reboot command so it loads the new one up (after the reboot).

What I was saying before is that you could modify the scripts within the linux partitions initramfs folder, when the kernel loads get it to issue the update then reboot, this would probably lead to a smaller initramfs file.

---

