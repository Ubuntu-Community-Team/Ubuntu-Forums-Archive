---
title: "DD is not copying to USB"
date: 2018-08-26
forum: General Help
---

### Post by drpeppercan on 2018-08-26
Hi all,

I am trying to make a bootable USB drive with rEFInd.
It says:

"*Although you can create your own rEFInd USB flash drive, you may find it easier to download this version and copy it to your USB drive with dd or some other low-level disk copying utility*." [Source]("http://www.rodsbooks.com/refind/getting.html")

Then from its README-flashdrive.txt file I got this command line:

[FONT=courier new]dd if=refind-flashdrive-0.11.3.img of=/dev/sdc[/FONT] (modified to my situation)

Then it gives me this:

14272+0 records in
14272+0 records out
7307264 bytes (7.3 MB, 7.0 MiB) copied, 3.98659 s, 1.8 MB/s

And nothing found in the USB drive.

---

### Post by drpeppercan on 2018-08-26
Also, I just tried their TIP:
[B]
Tip[/B]: [I]If you want to make your own bootable USB flash drive, download the binary zip file or CD-R image file, prepare a USB flash drive with a FAT32 partition, and then use the refind-install program's --usedefault option, and perhaps the --alldrivers option, as in bash refind-install --usedefault /dev/sdd1 --alldrivers to install to the first partition on /dev/sdd. 
[/I][Source]("http://www.rodsbooks.com/refind/getting.html")

I entered: 
[B][FONT=courier new]sudo bash refind-install --usedefault /dev/sdc --alldrivers

[/FONT][/B][FONT=arial]It tells me: 
[/FONT][FONT=courier new][B]The rEFInd binary file is missing! Aborting installation!

[/B][/FONT]If the rEFInd binary file is: refind-flashdrive-0.11.3.img, then it's definitely there!

What am I missing?!

Thanks guys

---

### Post by hrsetrdr on 2018-08-26
I don't know, maybe chown or chmod for the rEFInd binary before dd*ing* to usb drive?

---

### Post by oldfred on 2018-08-26
If you used dd, then the image is a hybrid DVD/flash drive. But then flash drive is not formatted with standard partitions. Often partition tools do not fix it, and you have to use dd to clear the first sector so partitions can be written. See this:

[https://help.ubuntu.com/community/mkusb#Re-use_the_pendrive](https://help.ubuntu.com/community/mkusb#Re-use_the_pendrive)

---

### Post by Antnio_Almeida on 2018-08-26
you can try "sudo wipefs -a /dev/sdc" to clean the drive (must be unmounted) and then dd it again.

---

### Post by drpeppercan on 2018-08-26
Thank you so much for your input guys!
Basically the "[COLOR=#000000]sudo wipefs -a /dev/sdc" command did it! [/COLOR];)

---

### Post by HermanAB on 2018-08-27
Just some general words of advice:
Do not assume that the USB device will use the next logical device name such as /dev/sdc.
Plug the thing in, then run dmesg to make SURE that it is /dev/sdc.

You need not use dd to copy an image.  For a straight up copy, the good old kitty cat is the exact same speed and maybe less of a fat finger problem:
$ sudo cat file.img > /dev/sdc

---

### Post by drpeppercan on 2018-08-27
Thanks for sharing HermanAB :)

---

### Post by The Cog on 2018-08-27
sadly ```
$ sudo cat file.img > /dev/sdc
``` does not work because the command tries to set up writing to /dev/sdc before launching sudo. So it tries to write the device as the normal user, and gets permission denied.
Once you have a root prompt, ```
# cat file.img > /dev/sdc
``` works though.

---

