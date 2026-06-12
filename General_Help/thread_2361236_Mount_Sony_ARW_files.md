---
title: "Mount Sony ARW files"
date: 2017-05-14
forum: General Help
---

### Post by zkab on 2017-05-14
I have a Sony camera with a bunch of ARW files on it sdcard.
When USB connect the camera then Thunar pops up with the sdcard folder name but when I click on that folder  it refuses to mount the files.
Do I need some libraries to mount the camera's sdcard in Thunar ?
I have xubuntu 17.04

---

### Post by zkab on 2017-05-16
Problem solved by a user in another forum.

[COLOR="#0000FF"]sudo apt-get install exfat-utils exfat-fuse[/COLOR]

---

