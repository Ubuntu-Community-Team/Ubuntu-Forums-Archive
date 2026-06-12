---
title: "how to re-install after deleting an image"
date: 2017-12-04
forum: General Help
---

### Post by stephenbbb on 2017-12-04
I was using Synaptic to cleanup and free some space and now it takes me to a black screen. Done this several times before and never had a problem. I always leave the 3 highest numbered images showing as installed.
This time it seems the active image was not the highest number. So there are higher images, but somehow grub is not offering them and it tries to load an image that was deleted.

any ideas how to fix??

---

### Post by gordintoronto on 2017-12-04
Boot repair.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by ian-weisser on 2017-12-04
Use the grub menu to choose a different kernel.

---

### Post by stephenbbb on 2018-01-06
I did everything and said that repair is done. when I reboot it arrives at the same black screen and does not start the gui. the linux shell is there. is there a way to start the gui manually from there?
all the info is in

[http://paste.ubuntu.com/26332221/](http://paste.ubuntu.com/26332221/)

---

### Post by stephenbbb on 2018-01-06
it may not be a boot issue. I ran several recovery modes aand all take me to the same spot:

i/o error, dev sda sector xxxxx
------
/dev/sda5 unexpected inconsistency; run fsck manually
failure file system check of the root filesystem failed

so what do I do with fsck??

---

### Post by stephenbbb on 2018-01-06
Fixed.

I googled and found this
[https://askubuntu.com/questions/697190/fsck-error-on-boot-dev-sda6-unexpected-inconsistency-run-fsck-manually](https://askubuntu.com/questions/697190/fsck-error-on-boot-dev-sda6-unexpected-inconsistency-run-fsck-manually)

just ran fsck /dev/sda5 and VOILA it works.

---

