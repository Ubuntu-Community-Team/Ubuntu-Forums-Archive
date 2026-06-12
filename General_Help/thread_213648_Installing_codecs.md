---
title: "Installing codecs?"
date: 2006-07-11
forum: General Help
---

### Post by Bino on 2006-07-11
I just installed ubuntu and when playing movies or dvd´s I got a message the right codec wasn´t found.

I browsed around on "restricted formats" and other pages and found I needed to install some packages.

I´m a bit lost now. How do I install those packages because when running "sudo apt-get install gstreamer0.10-ffmpeg" and such I got a message "couldn´t find package".

---

### Post by ciscosurfer on 2006-07-11
Your repositories need to include universe and/or multiverse.

Check [here]("https://launchpad.net/distros/ubuntu/+ticket/983") for further information.

---

### Post by Bino on 2006-07-11
Will this also work when the pc isn´t connected to the internet?

---

### Post by ciscosurfer on 2006-07-11
You can do many things with Apt (apt-get, aptitude, synaptic, adept, take your pick...)

The thing to keep in mind here is that when you want to download a package, you need to be connected to the Web.  So, for instance, let's say your at the command line and you type:```
sudo aptitude install gs  <---then hit the Tab key twice
```you'll notice a list of other programs that match the beginning string that you input: all programs that begin with 'gs'.  The reason you can see all of these is because they are listed in a sort of package manifest that gets downloaded each time you issue a```
sudo aptitude update
```keep in mind you need to be connected to issue **update**, **dist-update**.  It's always good practice, again while connected to the Web, to issue:```
sudo aptitude update   <---followed by
sudo aptitude dist-upgrade
``` The bottom line: you need to be connected when you want to install.  But you can view an entire list of packages when you are offline provided you issued an **update **command or **reload** within Synaptic when you were connected. ;)

---

### Post by Bino on 2006-07-12
So basiclly I´m screwed because I don´t have an internet connection :-? 

Is there perhaps another way to install updates by downloading it to an usb device or a cd and then run it in the console? And if possible, how would I do that?

---

### Post by 3rdalbum on 2006-07-12
> **Bino said:**
> So basiclly I´m screwed because I don´t have an internet connection :-? 

Is there perhaps another way to install updates by downloading it to an usb device or a cd and then run it in the console? And if possible, how would I do that?

[http://packages.ubuntu.com](http://packages.ubuntu.com)

Search for the packages you need, download them to your USB drive or whatever, copy them onto your Ubuntu computer. You can double-click them to install, as long as you're running Dapper. If it complains about dependancies, find those on the site I linked to (they are listed on each package's page) and install them.

Ubuntu really is meant to be used with an internet connection, unfortunately.

---

