---
title: "Virtual Box and USB"
date: 2013-02-11
forum: General Help
---

### Post by saskatchewan on 2013-02-11
I am running Ubuntu 12.04 on an ASUS U31S.


I am trying to get Virtual Box to recognize my usb ports but I am having challenges.

Here is the site that I have been trying.

[http://news.softpedia.com/news/How-to-Fix-VirtualBox-USB-Support-111715.shtml](http://news.softpedia.com/news/How-to-Fix-VirtualBox-USB-Support-111715.shtml)

The site is for an older form of linux and I am having problems finding System -> Administration -> Users and Groups
to unlock usergroups.

The goal is to get Xperia PC Companion Software running so I can update my phone.

This is the orignial site that was working with.

Xperia PC Companion Software / VirtualBox USB Recognition

---

### Post by dino99 on 2013-02-11
you might pay attention to the date of that "howto"  ):P

if you are using virtualbox , and follow the settings doc, you'll not have such problem  :p

[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by ibjsb4 on 2013-02-11
To manage users and groups you need to install gnome-system-tools.

```
sudo apt-get install gnome-system-tools
```

You have installed your extension pack?  And its the right version?

[https://www.virtualbox.org/manual/ch01.html#intro-installing](https://www.virtualbox.org/manual/ch01.html#intro-installing)

---

### Post by saskatchewan on 2013-02-11
This is going to take some work.....

It will take a while but, thanks for the suggestions and please keep them coming.

---

### Post by saskatchewan on 2013-02-11
Okay, I have been trying and I get stuck when I get to Windows settings andI am told to select the USB+ button.  It says that there is nothing recognized despite me having two different USB devices plugged in.

Here are the instructions I am working from.

[https://help.ubuntu.com/community/VirtualBox/USB](https://help.ubuntu.com/community/VirtualBox/USB)

I took a screenshot if there is a way for me to attach it.

---

### Post by SeijiSensei on 2013-02-11
Did you install the [extension pack]("https://www.virtualbox.org/wiki/Downloads")?  Without it, the guest machine cannot access the host's USB ports.

---

### Post by saskatchewan on 2013-02-11
I installed the extension packs and still no luck.  Do I need to do a restart to get them to work?

The Windows I am running in the VM is updating and I do not want to close until it is finished.

---

### Post by saskatchewan on 2013-02-11
All the windows updates are done and I have restarted the VM.  Despite the extension packs. It still will not recognize any usb devices :-(

So.....  Any ideas.....

---

### Post by saskatchewan on 2013-02-12
Hey, I did a restart of the whole computer and it works!!


Thanks for all your help!!

---

