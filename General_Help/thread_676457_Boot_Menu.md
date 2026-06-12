---
title: "Boot Menu"
date: 2008-01-23
forum: General Help
---

### Post by Frizzy350 on 2008-01-23
Hello,
I'm new here and fairly new to using Ubuntu, I apologize if I am posting this on the wrong forum or if this issue has been addressed elsewhere.

Anyway this is the situation. I was happily running a dual boot XP/Ubuntu system when eventually my XP crapped out on me (viruses, wierd hardware conflicts, other typical windows problems) so I decided it was time to reinstall windows. I did know that it would overwrite the MBR thus making it impossible for me to go back to linux without reinstalling linux or finding a solution. I looked around and thought the solution was to copy the first 512 bytes of data from the Ubuntu root partition, copy that file to windows, and add a line to the end of the boot.ini file. I did all of that (and I beleive I performed it correctly as well) and yet a menu screen for selecting an appropriate OS upon bootup will not prompt. This is my boot.ini file:

```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

C:\bootsect.lnx="Linux"
```

I used the following command in the ubuntu terminal from a boot disk to build the file:

```
sudo dd if=/dev/hda2 of=bootsect.lnx bs=512 count=1
```

If any of you linux geniuses out there have any suggestions or information that could help it would be much appreciated.

---

### Post by y-lee on 2008-01-23
I don't know  maybe some body that knows more than me could help ya. But anyway I've had great luck with [Super Grub Disk ]("http://www.linux.com/feature/57240") for fixing various boot problems

---

### Post by Frizzy350 on 2008-01-23
I'll give it a try and let you know how it turns out.

---

### Post by logos34 on 2008-01-23
> **Frizzy350 said:**
> I did all of that (and I beleive I performed it correctly as well) and yet a menu screen for selecting an appropriate OS upon bootup will not prompt. This is my boot.ini file:

```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

C:\bootsect.lnx="Linux"
```

I used the following command in the ubuntu terminal from a boot disk to build the file:

```
sudo dd if=/dev/hda2 of=bootsect.lnx bs=512 count=1
```

The easiest way is to [restore Grub from the live cd]("http://ubuntuforums.org/showthread.php?t=224351").  But SGD will work as well.

You had the command right except I don't think you copied the file 'bootsect.lnx' to the C: root directory.  You have to mount windows with write access (ntfs-3g) and change the of= path to wherever the mountpoint is.  Or copy it to a usb stick or floppy and transfer it that way.

---

### Post by Frizzy350 on 2008-01-23
Actually I originally did write the file to a windows mountpoint, THEN I went back and used a floppy and neither worked. So I had the bootsect.lnx basically right next to the boot.ini file. It's beside the point though, as SGD worked great. I thank you both and if I encounter any other issues with linux I'll be sure to return here.

---

### Post by y-lee on 2008-01-23
Glad it worked for you. SGD is a very handy tool to have around.:)

---

