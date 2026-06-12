---
title: "Can't Empty Deleted Folder"
date: 2008-02-23
forum: General Help
---

### Post by helliewm on 2008-02-23
I cannot empty my trash/deleted folder. See attached Screenshot I keep getting strange message saying I do not Permission?

Anyone any ideas?

Helen

---

### Post by taurus on 2008-02-23
Looks like you are not the owner of that directory.  Try 

```
gksudo nautilus
```

---

### Post by helliewm on 2008-02-23
gksudo nautilus produces this:

Now what do I do??

Helen

---

### Post by imtheguru on 2008-02-23
> **helliewm said:**
> gksudo nautilus produces this:

Now what do I do??

Helen

Navigate to the dir which wasn't being deleted and try again. Close the window after the delete operation is complete.

---

### Post by helliewm on 2008-02-23
When I navigate to the Deleted Folder after doing gksudo nautilus there is nothing in it? Where have all my items gone? Yet if I click on Trash on the Desktop its full of items as per previous screenshots.

There is only user on this PC me.

See attached screenshot of gksudo nautilus deleted folder:

Helen

---

### Post by imtheguru on 2008-02-23
> **helliewm said:**
> When I navigate to the Deleted Folder after doing gksudo nautilus there is nothing in it? Where have all my items gone? Yet if I click on Trash on the Desktop its full of items as per previous screenshots.

There is only user on this PC me.

See attached screenshot of gksudo nautilus deleted folder:

HelenThe path in your original screenshot is something like /home/helen/.Trash-helen/something.

This is where the problem item is located. The Deleted items you've posted belongs to root... due to gksudo.

Cheers.

---

### Post by imtheguru on 2008-02-23
> **helliewm said:**
> There is only user on this PC me.You are the only human at the computer but the operating system has several internal users, one of which is the super user called **root.**

**gksudo** is a graphical way to run **sudo** which is a command to execute commands as root... super user do.

Cheers.

---

### Post by helliewm on 2008-02-23
That was extremely weird. I could not locate the directory. Searched for it. But tried emptying Trash again and it let me. Really weird its been several days that I have been unable to empty it.

It solved itself.

Helen

---

### Post by Andeh on 2008-03-15
I had this same problem, i had a quick look around after doing a 

```
gksudo nautilus
```

i ended up navigating to '/home/<user name>/.trash/' and deleted them from there. i had to enable hidden files in order to see the /.trash/ folder though.

just thought that if it happened again to anyone this might be of some use

andeh

---

### Post by bilal.17 on 2008-03-15
i had a smillar problem once and all i had to do was navigate to the trash og my user using root

---

