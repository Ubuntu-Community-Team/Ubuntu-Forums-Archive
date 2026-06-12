---
title: "gnomebaker annoyance"
date: 2006-09-26
forum: General Help
---

### Post by kpkeerthi on 2006-09-26
Gnomebaker detects my burner but it does not properly populate mount point (as you can see from the attachment, the mount point is just blank). I have to manually open the preferences dialog and set the mount point to /mnt/cdrom **each time I launch the app**. Not a big deal but annoying. Would appreciate if someone could help me fix this.

The Gnome baker forum appears to be completely umaintained and spammed. [http://gnomebaker.sourceforge.net/forum/viewforum.php?f=1](http://gnomebaker.sourceforge.net/forum/viewforum.php?f=1)

---

### Post by orb9220 on 2006-09-26
What does your fstab look like?

---

### Post by kpkeerthi on 2006-09-26
Thanks for asking... I should have posted it already... 

```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

```

---

### Post by orb9220 on 2006-09-27
Well your fstab entry looks right. If you can read and write thru gnome or other burning apps then it is gnomebaker.

You can right-click an iso file and burn or insert cd and rightclick to copy and if that works then you will know.

If it is a scsi drive that may be why gnomebaker has a problem with it.

---

### Post by yopnono on 2006-09-27
What is the permission on "/dev/scd0" it should be root:cdrom
Also you can try to reconfig the cdrecorder.

```
sudo dpkg-reconfigure cdrecord
```

---

### Post by kpkeerthi on 2006-09-27
Yes its a scsi drive on my notebook. But I don't have problems burning using K3B or nautilus. So I guess... its gnomebaker issue.

@yopnono 
I don't have access to ubuntu right (i'm at work). But I'm sure the permissions are correct. I'll confirm as soon as I reach home.

I really need to get gnomebaker working as I use only GNOME and I don't prefer to have the whole KDE libs just to burn my disks. 

Thanks for your help guys.

---

### Post by kpkeerthi on 2006-09-27
btw... Can someone please point me in right direction where to log this bug or contact the gnomebaker developers? Thanks.

---

### Post by yopnono on 2006-09-27
Well you can always use *complete removal* for the gnomebaker and reinstall it, or use Nero, Bonfire/Brasero. They work just fine in gnome.

EDIT: And Graveman. And no I have no idea where to find the devs for gnomebaker.

---

### Post by kpkeerthi on 2006-09-27
True... but multisession doesn't work with brasero and graveman. I tried nero but its not free.

---

### Post by yopnono on 2006-09-27
Ok did not know that. Have you tried to contact them from this page.
[http://sourceforge.net/project/memberlist.php?group_id=127397](http://sourceforge.net/project/memberlist.php?group_id=127397)

---

### Post by yopnono on 2006-09-27
Or just download the source and build it.

---

### Post by kpkeerthi on 2006-09-27
I'm using the latest version of gnomebaker (0.6). I got the deb from [http://www.getdeb.net]("http://www.getdeb.net"). Earlier versions were much worse. 

Sorry for being dumb... Is building from source any different than using the prepackaged software? How would it help.

---

### Post by kpkeerthi on 2006-09-27
Reported this as bug in gnomebaker as I could get K3B working fine without a problem:
[https://sourceforge.net/tracker/index.php?func=detail&aid=1566659&group_id=127397&atid=708499](https://sourceforge.net/tracker/index.php?func=detail&aid=1566659&group_id=127397&atid=708499)

---

### Post by yopnono on 2006-09-27
> **kpkeerthi said:**
> 
Is building from source any different than using the prepackaged software? How would it help.

No not really.

---

### Post by yopnono on 2006-09-27
Have you tried to clear out the gnomebaker profile in your home folder.
Make a backup and then delete it and try.
 
/home/*user*/.gconf/apps/GnomeBaker

---

### Post by Jallu59 on 2006-10-10
Buggy version of Gnomebaker. Look for a patch there:

[http://ubuntuforums.org/showthread.php?t=272033](http://ubuntuforums.org/showthread.php?t=272033)

Yours 
Jallu59

---

### Post by darrenm on 2006-10-10
Yes building from source is very different from using a package from getdeb. I've always had problems with the packages from there.

Why didn't you use the Ubuntu repo version?

---

### Post by puppy on 2006-10-10
I have the same problem as the OP, in that GnomeBaker does not populate the device with the correct mount point - I've tried everything to fix it and am getting nowhere... looks like I might uninstall and try to build from source...

---

### Post by nerval on 2006-10-14
my problem is a little bit different, it happened three times in a row; so i guess it's not a coincidence.

i wanna burn an mp3 cd; while burning it; it freezes the system. nothing works and i have to reset the computer.

any solution to that ?

---

