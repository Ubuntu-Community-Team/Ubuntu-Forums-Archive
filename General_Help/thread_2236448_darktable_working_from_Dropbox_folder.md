---
title: "darktable working from Dropbox folder?"
date: 2014-07-26
forum: General Help
---

### Post by jfca283 on 2014-07-26
Hi
I'm not sure if this doubt correspond to ubuntu, but, anyway.
I would like to set my darktable folder, from where i import the raw files from my camera, into Dropbox.
Something like Dropbox/darktable.
Anybody know how to do this?
Thanks for your time and effort.

---

### Post by tgalati4 on 2014-07-26
You want to mount your Dropbox to a local folder at startup.

Create a local folder and read the instructions from these posts: (read all three before you attempt.)

[http://askubuntu.com/questions/484526/ubuntu-14-04-using-dropbox-folder-located-in-sdcard](http://askubuntu.com/questions/484526/ubuntu-14-04-using-dropbox-folder-located-in-sdcard)

[http://askubuntu.com/questions/43027/loading-dropbox-on-start-up-when-my-dropbox-folder-is-on-separate-partition](http://askubuntu.com/questions/43027/loading-dropbox-on-start-up-when-my-dropbox-folder-is-on-separate-partition)

[http://askubuntu.com/questions/163823/how-can-i-mount-my-dropbox-folder-as-the-documents-folder-on-my-encrypted-home-f](http://askubuntu.com/questions/163823/how-can-i-mount-my-dropbox-folder-as-the-documents-folder-on-my-encrypted-home-f)

Set the local folder as the open location in DarkTable preferences and set Nautilus to open file type with DarkTable.

---

### Post by jfca283 on 2014-07-26
No. I didn't make myself clear.
I just want that darktable works over a Dropbox folder by default.
Now it works on HOME/Pictures/dartable.

---

### Post by vanadium on 2014-07-27
In your dropbox folder, create a symbolic link to your Pictures/darktable folder. Then, the files will be synchronized to dropbox.

---

