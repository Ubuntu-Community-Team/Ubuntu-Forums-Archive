---
title: "Freeze copying over 1.5GB"
date: 2008-05-09
forum: General Help
---

### Post by cfehunter on 2008-05-09
Hi, I recently installed ubuntu hardy heron in place of vista.

Before I installed i backed up important data onto an external USB HD, the problem is that when I try to copy it to my home folder it gets as far as 1.5gb and then ubuntu locks-up.

I've tried copying through the command line, Nautilus, dolphin and konquerer.

I'm certain that it's not the hard drive as I can access it completely fine on my laptop, i have also tried transferring the data through the network and it still causes ubuntu to crash.

In konquerer i get the error message "The process for the file protocol died unexpectedly"

Thanks in advance to anybody that's willing to shed some light on why this is happening. :)

Edit:
PC Specs:
Nvidia 8800GTS
AMD Phenom 9600
Samsung 500gb Sata HD
6GB DDR2 800mhz

The external hard drive is ext3 format.

---

### Post by cfehunter on 2008-05-12
bump

---

### Post by bingoUV on 2008-05-12
1. Is this "important data" one file or many files? A directory tree?

2. I presume your home folder is also ext3. How much space is left on that device?

3. Does ubuntu crash when you transfer on network, and lock up when you do it locally? Or is it the same thing? Please specify symptoms. If you move your mouse does anything happen? Can you ctrl-alt-F1 to a command line terminal? 

4. You say it happens around 1.5GB. So is this 1.5GB transferred correctly? If yes, next time why don't you try with data that has not been transferred already?

---

### Post by cfehunter on 2008-05-12
It's important data,

all of my partitions apart from the swap are formatted ext3

there's roughly 450gb left on the hard drive

It locks up no matter how i transfer data to it, wether it's through the network, the internet, usb flash, externalHDs or DVDs.

What acctually happens when it freezes:
It reaches 1.5gb, then the progress bar stops and the data copied stays at 1.5gb. I can still move the mouse, but if i click anywhere all of the window bars dissapear and it stops responding. If I then hit ctrl + alt + F1 the screen goes black and all that's left on the screen is the console text cursor with no text. The same occurs if I try to restart the Xserver. The only way to shutdown the system after this is to cut the power.

Other info:
I've been making partitions and installing other distributions to see if it'd work with them. So far I can say that it dosn't work with fedora 8 but it works with openSUSE 10.3. The problem with the being that i don't like using openSUSE.

Thanks for the reply.

---

### Post by bingoUV on 2008-05-12
1. Is it one file or many files? 

2. The space left on the hard drive is 450 GB, but how much on the partition?

4. Why don't you try the rest of data after next boot?

---

### Post by cfehunter on 2008-05-12
I've tried it as many files and as a zip file

the partition is the entire hard drive - the 12gb swap. There's roughly 450gb of that partition.

I could try that but it's still a major issue with my system, my important data isn't the only thing it effects, it also means i cant install anything that takes up over 1.5gb of space.

---

### Post by bingoUV on 2008-05-12
Could be a filesystem problem. Can you post the output of 
```

dmesg

```
just after you encounter this failure?

You say it happens for any data that is more than about 1.5GB, not just this particular sample of data? Does it happen only for the external drive or for the internal drive also? i.e. 2GB transfer from internal drive to another location in the internal drive?

---

### Post by cfehunter on 2008-05-12
i cant do dmesg after the failure (i assume you mean before powering off the computer?) typing in the console causes the entire system to freeze, just as clicking the mouse on anything does.

I've moved 6GB from one space on the hard drive to another, dosnt seem to produce any errors.

but the issue is still there.

---

### Post by cfehunter on 2008-05-12
Interestingly suse 10.3, which allows me to copy the files to the drive, uses an earlier version of the kernel.

---

### Post by bingoUV on 2008-05-13
Sorry, I forgot that. Run a script with the following content in another terminal when you start the file copy.
```

#!/bin/bash
while [ 1 == 1 ]; do
    dmesg -c >> ~/dmesg.out
    usleep 50000 #rest .05 seconds.
done

```

After reboot, see the file ~/dmesg.out.

EDIT: added usleep in the code so that this script does not cause heat and performance problems.

---

### Post by cfehunter on 2008-05-13
thanks for the script, i ran it from when i started copying, then when the error occured it started giving killed messages.

but here's the file i got.

---

### Post by bingoUV on 2008-05-13
dmesg does not contain the error. Data that we can gather is not enough to file a bug. I can only say upgrade to the latest kernels as soon as they come and hope this should be fixed soon.

---

### Post by cfehunter on 2008-05-13
Thanks for trying to help with it anyway.

---

### Post by cfehunter on 2008-05-13
Update:
I fixed this by forcing a downgrade of the kernel, i am 100% certain it's the new version of the kernel that causes the issue. If i could actually generate any data about it i'd post it up as a bug but as things stand i'm going to have to hope it gets fixed in newer builds.

Found a better fix:
to fix this open up a console and type in

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup

Then
sudo gedit /boot/grub/menu.lst

Find the boot settings for your ubuntu ( mine is 'title		Ubuntu 8.04, kernel 2.6.24-16-generic')
Add 'acpi=off noacpi' onto the end of the kernel line just below it.

To make this stick through kernel updates:
scroll up the file and find the section beginning: "# additional options to use with the default boot option"
add 'acpi=off noacpi' to the def options line.

This fixed all my issues with ubuntu.

---

### Post by cfehunter on 2008-06-12
I've fixed this now without having to disable ACPI, i thought i'd come back and post how so that anybody with the same problem will be able to fix it.

Firstly this is a problem with the AMD Phenom. To fix it you have to update your BIOS to the latest version from your motherboard manufacturer and then enable the AMD TBL3 erroneous patch option in advanced CMOS settings.

Login to ubuntu and then everything will work fine.

---

### Post by veiloctane on 2008-07-15
> **cfehunter said:**
> Update:
I fixed this by forcing a downgrade of the kernel, i am 100% certain it's the new version of the kernel that causes the issue. If i could actually generate any data about it i'd post it up as a bug but as things stand i'm going to have to hope it gets fixed in newer builds.

Found a better fix:
to fix this open up a console and type in

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup

Then
sudo gedit /boot/grub/menu.lst

Find the boot settings for your ubuntu ( mine is 'title		Ubuntu 8.04, kernel 2.6.24-16-generic')
Add 'acpi=off noacpi' onto the end of the kernel line just below it.

To make this stick through kernel updates:
scroll up the file and find the section beginning: "# additional options to use with the default boot option"
add 'acpi=off noacpi' to the def options line.

This fixed all my issues with ubuntu.





thank you so much for this fix but unfortunately the bios update did nothing for me. and turing off acpi fixed the issue.

---

