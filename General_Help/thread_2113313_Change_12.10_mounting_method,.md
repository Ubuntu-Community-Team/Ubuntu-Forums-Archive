---
title: "Change 12.10 mounting method,"
date: 2013-02-07
forum: General Help
---

### Post by CaptainMark on 2013-02-07
The new way of auto-mounting usb drives since 12.10 isn't working out for me, if my passport gets mounted when I turn on my pc under /media/mark/passport it works fine for me but when I log out and my girlfriend logs in then deja-dup throws up a permission denied error, I've changed permissions for /media/mark/ to 777 which allows her file access via the browser and terminal but still deja dup doesn't work.

It worked fine in 12.04 as the passport was just mounted at /media/passport and if she's the first to log in when the pc is turned on then it works fine as the passport is mounted at /media/lorraine/passport

Is there any way to revert the mounting behaviour to that of 12.04 or another usable work around that will work for deja dup.

---

### Post by LewisTM on 2013-02-07
12.10 uses udisks2 instead of udisks for accessing and mounting USB drives. The method for automatically allocating a spot in /media is different and more user-centric. I doubt you can remove it.

What you could do is mount the disk by the old fashioned [fstab]("https://help.ubuntu.com/community/Fstab") method. Package **mountmanager** can help you with that. 

Here's an example of a good fstab entry, assuming the Passport is formatted with ext4 and using a bogus UUID.
```
UUID=ace75903-6725-4d87-b648-47fbb527b239 /media/passport ext4 defaults 0 1
```
The disk would be mounted at boot and would be accessible by all users, assuming the permissions allow.

Cheers!

---

### Post by CaptainMark on 2013-02-07
Thanks I'll use this method, it seems weird that is now default behaviour, it seems silly that if I plug in a usb and then someone else sits down at the computer , I see the security reasons but when Canonical wants Ubuntu to be approachable and easy for new users this sort of thing can really throw people off because there's no noob friendly message that tells you why you cant access or unmount a usb device that another family member plugged in, oh well, fixed anyway

Regards

---

### Post by LewisTM on 2013-02-07
Yes, the behavior is unintuitive. The peripherals should unmount when the user logs out. Although switching users without logging out might still create issues.
It's very well described (and debated) in this bug report
[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/1084188](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/1084188)
Please add yourself to the number of people affected by clicking the link at the top.

There might be a workaround using bindfs. This filesystem can generate a "view" of an entire directory tree with modified permissions. In your case, you would want the /media directory to be "owned" by each user when they access it in the bindfs view.

1) Install bindfs 
```
sudo apt-get install bindfs
```
2) Make directory /disks which will contain this new view.
3) Add this entry to /etc/fstab
> bindfs#/media /disks fuse mirror=user1:user2:user3 0 0
Replace user1... by the users on your system
4) Execute ```
sudo mount /disks 
```or reboot

Now any user who accesses /disks will have full access to the contents of the USB devices. The downside is that peripherals in /disks will not appear in key places likes the file manager side pane or the desktop.

Hope this helps.

---

