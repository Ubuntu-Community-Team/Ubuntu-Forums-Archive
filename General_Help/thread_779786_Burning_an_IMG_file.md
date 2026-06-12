---
title: "Burning an IMG file"
date: 2008-05-03
forum: General Help
---

### Post by AyAn4m1 on 2008-05-03
I've looked on these forums and on google to no avail... I have a .img file about which the 'file' command says:

"bootdisc.img: DOS floppy 1440k, x86 hard disk boot sector"

It's a bootable CD image that I'm trying to burn so that I can flash my BIOS. I've tried renaming it to an iso, and the gnome CD writer tells me it's an invalid iso. I've tried using ccd2iso to convert it into an iso, but it says "Unrecognized sector mode (0) at sector 0!" and produces a 0-byte iso file. I've exhausted all of the options that I've found, other than installing k3d, but I'd really rather not install all the KDE stuff unless I have some reassurance it'll work... Anyone have any suggestions?

---

### Post by warp99 on 2008-05-03
> **AyAn4m1 said:**
> I've looked on these forums and on google to no avail... I have a .img file about which the 'file' command says:

"bootdisc.img: DOS floppy 1440k, x86 hard disk boot sector"

It's a bootable CD image that I'm trying to burn so that I can flash my BIOS. I've tried renaming it to an iso, and the gnome CD writer tells me it's an invalid iso. I've tried using ccd2iso to convert it into an iso, but it says "Unrecognized sector mode (0) at sector 0!" and produces a 0-byte iso file. I've exhausted all of the options that I've found, other than installing k3d, but I'd really rather not install all the KDE stuff unless I have some reassurance it'll work... Anyone have any suggestions?

Well that's a floppy image, so your best solution is just dd the image to  a 1.44 floppy:
```
dd if=/home/foo/file.img of=/dev/fd0
```
make sure you have a floppy disc in the drive before you issue the command.

---

### Post by AyAn4m1 on 2008-05-03
I don't have a floppy drive, and I found the image on some part of the Nero site about burning a bootable CD for flashing a BIOS. The image is definitely intended for use with a CD writing program, I just need to get it on a CD from Ubuntu (the guide it came from was written to be used with Nero for Windows and I can't get NeroLinux). Is there any way to either burn an img to disc or convert an img to iso from Ubuntu that doesn't involve ccd2img or renaming the file?

---

### Post by bingoUV on 2008-05-03
At the risk of wasting electricity, plastic etc. you could always force burning of a CD. With an empty CD in your optical drive, do the following
```

sudo dd if=/path/to/img/file of=/dev/sr0

```

Confirm that your optical drive device node is /dev/sr0. Just the existence of this file /dev/sr0 is a good indication. Gnome CD writer should tell you more.

[B]K3b
[/B]    I think installing k3b will be less than a 10MB download (including essential kde libraries). You could always stop before the download starts when apt-get tells you how much it will need to download.
```

sudo apt-get install k3b

```

---

### Post by AyAn4m1 on 2008-05-03
I tried using dd and it seemed to write data according to the console output, but upon ejecting and reinserting the disc, it was still blank. I also installed k3b, which said the image seemed "like an unusable file." I ended up using a spare Windows machine I had to burn the image, no problems. Thanks for your help.

---

### Post by warp99 on 2008-05-03
> **bingoUV said:**
> 
[B]K3b
[/B]    I think installing k3b will be less than a 10MB download (including essential kde libraries). You could always stop before the download starts when apt-get tells you how much it will need to download.
```

sudo apt-get install k3b

```

You can always use the -s parameter to do a simulation install so the command string would be:
```
sudo apt-get -s install k3b
```
that way you know exactly what will happen before you commit.

---

