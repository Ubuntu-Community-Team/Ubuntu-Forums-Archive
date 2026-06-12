---
title: "External hard drive caddy - feisty"
date: 2007-05-05
forum: General Help
---

### Post by mykrob on 2007-05-05
Hey-
Using Kubuntu Fesity
I have a friend's hard drive i am trying to get data off of. I am using a Dynex hard drive caddy I purchased from Best Buy. The hard drive is a Samsung 120GB, formatted to NTFS. When I power up the caddy, I get the prompt on screen asking what I want to do with it.. I click open in new window, and nothing happens. I dont get the icon on the desktop showing the drive or anything...

I had to mount it manually through the console using

sudo mount /dev/scd1 /Storage/lorenzo

Then the disk showed on the desktop. However, i couldnot open the disk, it said I didnt have permission..

I opened a root file browser using

kdesu konqueror

then navigated to where i need to and copied the files to a local folder so I can burn his data to a dvd..

My question is, what's the problem with mounting this volume? I assume it is a permissions issue with NTFS. How can i get around this allowing a normal user to mount an ntfs volume through this drive caddy?

Thanks,
-myk

---

### Post by taurus on 2007-05-05
Try

```
sudo umount /dev/scd1
sudo mount -t ntfs /dev/scd1 /Storage/lorenzo -o nls=utf8,umask=0222
```
That would give you a read-only permission on the drive.

---

### Post by mykrob on 2007-05-05
cool. In the future, however, is there a way I can just make it automount an external drive when i plug it up, just like with a thumb drive? I assume this is only an issue with NTFS, correct?

Thanks,
-myk

---

