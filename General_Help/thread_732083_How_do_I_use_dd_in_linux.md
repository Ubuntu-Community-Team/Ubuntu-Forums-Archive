---
title: "How do I use dd in linux"
date: 2008-03-22
forum: General Help
---

### Post by lorderico on 2008-03-22
I want to put bootable cd loader (bcdl) on a floppy drive to boot to on a laptop, because it is old and doesn't support booting to the cd drive.  On the web site ([http://www.ultimatebootcd.com/forums/viewtopic.php?t=512&start=0&postdays=0&postorder=asc&highlight=](http://www.ultimatebootcd.com/forums/viewtopic.php?t=512&start=0&postdays=0&postorder=asc&highlight=)), it says to use dd.  Here is what I tried:

leo@Ebuntu:/media$ dd if=/home/leo/Documents/bcdl150z.zip of=floppy0
dd: opening `floppy0': Is a directory
leo@Ebuntu:/media$ dd if=/home/leo/Documents/bcdl150z.zip of=/floppy0
dd: opening `/floppy0': Permission denied
leo@Ebuntu:/media$ sudo dd if=/home/leo/Documents/bcdl150z.zip of=/floppy0
[sudo] password for leo:
44+1 records in
44+1 records out
22829 bytes (23 kB) copied, 0.00279124 seconds, 8.2 MB/s

When I put it in the laptop "not a bootable floppy".

How do I use dd?

---

### Post by nick_h on 2008-03-22
You probably need of=/dev/floppy0 and you will need to unzip the archive.

The manual page for dd can be found by typing:
```
man dd
```

Be careful when using this command it can be very destructive if used incorrectly.

---

### Post by keratos on 2008-03-22
ditto that

dd isnt the problem here !!!!

---

### Post by anantshri on 2008-03-22
yup the problem is in your commands 
unzip file 

then on of=/dev/floppy0

that's correct

---

### Post by lorderico on 2008-03-22
Here is what I did:
I unzipped it, which created the folder bcdl150z.  There are 4 files in there:
bcdl150z.ima
bcdl_d.htm
bcdl_e.htm
bcdl_r.htm

I assume the only file I need is bcdl150z.ima

leo@Ebuntu:/media$ sudo dd if=/home/leo/Documents/bcdl150z of=/dev/floppy0
[sudo] password for leo:
Sorry, try again.
[sudo] password for leo:
dd: reading `/home/leo/Documents/bcdl150z': Is a directory
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0.000507604 seconds, 0.0 kB/s
leo@Ebuntu:/media$ sudo dd if=/home/leo/Documents/bcdl150z/bcdl150z.ima of=/floppy0
2880+0 records in
2880+0 records out
1474560 bytes (1.5 MB) copied, 0.0443526 seconds, 33.2 MB/s
leo@Ebuntu:/media$ sudo dd if=/home/leo/Documents/bcdl150z/bcdl150z.ima of=/media/floppy0
dd: opening `/media/floppy0': Is a directory
leo@Ebuntu:/media$ 

I think that media/floppy0 is the path to the floppy drive, but it won't let me use that.  Any  suggestions?

---

### Post by keratos on 2008-03-23
OMG!

USE THE IMAGE FILE (.ima) as input. Your trying to write a directory to floppy, write the IMAGE file.

and /dev/floppy0 as output.

---

### Post by plucky on 2008-03-24
> I think that media/floppy0 is the path to the floppy drive, but it won't let me use that. Any suggestions?

Try ```
cd /home/leo/Documents/bcdl150z/
ls -l
dd if=bcdl150z.ima of=/dev/fd0
```

First line changes directory to where the file is located
Second line sees if you are in the right directory if the file is there (l=letter L not 1)
Third line copies the file to the floppy drive. (fd0 is a zero not O)

Good luck.

---

