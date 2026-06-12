---
title: "is there a virtual cdrom program for linux?"
date: 2005-04-29
forum: General Help
---

### Post by Yeeha on 2005-04-29
I mean program what can be used to look into cd images.

---

### Post by jcs296 on 2005-04-29
You can mount the .iso image as a loopback device, so that it's as if you had burned it and then mounted the cd normally. To do so use:

mount -o loop -t iso9660 [ -r ] filename.iso /mnt/iso

where 'filename.iso' is obviously the image file, and '/mnt/iso' is the directory where you'd like to mount the file.

the '-r' is optional and means to mount the file read only. hope this is what you meant,

Joe

---

### Post by Yeeha on 2005-04-30
Thx for help! It works but if anyone knows program for mounting images i would like to know because i would like to do it with couple clicks  :wink: .

---

### Post by jcs296 on 2005-05-01
You can turn any script (bash, perl, etc) into a nautilus script. That means you can right click on the file and one of the options will be to execute the script on that file. I can't see any difference between a special program to mount iso images and just using the regular file manager (nautilus). So to make a script that allows you to mount the iso from within nautilus by right clicking on the file:

put the following script in a file called "Mount_ISO_image" in ~/.gnome2/nautilus-scripts/, and make it executable ('chmod u+x Mount_ISO_image')

#!/bin/bash
mount -o loop -t iso9660 $1 /mnt/iso

The above two lines are the script; the '$1' is the name of the .iso file. Making this executable and put it in ~/.gnome2/nautilus-scripts/ means that you can right click on any .iso file and mount it (see [http://g-scripts.sourceforge.net/faq.php](http://g-scripts.sourceforge.net/faq.php) for more details on making nautilus scripts). The downside is that the script will appear for non iso files as well. Alternatively, you can use the archive manager to open and look through .iso files and extract specific files.

---

### Post by Yeeha on 2005-05-02
Wow using scripts like that in gnome makes gnome real good :) . Thanks for info. Now i will go and make many scripts that can make my life more convinient :grin: .

---

### Post by madjr on 2008-03-29
try **gmount-iso** (in the repos)

or acetoneiso

[http://www.acetoneiso.netsons.org/viewpage.php?page_id=2](http://www.acetoneiso.netsons.org/viewpage.php?page_id=2)

---

