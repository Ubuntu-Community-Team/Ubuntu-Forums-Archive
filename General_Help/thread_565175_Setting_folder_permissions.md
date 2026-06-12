---
title: "Setting folder permissions"
date: 2007-10-01
forum: General Help
---

### Post by zaphod777 on 2007-10-01
I am using Virtualbox but after every reboot I have to reset permissions to a perticulure folder to get it to work.

sudo chmod -R 777 /dev/vboxdrv

how can I make this stick after a reboot?

---

### Post by bodhi.zazen on 2007-10-02
I think the preferred method is to add your user to the vboxusers group ;)

---

### Post by zaphod777 on 2007-10-02
what is the proper syntax for adding my user to the group.

---

### Post by bodhi.zazen on 2007-10-02
Either from the gui (manage groups and users) or the command line:

```
usermod -G vboxusers -a <user>
```

---

### Post by scruff on 2007-10-02
That's correct. /dev is a pseudo-filesystem. It is generated at boot time and lives in RAM rather than disk.

When kernel-2.6 was release, the default DevFS was changed to udev which is supposed to be more efficient.

Check out these links for more info: 

[http://en.wikipedia.org/wiki/Udev]("http://en.wikipedia.org/wiki/Udev")

[http://www.atnf.csiro.au/people/rgooch/linux/docs/devfs.html]("http://www.atnf.csiro.au/people/rgooch/linux/docs/devfs.html")

---

### Post by zaphod777 on 2007-10-02
thanks guys I will give it a shot tonight. Thanks for the help it was starting to drive me mad.

---

### Post by zaphod777 on 2007-10-03
no go I am still getting the error at bootup 


The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

---

### Post by bodhi.zazen on 2007-10-03
did you :

1. sudo usermod -G vboxusers -a <user>

(sorry, forgot the sudo)

2. Log out and back in (this always seems required for the changes to take effect)

---

### Post by zaphod777 on 2007-10-04
i diddn't specificly run that command but through the GUI I could see my username in that group.

---

### Post by notwen on 2007-10-04
Had this similar error before too, try using the CLI command and restart.  Sometimes permissions applied through Nautilus just won't stick.  =]

---

### Post by zaphod777 on 2007-10-05
cool beans it works!

---

