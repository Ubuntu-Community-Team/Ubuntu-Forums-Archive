---
title: "need to edit a file as root"
date: 2008-02-02
forum: General Help
---

### Post by raptor222 on 2008-02-02
Hi,in order to install my scanner I need to edit a file as root, and i'm not sure how i do this.
never mind what  i do i cant edit it, it just says that i dont have premmision to save the file.

---

### Post by Zack McCool on 2008-02-02
> **raptor222 said:**
> Hi,in order to install my scanner I need to edit a file as root, and i'm not sure how i do this.
never mind what  i do i cant edit it, it just says that i dont have premmision to save the file.

In a terminal window:

sudo nano filename

When requested, enter your user account's password.  It will NOT echo.

Edit your file, CTRL-X to exit, and it will be good to go.

---

### Post by cdaringe on 2008-02-02
perhaps a more friendly text editor is gedit.

what i would recommend doing is browsing to the folder that the file is in.

then, open up a terminal window.  type 
```
cd /YOUR/DIRECTORY/WITH-THE-FILE/HERE
```
its easiest to copy and paste the directory location

then do a 
```
sudo gedit filename
```

either way will work. just kind of building on the last post.
when you are done, save and exit!
yahoo.

---

### Post by raptor222 on 2008-02-02
thank for all your replies, now works like a charm,:guitar:

---

### Post by oldos2er on 2008-02-02
Just FYI, when you're using a graphical application, you want to use 'gksudo.' So your command should be 'gksudo gedit /filename'

---

