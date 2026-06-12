---
title: "Unable to copy files from DVD"
date: 2008-04-03
forum: General Help
---

### Post by kung fu buntu on 2008-04-03
cp -r    /media/VERY_COOL_STUFF_IN_THIS_DVD/this_is_a_very_annoying_error.avi     /tmp/

cp: reading "filename" : Input/output error


I can copy the files in the DVD from windows (guest in vmware) with no problems!

```
$df -h
/dev/scd0             4.3G  4.3G     0 100% /media/VERY_COOL_STUFF_IN_THIS_DVD

$cat /etc/fstab
/dev/hda        /media/cdrom0   iso9660,udf user,noauto     0       0

$disktype /dev/scd0
--- /dev/scd0
Block device, size 1.000 GiB (1073741312 bytes)
CD-ROM, 1 track, CDDB disk ID 023BFD01
Track 1: Data track, 2.197 GiB (2358986752 bytes)
  ISO9660 file system
    Volume name "VERY_COOL_STUFF_IN_THIS_DVD"
    Application "NERO BURNING ROM"
    Data size 4.222 GiB (4533714944 bytes, 2213728 blocks of 2 KiB)
    Joliet extension, volume name "<5341><4D55><5241><495F><4348><414D><504C><4F4F><5F5F><5F47><4C41><5353><595F><4F43><4541><4E20>"

```


What is wrong over here?
How can I copy files from my Linux system?


EDIT: this is not related with my problem, but can help some people than end up here with a search, so for future reference:
Unable to mount Data DVD created under Windows XP or Vista that are in UDF format
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/106910](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/106910)

---

### Post by LaRoza on 2008-04-03
In what format is it burned?

---

### Post by bolucpap on 2008-04-03
It may be that Nero (apparently the app that created the dvd) used a different filesystem than iso9660, which is not supported by linux. This would particularly be the case if the file in question is over 2gigs. How big is the file?

---

### Post by kung fu buntu on 2008-04-03
diskinfo says:
ISO9660 file system
....
Joliet extension

(a more complete output is on my first post)


Thank you.

---

### Post by cdenley on 2008-04-03
I'm guessing it's a problem with the multi-extent workaround for files larger than 4GB. What version of ubuntu or linux kernel are you using? It seems there was support in linux for multi-extent as of 2.6.20, but I'm not sure about previous versions. Windows XP does support it.

[http://en.wikipedia.org/wiki/ISO_9660#The_4_GiB_.28or_2_GiB_depending_on_implementation.29_file_size_limit](http://en.wikipedia.org/wiki/ISO_9660#The_4_GiB_.28or_2_GiB_depending_on_implementation.29_file_size_limit)

---

### Post by kung fu buntu on 2008-04-03
I don't have any file larger than 1GB on that DVD... much less 4GB

My kernel: 2.6.21-2-amd64

---

### Post by cdenley on 2008-04-03
> **kung fu buntu said:**
> I don't have any file larger than 1GB on that DVD... much less 4GB

I guess I misread it. Try copying it to an image and see if you get an error.
```

cat /dev/dvd>test.iso

```
If that doesn't give you any errors, try mounting it. If you can't copy from the mounted image, then it must be a problem with the filesystem. It is possible that the file could be unreadable on the first try, then readable on the second. Some disc errors are intermittent.

---

### Post by kung fu buntu on 2008-04-04
Ok... this is very weird...

What I did was put the DVD in my computer, the autorun menu poped up and I opened a konqueror on it. I tried to copy the files and it failed. I tried the command line and it failed.

Then I tried it from vmware with windows as guest. It succeded.
Without me removing the DVD from the drive... One thing right after the other.



Now, today, after I rebooted my computer (and restarted hald because it wasn't poping up the autorun window) I was able to copy files from the DVD.

The only annoyance is the fact that it wasn't preserving uppercase :-(
Although there is some weirderness to it all (due to hald restart) because I have device /dev/scd0 and /dev/scd0_1 ... when I should only have scd0

Any idea on what is wrong on my fstab which affects filenames being in lowercase?
```
/dev/hda        /media/cdrom0   iso9660,udf user,noauto     0       0
```
I remind that the file system used is ISO9660  with Joliet extension.



Thank you

---

### Post by pietjanjaap on 2008-04-04
Name to long?
Name to long fot nero? See settings nero.

---

### Post by kung fu buntu on 2008-04-04
> **pietjanjaap said:**
> Name to long?
Name to long fot nero? See settings nero.It has nothing to do with names...

My current problem is that filenames aren't displayed correctly.
It seems it's ignoring the Joliet extension... all filenames are displayed in lower case, while on Windows they display correctly!

---

