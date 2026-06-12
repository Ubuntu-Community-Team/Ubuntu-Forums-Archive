---
title: "Problems mounting NTFS drive."
date: 2007-04-04
forum: General Help
---

### Post by Kwilco on 2007-04-04
I am desparately trying to backup a dying (but still functional) windows hard drive onto another computer. My only option is to hook up the hard drive as a slave into my ubuntu tower and transfer the data through Ethernet.

However, I have not been able to access the harddrive. I read a tutorial, and used the following commands to mount:

sudo mkdir /media/secondhdd
sudo chmod 777 /media/secondhdd
sudo mount -t ntfs /dev/hdb1 /media/secondhdd

This all works fine, no error messages. Then, when I try to access /media/secondhdd, I get an error 'Permission Denied' (in the Terminal) and 'You do not have the permissions necessary to view the contents of "secondhdd"'. Am I doing something wrong? Any help would be **much** appreciated.

By the way, I have also tried mounting with the -r flag, and chmodding to 444, but it still doesn't work.

---

### Post by yabbadabbadont on 2007-04-04
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

That is a pretty decent guide for doing what you need.  It is written by one of the moderators.

---

### Post by Kwilco on 2007-04-04
A million thanks for the link, it worked perfectly! :-D

---

