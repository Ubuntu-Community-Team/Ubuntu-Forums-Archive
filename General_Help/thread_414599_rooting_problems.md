---
title: "rooting problems"
date: 2007-04-20
forum: General Help
---

### Post by Amilius on 2007-04-20
Kubuntu user. I'm getting a problem every time I plug in my external USB hard drive or any USB device. It shows on my desktop but to access it I have to mount it manually on a terminal EVERY time. it didn't do this the last time I installed kubuntu, it started happening after I reisntalled kubuntu over the last install. It's kind of tiring and time-consuming to have to mount it manually everytime I plug in a device, is there a way to mount it permanently? 
 
 and another problem is that once I mount the device, I can't manage the files inside, I can't delete them, nor pass files to it. I went to it's Properties to allow permissions to modify it, but it won't let me, telling me that only root can do this, but I'm suppossed to be root and it's not working, how do I get full power over my stuff??
 
 please I would really appreciate help.
Edit/Delete Message:(

---

### Post by Famicommie on 2007-04-20
I don't have an answer to the first question, but I might be able to help with the second.

Ubuntu comes with root disabled by default. In the place of a root account, we use sudo. I dunno about KDE, but GNOME uses a tool called gksudo to run programs which require root privileges (such as Synaptic). [More info on sudo here](https://help.ubuntu.com/community/RootSudo).

To change the file permissions on your USB drive, open up a terminal and type
```
sudo chmod -R 777 /path/to/USBdrive
```
obviously replacing /path/to/USBdrive with the proper path.

---

