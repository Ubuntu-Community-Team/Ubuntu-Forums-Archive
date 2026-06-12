---
title: "disk space still &quot;missing&quot; after deleting /var/vm"
date: 2007-02-23
forum: General Help
---

### Post by wesglockzin on 2007-02-23
Ok.

I install vmware server, and everything works fine.  The only thing is after I delete a virtual machine the space that was allocated for the instance is still being used.  Meaning, I'm slowly running out of disk space every time I install and then delete a virtual machine.  I even deleted the the entire /var/vm directory...I but I didn't get any of the disk space back.

Ie: I use 8 gigs for w2k3 virtual machine.  I decide to delete the instance but the 8 gigs isn't given back.  I've done this about 3-4 times and now I'm "missing" 24-32gigs.

:confused:

---

### Post by llamakc on 2007-02-23
How are you 'deleting' it? Are you doing so on the command line or in Nautilus (or other gui app)?

---

### Post by vigleik on 2007-02-23
Install filelight, it will tell you what's taking up the space.

---

### Post by wesglockzin on 2007-02-23
gui, but was using Nautilus as root.

> **llamakc said:**
> How are you 'deleting' it? Are you doing so on the command line or in Nautilus (or other gui app)?

---

### Post by wesglockzin on 2007-02-23
I just installed it remotely...I will have to try it out after work when I can login via the gui.

> **vigleik said:**
> Install filelight, it will tell you what's taking up the space.

---

### Post by llamakc on 2007-02-23
If you have shell access you can use


cd / && sudo du -h --max-depth=1

(where you're looking from / ) and then descend into where you're concerns are and run the `sudo du -h --max-depth=1` command again. If you deleted these files from a GUI, be sure to empty the Trash too.

---

### Post by wesglockzin on 2007-02-23
> **llamakc said:**
> If you have shell access you can use


cd / && sudo du -h --max-depth=1

(where you're looking from / ) and then descend into where you're concerns are and run the `sudo du -h --max-depth=1` command again. If you deleted these files from a GUI, be sure to empty the Trash too.

Sweet, found it!

root@xxxxxx:/# cd /root && sudo du -h --max-depth=1
4.0K    ./.aptitude
340K    ./.gconf
12K     ./.gconfd
96K     ./.gnome2
4.0K    ./.gnome2_private
212K    ./.synaptic
32K     ./.nautilus
292K    ./Desktop
12K     ./.gnome
4.0K    ./.kde
32K     ./.xine
1.1M    ./.thumbnails
**22G     ./.Trash**
244K    ./share
4.0K    ./.qt
20K     ./smb4k
4.0K    ./.xcdroast
16K     ./.mcop
8.0K    ./.ssh
12K     ./.metacity
452K    ./.gstreamer-0.10
12K     ./.vmware
4.0K    ./vmware
22G     .


So, do I just "rm .Trash" ?

---

### Post by llamakc on 2007-02-23
cd into .Trash and make sure you want to delete everything. Then rm it.

---

### Post by wesglockzin on 2007-02-23
> **llamakc said:**
> cd into .Trash and make sure you want to delete everything. Then rm it.

Man, thanks for the quick help on this.  I'll be adding this command to my little black book of unix/linux commands.


:guitar:

---

