---
title: "Burn CD via CLI"
date: 2006-12-19
forum: General Help
---

### Post by Mau on 2006-12-19
How does one burn a CD via the command line?

---

### Post by meng on 2006-12-19
It's been a long time since I bothered doing this (I got lazy) but back when I did I used this resource:
[http://www.yolinux.com/TUTORIALS/LinuxTutorialCDBurn.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialCDBurn.html)

---

### Post by SteveF on 2006-12-20
> **Mau said:**
> How does one burn a CD via the command line?

I wrote a script to do it, but basically you use mkisofs to make an iso file from your data.  I use something like:
mkisofs -v -r -J -V volumename -o outfile.iso /data/cddata

volumename is just a name that gets placed as the volumne name on the CD
outfile.iso is the name of the file create by mkisofs
/data/cddata is the folder containing the data I want to burn

Then use cdrecord to burn the iso to a cd.  Something like:
cdrecord -v speed=8 dev=/dev/hdc -data -tao -multi outfile.iso

/dev/hdc is the CD device

Some people say they need to run cdrecord as sudo.  I haven't had to (I do get a message from cdrecord stating I should have root access to the program but I have never had a problem with the CD burned).

This all assumes you mean burning a data CD.

If you want to burn an audio CD.  Use something like:
cdrecord -v speed=8 dev=/dev/hdc -audio -eject /data/cdaudio

/data/cdaudio would be the location of the WAV files.

mkisofs would not be needed in this case.

hth,

Steve

---

### Post by pickarooney on 2006-12-20
I've a couple of old scripts lying around that do it in different ways.
Not sure how much you might need to change for Ubuntu and whatever hardware devicesyou have.

```

#!/bin/bash
echo "Enter CD title:"
read title

shorttitle=`echo "$@"|sed s/\'//g`
mkisofs -J -R -V "$shorttitle" -o "$shorttitle".iso "$@"
cdrecord -v -pad -tao driveropts=burnfree speed=8 dev=/dev/dvd:1,0,0 "$shorttitle".iso

```

---

### Post by wpshooter on 2006-12-20
> **Mau said:**
> How does one burn a CD via the command line?

I have absolutely NO idea, but my question is why would you want to when there is such a nice GUI program like K3b available for FREE for everyone to use ???

---

### Post by Mau on 2006-12-20
Thanks guys.

The reason is because my system pretty much failed (hd might be  dieing) and when I booted  into gnome my keyboard wouldn't work, making things pretty useless.  So, I wanted to burn some data as an extra backup to a CD in the recovery console.

Turned out cdrecord got corrupted and thrown into lost+found, so I just gritted my teeth and did a re-install (keeping my home partition in tack).  Everything seems fine now without any data loss.

---

