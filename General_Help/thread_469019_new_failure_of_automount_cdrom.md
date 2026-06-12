---
title: "new failure of automount cdrom"
date: 2007-06-09
forum: General Help
---

### Post by whb on 2007-06-09
I am using feisty32 on an amd64 system. Sometime in the last week or so a dvd in the drive now will not automount as before but gives me an error message saying that the fs type is not recognised. I have to open a console and sudo mount it. There have been no changes to my fstab as far as I can see. It must be a permission issue, but who changed it., I am the only operator, so I presume some update changed something. Sorry if this has been seen before and commented on but I can not find an appropriate answer anywhere on the forum. Thank in advance,

Hunter

---

### Post by polt on 2007-06-10
What does your fstab file look like?

---

### Post by whb on 2007-06-10
My fstab looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=5e568286-434b-49d8-adb4-c24c40734459 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=bf3c52a4-d3b8-4282-8b3c-21d07458686d /home           ext3    defaults        0       2
# /dev/sda3
UUID=b8db52e3-922c-40ea-b33d-29650d7a350d none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660, user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

I do not have a floppy drive so could kill the last line. I have not fiddled with it, so I still believe an update changed something.

Thank you for answering. This problem should be within my power to solve, but my brain seems to have gone walkabout. Help is appreciated,

Hunter

---

### Post by jimbob on 2007-06-10
Don't know if it makes any difference but you have an extra comma after iso9660 that I don't have:

   /dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by whb on 2007-06-10
Yeah, I checked my laptop and there is no comma. I shall remove it and see what happens,

Hunter

---

### Post by whb on 2007-06-10
Yes. Removal of the comma seems to have fixed it. Thanks,

Hunter

---

### Post by roddersg on 2007-10-03
I have the same problem and have posted a query somewhere in this forum too.
The solution presented does not solve the problem, I think Feisty does not know what to do with the different disc types. 

/etc/fstab
/dev/hdd  /media/cdrom0  [COLOR="Red"]udf,iso9660[/COLOR]  .....

I can find no mention in the man on putting more than one option in the mount type.  My DVD reader will always default to iso9660 and I still have to manually mount the UDF discs.

This is not so much a problem but rather an irritation.  Does anyone have a solution?

---

### Post by roddersg on 2007-10-04
There is a problem with the /etc/fstab.  The original version is (as above)

/dev/scd0  /media/cdrom0  [COLOR="Red"]udf,iso9600[/COLOR] user,noauto,exec 0 0

The problem is that fstab cannot make up its mind whether to load udf or iso9600 and there is no mention in man fstab on multiple formats.  The correct solution is to use the word [COLOR="Red"]auto[/COLOR] as below

/dev/scd0  /media/cdrom0  [COLOR="Red"]auto[/COLOR] user,noauto,exec 0 0

and it works.
Thanks to those kind people at [http://amazingrando.wordpress.com/2007/05/02/how-to-mount-udf-dvds-in-ubuntu](http://amazingrando.wordpress.com/2007/05/02/how-to-mount-udf-dvds-in-ubuntu)

Now Feisty automounts my DVDs (whether udf or iso9600) correctly each time.

---

