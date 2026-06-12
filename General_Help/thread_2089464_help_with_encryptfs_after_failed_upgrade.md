---
title: "help with encryptfs after failed upgrade"
date: 2012-11-29
forum: General Help
---

### Post by elj4176 on 2012-11-29
A friend tried to update/upgrade his 11.04 install and something went sideways. Can't boot and can't get a login prompt @ a tty.
So he is asking if I can recover his files from the drive. 

I have put the drive into my machine and can see both of his home folders and the .encryptfs folder with the encrypted contents of both home folders.

I have the passwords for both users but am unable to figure out how to access their encrypted data so I can do a clean install. 

I must be missing something simple here. Any help?

edit - when I run:
gksu nautilus

and click on 'access my private data' I get a quick terminal window that pops up and goes away immediately.

---

### Post by elj4176 on 2012-11-29
[http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/](http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/)

This link helped me get what I needed. My problem was that I couldn't get to a live linux session. I finally made a bootable usb and that allowed me to mount the encrypted folders and copy what I needed.

---

