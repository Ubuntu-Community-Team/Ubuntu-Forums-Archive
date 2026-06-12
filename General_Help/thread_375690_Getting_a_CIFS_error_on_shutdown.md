---
title: "Getting a CIFS error on shutdown"
date: 2007-03-04
forum: General Help
---

### Post by tenjin1 on 2007-03-04
I have just recently started getting this error when I shutdown mt ubuntu edgy box. This error comes up whever I shutdown, it's after the splash screen has ended the moment right before shutdown. 
The error looks like this:
> CIFS VFS: NO RESPONSE FOR CMD 50 MID 1788

It's not really much of a problem except for having to wait a little bit before my machine finally shutdown whenever I restart. The only thing I use CIFS for is a network share I added in fstab using this [thread]("http://ubuntuforums.org/showthread.php?t=288534&highlight=cifs+vfs"). I have googled the error and didn't come back with anything. Here on the forums didn't see anything either.

Any help on this would be greatly appreciated!!!

---

### Post by tenjin1 on 2007-03-06
I guess this is an error basically saying that it can't unmount the volume. Maybe because it's a network share instead of usb or partition? Samba seems like it didn't have much problmes unmounting volumes on shutdown.

---

### Post by bonustracks on 2007-03-23
I'm also encountering this error on Fiesty.

---

### Post by theraapster on 2007-03-28
Did either of you find out what was wrong?  I am currently using edgy and I just set up CIFS network share also.

---

### Post by theraapster on 2007-03-28
Guess I should have kept looking before posting in here, but for anybody else who need the solution: [Here it is]("http://ubuntuforums.org/showthread.php?t=293513&highlight=CIFS+VFS%3A")

---

### Post by tenjin1 on 2007-03-31
> **theraapster said:**
> Guess I should have kept looking before posting in here, but for anybody else who need the solution: [Here it is]("http://ubuntuforums.org/showthread.php?t=293513&highlight=CIFS+VFS%3A")

Cool, Thx!
...worked for me!

---

