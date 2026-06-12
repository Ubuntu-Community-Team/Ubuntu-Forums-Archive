---
title: "can't access webdav with samba"
date: 2015-03-05
forum: General Help
---

### Post by sporksrule on 2015-03-05
[COLOR=#333333][FONT=UbuntuRegular]I'm running Ubuntu 14.04. I have a raspberry pi with a webdav drive mounted (s3) and I would like to access it from my main machine with NFS. When I mount the parent folder where the webdav is located, I can read/write to other folders with NFS but the webdav drive is locked. Out of desperation I even mounted the webdav drive with 777 permissions- still not working. Any advice?[/FONT]

[FONT=UbuntuRegular]EDIT: title says samba instead of NFS. Made a mistake and can't change it. My question is regarding NFS though. Thanks. [/FONT][/COLOR]

---

### Post by TheFu on 2015-03-06
Don't use webdav. 
[http://www.maketecheasier.com/mount-amazon-s3-in-ubuntu/](http://www.maketecheasier.com/mount-amazon-s3-in-ubuntu/) has a fuse file system, riofs, to mount S3 storage.

---

