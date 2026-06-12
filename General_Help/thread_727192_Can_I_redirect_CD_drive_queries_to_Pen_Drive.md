---
title: "Can I redirect CD drive queries to Pen Drive?"
date: 2008-03-17
forum: General Help
---

### Post by theonlygolux on 2008-03-17
Hi,

I am running Xubuntu 6.06 on an 850Hz Asus Notino A1300, which is old enough to have a CD drive which doesn't read CDRs or CDRWs.

I have managed to install Xubuntu  by dint of borrowing a newer laptop and swapping the harddrives, then rejigging settings with the help of these boards so that display etc works.

I am having problems with some of my apt gets (notably ndiswrapper, but others too), because the computer seems to wish to access my installation CD once it has apt-gotten the files, which obviously the computer can't read.

Is there any way I can redirect these queries to read from a USB drive? I have the .iso image on one.

I have searched the boards and do believe this query to be unique insofar as I can find no threads pertaining to my particalar problem, but I hope that you can help.

Thanks

---

### Post by DoctorMO on 2008-03-17
you should just disable the cdrom entry in your sources.list editing it like so:

```
gtksu gedit /etc/apt/sources.list
```

Comment out on of the first lines that mentions the cdrom (add # to the start of the line) and save and exit.

now run:

```
sudo apt-get update
```

to update your repository information and this should solve the problem.

To answer your question directly, in this case yes, if you wanted to access the iso as if it was a cdrom then you could mount the iso under /media/cdrom and forgo having to use a usb pen drive. although this is redundant so I won't show you have to do this, there are plenty of places showing how for the interested though.

---

### Post by theonlygolux on 2008-03-17
Thank you muchly - That has solved the problem.  Now I have new ones, but ones which I think I have seen the answer to elsewhere.

---

