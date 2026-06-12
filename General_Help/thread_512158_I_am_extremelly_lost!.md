---
title: "I am extremelly lost!"
date: 2007-07-28
forum: General Help
---

### Post by Blade14228 on 2007-07-28
Hi...
I just started using Ubuntu today, and I downloaded the Server edition (7.04) and I need serious help.

My problems are:
1) I need to somehow get ndiswrapper (I can't get on my DWL-G520)
2) After, configure the network from the terminal (I don't have a GUI yet :( )
3) Get at least 1 GUI - KDE or GNOME, if possible - both, if not then KDE
4) Setting that up
5) I need the directories for Apache, MySQL, and PHP.

I am sorry if I seem to be asking to much.

Yes- I did a search here before posting, and all the results still seemed confusing.

Thank you for the time.

-Keith

---

### Post by dpar on 2007-07-28
The server edition doesn't come with a GUI, AFAIK.
You will have to download Gnome or KDE desktop.

Edit: I'm on a Winblows box right now, so I can't get you the install links:(

---

### Post by dpar on 2007-07-28
Check this one out.......> [http://ubuntuforums.org/showthread.php?t=512006&highlight=install+kde+desktop](http://ubuntuforums.org/showthread.php?t=512006&highlight=install+kde+desktop)

---

### Post by Ripfox on 2007-07-28
Do you need a server specifically? If not then you should download the desktop version and use it as a server? That would solve alot of gui problems...otherwise you could (sudo aptitude install gnome-desktop) or kde-desktop

---

### Post by Blade14228 on 2007-07-28
I would do the apt-get, but the problem is that every time I do that it says that it can't do it because of no internet. Is there any links for downloading it to a cd, and installing it from the cd via the terminal? I'm in a dual-boot with ubuntu and xp, so I could keep switching as needed...

Keith

---

### Post by Blade14228 on 2007-07-28
Ripfox,

I could use the desktop, as long as I can do the following:

Use localhost
It comes with Apache, MySQL, and PHP installed and configured
Obtain the ndiswrapper for the card...

That's the reason I steered away from it in the first place... I didn't think it would have it.
The reason I can't use windows is because it seems to have a problem with MySQL and PHP (Yes, I followed the order - Installing MySQL then PHP). But, I guess I could use it then if it meets the needs...

I'm trying to develop a PHP app for my site, and also just learning PHP, so...

Thanks again.
Keith

---

### Post by Stephen Howard on 2007-07-28
*1) I need to somehow get ndiswrapper (I can't get on my DWL-G520)*

I'm assuming you don't have any internet access while running Ubuntu.  If so, boot up whatever operating system works and download the [ndiswrapper]("http://launchpadlibrarian.net/7040724/ndiswrapper-common_1.38-1ubuntu1_all.deb") package from Launchpad.  Put it into a partition that Ubuntu can see, or put it on a memory stick, floppy etc.  Boot into ubuntu and install the package using:
```
sudo dpkg -i <DownloadedFile>
```

Alternatively, if you do have access to the web from inside ubuntu, just type:  ```
sudo apt-get install ndiswrapper-common
```


**2) After, configure the network from the terminal (I don't have a GUI yet  )**

You don't have a GUI because you downloaded the server version of Ubuntu - servers don't need a gui so the necessary packages aren't installed.  If you are new to Ubuntu / linux, I recommend that you download the full GUI version before proceeding any further - life will become a lot easier.

As to actually configuring your network, there are books written about it from the perspective of securing a server exposed to the internet.  In any event, maybe installing ndis will be enough, otherwise I recommend installing the GUI version.

**5) I need the directories for Apache, MySQL, and PHP.**

```
sudo apt-get install apache mysql php
```

---

### Post by Blade14228 on 2007-07-28
Okay, from the way it looks, I'll download the desktop version for now... and just try installing everything from apt-get. (After I get the internet configured!) So, for now I'll do that, but tomorrow, I might have another question relating to this topic, so I won't stop paying attention to it yet... But, thanks to everyone who responded, for their time and responses, and I am very pleased with the quick response time! So, until tomorrow (If I need further help, that is) thanks again! -Keith

---

### Post by dpar on 2007-07-28
Everything on the Server Edition, you can get onto the desktop version too. Just requires some downloads.:)

---

### Post by Blade14228 on 2007-07-29
Okay, so let's see here...

1) I got the Desktop 7.04 installed...
2) I installed the ndiswrapper by using the automatic install (The terminal wasn't working right...)
3) I entered my configuration for the network (WEP, Name)
4) And still nothing.

Is there an additional download? Am I missing something?

---

### Post by Stephen Howard on 2007-07-30
Hmm, not sure I can help, but please provide the output from the following commands:

```
lshw -C network
```

```
lsmod
```

```
iwconfig
```

```
dmesg
```

Also, have a go at installing the linux restricted modules as they include a potentially relevant driver:

```
sudo apt-get install linux-restricted-modules-generic
```

Sorry for the huge data request, but I'm fishing around...

---

