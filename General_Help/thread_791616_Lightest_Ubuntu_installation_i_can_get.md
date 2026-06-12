---
title: "Lightest Ubuntu installation i can get?"
date: 2008-05-12
forum: General Help
---

### Post by orasetaina on 2008-05-12
Ok here is what i want!

Lightest ubuntu installtion possible. 
Be able to install vlc
should be able have myth/pref Elisa
should have open office
a torrent client
mencoder 
winff

any ideas?

---

### Post by joselin on 2008-05-12
> **orasetaina said:**
> Ok here is what i want!

Lightest ubuntu installtion possible. 
Be able to install vlc
should be able have myth/pref Elisa
should have open office
a torrent client
mencoder 
winff

any ideas?

The lighest version is an alternate cd of xubuntu. Then you must install vlc, open office or whatever you want.

Regards

---

### Post by orasetaina on 2008-05-12
can i downgrade my hardy installation that i have now? or a fresh install?

How can i keep my bookmarks in firefox?
How can i keep a list of the programs i have now so i can install later...mencoder, elisa/myth, winff being top of that list?

sorry too many questions i know!!!

---

### Post by joselin on 2008-05-12
> **orasetaina said:**
> can i downgrade my hardy installation that i have now? or a fresh install?

Better a fresh install.

>  How can i keep my bookmarks in firefox?

Keeping your home partition when you install it.

> How can i keep a list of the programs i have now so i can install later...mencoder, elisa/myth, winff being top of that list?

```
$ dpkg --get-selections | grep -v deinstall > ubuntu-files
```

To recover:
```
$ sudo apt-get update
$ sudo apt-get dist-upgrade
$ dpkg --set-selections < ubuntu-files
$ sudo dselect
```

>  sorry too many questions i know!!!

No problem.

---

### Post by orasetaina on 2008-05-12
i dont actually phsically want to keep the packages/progs...just a list of them...i will install them later!

compiz work with xubuntu?

in terms of performance does xubuntu make a diff?
for example encoding a vid in xubuntu as compared to encoding in ubuntu...would there be any difference? quality of file? speed? cpu workload? etc

thanks for yur help btw :)

---

### Post by joselin on 2008-05-12
> **orasetaina said:**
> i dont actually phsically want to keep the packages/progs...just a list of them...i will install them later!

Yes, that the idea.

>  compiz work with xubuntu?

Sure.

>  in terms of performance does xubuntu make a diff?

Yes, don't know how much, but yes.

>  for example encoding a vid in xubuntu as compared to encoding in ubuntu...would there be any difference? quality of file? speed? cpu workload? etc

There won't be any difference in a encoded video. About the speed, cpu load, etc.  think that xubuntu uses less memory that ubuntu, that's the only difference, so perhaps you could wait for less time, but the difference will be really really small.

Regards

---

### Post by FakeOutdoorsman on 2008-05-12
You can do better than Xubuntu in terms of a lightweight Ubuntu with a number of different Windows Managers (WM).  My personal favorite is Openbox, but others may prefer Fluxbox, IceWM, etc.  You can also create a custom Gnome which will be much more lightweight than the standard Gnome.  I recommend getting the "alternate" installation disc or the [mini.iso]("https://help.ubuntu.com/community/Installation/MinimalCD").  With these you can choose to perform a command-line only installation.  Once the command-line system is installed you can build up from there, installing only what you want or need.  It will seem more complicated than a standard install, but you will learn more about your final installation and the system will be much more responsive.

Example for lightweight Gnome once the command-line is installed:
```
sudo aptitude update
sudo aptitude install xserver-xorg gdm gnome-core gnome-media gnome-system-monitor gnome-system-tools gnome-volume-manager gnome-utils gnome-app-install synaptic firefox deluge-torrent openoffice vlc mencoder
```

More info:
[Lightweight Gnome]("http://ubuntuforums.org/showthread.php?t=298835")
[Ubuntu Installation on Low Memory Systems]("https://wiki.ubuntu.com/Installation/LowMemorySystems")
[Urukrama's Openbox Guide]("http://urukrama.wordpress.com/openbox-guide/")

> **orasetaina said:**
> i dont actually phsically want to keep the packages/progs...just a list of them...i will install them later!
joselin's suggestion above gives you a file called "ubuntu-files".  Open it to see a list of your installed packages.

---

### Post by orasetaina on 2008-05-13
im not really comfortable with the command line so far!!

Im not really that confident with it. I want something that will use mencoder to encode....but not be a strain on my pc!!!

---

### Post by ryanhaigh on 2008-05-13
When you are encoding it is the encoding process that is making the PC work, not the desktop environment. Even if you installed a commandline system and used a commandline application to do the encoding it would still likely stress the system. That said you can lower the priority of the process which will allow other processes access to the systems resources before the re-prioritised process. You can do this using the commandline application renice (search help and support under the system menu) or by using the gnome-system-monitor.

For the gnome-system-monitor method, open system>admin>system monitor and select the processes tab, find the process that is using all your cpu, right click on the process and select change priority, use the slider to change the priority as desired and click change priority. Note that if you change a processes priority downward (1 to 0 for example) thereby increasing the priority of the process the system will ask for your admin password. 

As you would expect reducing the priority of the process will make the encode slower, but should make other applications more responsive while it is running.

EDIT: just to clarify I am not sure what the effect on the overall system load will be as a result of renicing the encoding process, as mentioned in the documentation "the affected processes will run only when nothing else in the system wants to", so if nothing else wants to use the cpu for that cycle the encoding process will still be able to. If you are genuinely worried about over stressing your system, ensure that your vents/fans are clean and running properly and you should be ok, there is not much point having a fast pc if you aren't going to use that power. If your problem is the responsiveness of the system during an encoding operation, renicing should help.

---

### Post by orasetaina on 2008-05-13
does lowering the priorty actually work though?

---

### Post by nlvivar on 2008-10-08
I hope that you found acceptable answers for yourself. I have an old Dell laptop that I use a barebones Ubuntu system on. So I have found a few places to look.

If you have not found a good solution, here is a good resource:
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

Also, here are a few Ubuntu remixes that may suit your needs:
[http://www.xubuntu.org/](http://www.xubuntu.org/)
[http://fluxbuntu.org/](http://fluxbuntu.org/)
[http://ubuntulite.tuxfamily.org/](http://ubuntulite.tuxfamily.org/)

---

### Post by mikjp on 2008-10-10
> **orasetaina said:**
> How can i keep my bookmarks in firefox?

If you have a separate partition for /home, that should be no problem at all. I suppose you know you should have a separate partition at least for / and /home?!

---

