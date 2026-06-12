---
title: "Samba mount access issues"
date: 2017-01-08
forum: General Help
---

### Post by Bigfoot73 on 2017-01-08
I have a router that acts as a samba server and shares an ext3 usb disk, the router is running Tomato open software (linux based).
On my windows computers I can access the files without problems but on my Ubuntu machine I have some problems:
I can access the files by browsing the network in a file manager, in that case it mounts automatically in /run/user/1001/gvfs/smb-share:server=xxx,share=xxx and I can access the files. If I check the access right the owner of the files always appear to be me. However there are two problems:
1. I don't want to browse the network manually to mount after each boot.
2. Some programs (EasyTag) seems to have a problem when saving files, probably due to the "strange" path.

So I tried to mount the share in a better location by adding it in fstab. However the owner of the files is now reported as the original owner. (Which surprises me because I didn't expect samba to handle ext3 file ownership.) I can create a new file, but the ownership is automatically set to root and I am not able to access it. Probably because smb.conf on the server contains "force user = root".

What I would like to do is to mount the share so that ownership information is ignored and all users gets full read and write access. (Just like when it becomes mounted by browsing in a file manager but in a better location and permanently mounted!) How can I achieve this?

---

### Post by Morbius1 on 2017-01-08
Maybe something like this:

```
//server/share /media/USBStick cifs defaults,uid=1001,nounix 0 0
```

Or if you have multiple users on the same client:
```
//server/share /media/USBStick cifs defaults,dir_mode=0777,file_mode=0666,nounix 0 0
```
You would have to adjust and add whatever authentication mechanism you are currently using to access the share.

---

### Post by Bigfoot73 on 2017-01-08
Thanks, problem solved!

---

### Post by mörgæs on 2017-01-08
Good, please mark the thread so.

---

