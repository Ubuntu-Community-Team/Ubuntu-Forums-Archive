---
title: "I just screwed up my user permissions"
date: 2007-08-13
forum: General Help
---

### Post by climbjm on 2007-08-13
I don't know how, but I just screwed up my main users permissions.

Now I cannot run my FTP server, I cannot access the "System > Administration > user groups" and when I try and sudo anything, it says "user is not in the sudoers file."

Anybody?  Help?

I think it was this line and screwed me up... "sudo usermod -G ftpgroup user"

---

### Post by McNils on 2007-08-13
Yes, I can confirm your suspicions...

However, it is quite simple to correct. 

Restart the computer in recovery mode. Add your self to the **admin** group by using.

```

usermod -a -G admin user

```

Where user is exchanged for yor loginname. You should also add your self to thease groups:

dialout
cdrom
floppy
audio
dip
video
plugdev
scanner
lpadmin

And your own group (same as your login)

---

### Post by climbjm on 2007-08-13
Holy Crap that worked!

Thanks a ton!

- Phew!!!!

---

