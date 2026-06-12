---
title: "Home folder empty and &quot;Could not update ICEauthority file /home/user/.ICEauthority&quot;"
date: 2014-08-30
forum: General Help
---

### Post by mateolegba on 2014-08-30
Hi, I'm an Ubuntu 12.04 user. After doing nothing special, I couldn't access to my user session. Booting with a Debian live-usb I realized that my home folder in the system partition is empty. I have the content of my user folder in another partition. Do I have any chances of get my system back? Ah, the message on the starting screen is "Could not update ICEauthority file /home/user/.ICEauthority". What do I have to do????. Thanks Thanks Thanks!!!

---

### Post by Bashing-om on 2014-08-30
mateolegba; Humm ??

A broken symbolic  link that should point to the home directory ???
Show us what we are working with. Post back - between code tags - the outputs of terminal commands:
```

sudo fdisk -lu
sudo parted -l
cat /etc/fstab
sudo blkid

``` Which will give a overview of your system, and perhaps some hints as to what is not goping on.

[INDENT][INDENT][INDENT]where there are solutions
[INDENT][INDENT][INDENT]there are no problems
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

