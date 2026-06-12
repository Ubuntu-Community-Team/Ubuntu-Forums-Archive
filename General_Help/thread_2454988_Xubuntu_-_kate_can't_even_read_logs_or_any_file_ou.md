---
title: "Xubuntu - kate can't even read logs or any file outside my own folders..?!"
date: 2020-12-10
forum: General Help
---

### Post by phuzzyday on 2020-12-10
[SIZE=2](NOW RESOLVED - But I am still picking brains!!)

I feel like I should have found this answer already!  I have seen other people with things that were similar..  But alas, I have to bug you'se guys!!

So, yes.  kate.  I love it. (her?). 
I wiped Ubuntu, installed Xubuntu.  Manually installed kate from Software app in GUI. Try to open /var/log/syslog...

"[COLOR=#000000]The file /var/log/syslog could not be loaded, as it was not possible to read from it.[/COLOR]
[COLOR=#000000]Check if you have read access to this file."

So, all the permissions you can change in the Software app checkbox are turned on.  I tried installing it via snap on command line, same diff.

I am still relatively new to Linux, but it's 98% my daily driver now.  (Plus windows in VB for Fusion 360.)  Anyway, thanks everyone in advance for your help!!

EDIT:  Ii have added some of the log file that looked relevant..  (Some identical repeating lines were deleted to fit the forum limit...)[/COLOR][/SIZE]

---

### Post by Impavidus on 2020-12-10
/var/log/syslog is supposed to readable for the syslog user and the adm group and the first user of the system should normally be in the adm group:```
$ ls -l /var/log/syslog
-rw-r----- 1 syslog **adm** 58640 dec 10 09:33 /var/log/syslog
$ groups
username **adm** cdrom sudo dip plugdev lpadmin lxd sambashare
```
I assume your problem is caused by snaps. You installed a snap version of kate instead of the regular deb version (the software tool makes it easy to mix them up) and snaps can only access files in your home directory and, maybe, /media. I suggest you try the deb version instead.

A freshly installed Xubuntu 20.04 system has no snaps. I don't want them, so I removed the ability to install them.

---

### Post by phuzzyday on 2020-12-10
Ding Ding Ding!!  You were right!! Thank you!!

I un-installed the snap one via command line, reinstalled the one that came up in 'software' and the snap remove command removed it again, and it showed gone in the software app.
I had to manually change the 'source' dropdown from whatever it was - to the ubuntu one.  Even the icon changed.
So nearly anyone who installs this popular app onto a freshly installed Xubuntu gets a crippled one.  This seems..  wrong..

Since you clearly know what you are talking about...  Please let me ask this..
I previously installed Ubuntu, and then Plasma, cause I hate the desktop manager, which was WAY better, but I had a couple confusing problems, and someone suggested you have less if you just install the Xubuntu distro, (which I thought was using plasma.. but close enough..)  
I feel like I am running into things in Xubuntu that weren't problems in Ubuntu...  I dunno, but HOW DIFFERENT ACTUALLY are they from each other??  Is it actually more finicky to install a different DE over Ubuntu?

My main goal here is to be able to leech from the most massive and complete pile of articles and posts that accurately help me do the most stuff.  I figured Ubuntu was the biggest pile...  Correct me if I am wrong there too, but I am most used to debian stuff due to raspberry pi.

Thank you!!!

---

### Post by ActionParsnip on 2020-12-10
You can install as many DEs as you like. You just choose the active one when you log in. Xubuntu uses XFCE. If you like Plasma then install Kubuntu.
Xubuntu is aimed at lower end systems and uses leaner, less resource hungry options for applications.

BTW, if you are reading logs, I don't recommend a GUI text editor. You can use grep to search the file in the terminal for the things you want to see. You'll find it much quicker. If you go to any Linux system and can grep effectively then you can search any text file as you need. This means its a transferable skill

---

### Post by Impavidus on 2020-12-10
The Software tool or whatever it's called nowadays tries to make things easy for beginners by hiding difficult things like the difference between snaps and deb packages. Unfortunately this difference is very relevant, so that may have been a bad idea.

I don't use the Software tool. In fact, I removed it, along with all tools handling snaps. To install or remove software I use the command line or Synaptic, which is the GUI package manager that was the default on early releases of Ubuntu (I started with Ubuntu 6.06).

As stated above, the Ubuntu flavour that comes with plasma is Kubuntu. It also comes with kate, I think. Different Ubuntu flavours all use the same repositories and have the same software available for installation, but some combinations work better than others. Applications that have been designed for a particular desktop environment may integrate less well in a different desktop environment, although they will run, and may lead to higher memory usage by loading mutiple libraries for the same task. Different Ubuntu flavours have different looks, but the command line tools they use are the same (except, of course, the command line tools that configure the GUI).

---

### Post by phuzzyday on 2020-12-10
Thanks everyone!!!!

---

### Post by phuzzyday on 2020-12-10
So, sorry if I'm beating this to death, before I dig my roots in deep, I have Xubuntu with Plasma running now.  Aside from the leftover files for now, how would this be different from Kubuntu?  Should I just reinstall with that?  I've spent a few days setting stuff up, nothing major, but would there be any benefit aside from the extra files I could remove anyhow?  Thanks for being super helpful!

---

### Post by Impavidus on 2020-12-11
> **phuzzyday said:**
> ... would there be any benefit aside from the extra files I could remove anyhow? Not really.

---

### Post by HermanAB on 2020-12-11
Hmm, sometimes I think that the best version of Ubuntu is straight up Debian.  This is kinda sad since Ubuntu was originally supposed to be a more user friendly Debian and these days it isn’t.

Your problems with Kate were due to another lady called PAM and man, is she ever moody...

IMHO Snaps address a problem that nobody ever had - badly.  There are various things I remove from every Linux install: snaps, the damn zeroconf 169 address server and a few other useless utilities.

---

