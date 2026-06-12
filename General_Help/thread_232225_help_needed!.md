---
title: "help needed!"
date: 2006-08-08
forum: General Help
---

### Post by brobbo on 2006-08-08
hi i have followed the ndiswrapper method 1 on tehre website and found the 2 .sys files 
to tell the truth i just started using ubuntu linux yesterday and i am in the total deepend lol
i want to learn the code of linux and how to use it so here gos

could someone be extremly kind and give me an idea on how to use ndiswrapper becasue i have no idea how to install in on ubuntu and im havving problems

cheers guys brad

---

### Post by Jagot on 2006-08-08
What wireless card do you have?  Are you sure you need ndiswrapper?

The driver you require I think should be a .inf file.  This is the basic method of getting a driver working with ndiswrapper:

```
sudo ndiswrapper -i ~/Desktop/bcmwl5/bcmwl5.inf
```

The above code actually installs the drive.  My driver happened to be placed in a folder on my desktop - you'd need to change it to wherever you've put your driver.

```
sudo modprobe ndiswrapper
```

The above code starts the module.

```
sudo ndiswrapper -m
```

The above code makes sure that ndiswrapper starts each time you start your computer.

I have to add some additional code because Ubuntu has some drivers built in for my card (a Broadcom), but they don't work for me so I use ndiswrapper.

If you want to learn some stuff you can do with the terminal then have a look at this site:

[http://linuxcommand.org/](http://linuxcommand.org/)

---

