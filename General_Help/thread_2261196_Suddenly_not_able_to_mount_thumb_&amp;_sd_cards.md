---
title: "Suddenly not able to mount thumb &amp; sd cards"
date: 2015-01-17
forum: General Help
---

### Post by lisa_gibson on 2015-01-17
I don't know what happened or why or even how but I put an sd card into my comps reader and suddenly it showed the contents as a bunch of weird writing. So I tried and tried to reformat but it was in read mode yet every code I used didn't fix it, so I simply put it into my  samsung tablet and had it reformat it. Anyway, now every sd card and thumb drive I plug in says this:
```
Error mounting system-managed device /dev/sdc1: Command-line `mount "/mnt/sdc1"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```


which is weird because I've done this a billion times before ( and yes I safely remove before unplugging)
Any idea wtf is going on?

---

### Post by nerdtron on 2015-01-17
When you put on errors like that, you should put also the command that you use so that we can see and analyze your situation.
Also what program did you use/what command did you use to format your sd card?
Did you install anything to fix this?

---

### Post by lisa_gibson on 2015-01-17
i dont use commands for it. Normally when I plug it in, Lubuntu automatically mount it like it would on mac or windows. I did try the mount command and it says its already mounted o.o

---

### Post by nerdtron on 2015-01-17
It says already mounted but you posted an error that it can't be mounted? I'm confused. Also, I'm asking what is the complete mount command that you used that resulted to your error, or resulted to that it says it is already mounted.

Anyway, if you want to check if the device is already mounted and what directory it is mounted you can use the following commands:
```
mount
lsblk
df -h

```

---

### Post by lisa_gibson on 2015-01-18
I made a video showing whats happening. I plugged the device in, get a notice its not able to mount but in terminal the 8gb flash drive is mounted but it doesn't let me add anything ..<[http://youtu.be/8kvKwE_HXmU](http://youtu.be/8kvKwE_HXmU)

---

### Post by nerdtron on 2015-01-18
The flash is not formatted correctly. Just format it again and use FAT32. You can use gparted to format it (install gparted from the software center). You can follow this video for formatting the drive: [https://www.youtube.com/watch?v=CH6FwwIf0KM](https://www.youtube.com/watch?v=CH6FwwIf0KM)
If you still have problems, ask questions here. 
on last resort - try to format the usb from a windows computer.

---

### Post by lisa_gibson on 2015-01-18
but it does that to all sd cards that i use to read before.

---

### Post by nerdtron on 2015-01-18
What else did you do before this started to happen?

---

### Post by HermanAB on 2015-01-19
Howdy,

Check to see whether you have a hanging mount and remove it.

Remove all SD cards from the machine

Use mount or df to see what is mounted:
$ df

Do a lazy unmount - something like this: 
$ sudo umount -l /dev/mmcblk0/whatever

Now stick a good SD card back in and see what happens.

---

