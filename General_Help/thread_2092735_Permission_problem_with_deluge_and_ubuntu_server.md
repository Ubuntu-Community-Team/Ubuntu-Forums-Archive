---
title: "Permission problem with deluge and ubuntu server"
date: 2012-12-08
forum: General Help
---

### Post by MadsRC on 2012-12-08
I recently set up a Ubuntu 12.04 server and installed the Deluge Server following this guide: [http://www.havetheknowhow.com/Install-the-software/Install-Deluge-Headless.html](http://www.havetheknowhow.com/Install-the-software/Install-Deluge-Headless.html)

Then I fired up the deluge webgui and changed the download dir to /mnt/storage/deluge/incomplete and the complteded dir to /mnt/storage/deluge/complete.

/mnt/storage/ is a pool of 2 disks, using aufs.

Permissions for /mnt/storage/deluge folder is:
```
drwxrwsr-x   5 deluge deluge       128 Dec  8 21:40 deluge
```

I also setgid with:
```
sudo chmod -R g+s deluge/
```

Problem is, addind the ubuntu iso I get:
```
Permission denied: /mnt/storage/deluge/incomplete/ubuntu-12.04.1-desktop-i386.iso
```

Then I went to /mnt/storage/incomplete and did "ls -l" without any output. So basicly the file doesn't exist.

From my user, who is part of the deluge group, I can create files with touch and remove them again in /mnt/storage/deluge/ - So atleast members om the deluge group can do that.

The permissions for /mnt/storage/deluge/incomplete is:
```
drwxrwsr-x 2 deluge deluge  48 Dec  8 20:39 incomplete
```

Creating a file in there forces the group to be deluge, as per the setgid.

So why adding a torrent through the webinterface gives a permission error, I don't know?

The uploaded file should be created with the user of the deluge process (Which should be deluge) and the group of deluge as per the setgid.

Anyone got any idea?

EDIT: I had the SAME exact problem with transmission when I tried that earlier today...

---

### Post by MadsRC on 2012-12-09
Damnit, accidently marked thread as solved... Could a mod mark it as ubuntu?

---

