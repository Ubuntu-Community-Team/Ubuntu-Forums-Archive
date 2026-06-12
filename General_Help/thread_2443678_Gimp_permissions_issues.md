---
title: "Gimp permissions issues"
date: 2020-05-18
forum: General Help
---

### Post by JamButty on 2020-05-18
Just started working with a new external HDD, copying archived files onto it from CDs,DVDs. With image files on the new HDD (jpg,png,tif) I can view and edit via default image viewer or Shotwell, but not with GIMP, which gives me "permission denied" errors. I can use GIMP on files residing on my internal HD. This makes no sense to me, given that other programs access the same files without a problem.
The partition owner is ROOT, but ADM (me) has create and delete permissions.
Any suggestions?
thanks.

---

### Post by monkeybrain20122 on 2020-05-18
Did you install gimp from the software store? It is a snap package and snap is known to have problems accessing external drives because of sandboxing.


So uninstall the snap version from the software store first and install the .deb from synaptic or apt install 

```
sudo apt install gimp
```

(you should install synaptic if you haven't already, it is a easy to use gui to manage packages in the normal software channels not like the software store) 

If you are using Ubuntu 20.04 the gimp version in the repository should be the latest, otherwise there is a [ppa]("https://launchpad.net/~otto-kesselgulasch/+archive/ubuntu/gimp").

---

### Post by JamButty on 2020-05-18
Gimp seems to be working now. Thanks!
Possibly the same issue? DejaDup, installed as part of basic 20.04 package, is also not working. Initially I had the new partitions with a MBR partition table and did test backups with no problem. After changing partition table to GPT, DejaDup could write to backup partition but not restore from it.

---

### Post by Dennis N on 2020-05-18
Too late now, but in case another user finds this information useful:

You could have fixed the permissions on the snap (assuming that's what you had) by this command:
```
dmn@Tyana-vm:~$ snap connect gimp:removable-media
```
Then, it would read/write to removable media and also any internal disk mounted at /mnt.

The snap version will automatically update to the latest version over the 5 year lifetime of Ubuntu 20.04. No PPA required to get the latest version.

---

### Post by JamButty on 2020-05-18
I will separate the Deja-dup issue to another post.

---

### Post by TheFu on 2020-05-18
> 
Then, it would read/write to removable media and also any internal disk mounted at /mnt.

Mostly true with caveats.

  Snap packages must feature (removeable-media) option from the snap package team and lots of other places besides /mnt and /media don't work.  For example,  we use /stuff to put temporary media files that aren't ready yet.  Any snap with constraints can't access that storage.  Same for lots of other places ... perhaps /opt/ or /srv/?

---

### Post by Dennis N on 2020-05-19
> **TheFu said:**
> Mostly true with caveats.

  Snap packages must feature (removeable-media) option from the snap package team and lots of other places besides /mnt and /media don't work.  For example,  we use /stuff to put temporary media files that aren't ready yet.  Any snap with constraints can't access that storage.  Same for lots of other places ... perhaps /opt/ or /srv/?

As to user access, I believe you are limited to home folder, /media/<user-name> and /mnt by design. You can see the available plugs an installed snap has (both connected and unconnected) by running:
```
snap connections <application-name>
```
Gimp has the necessary plug (removable-media) - I checked it before posting.

---

