---
title: "I don't understant this alert"
date: 2019-11-14
forum: General Help
---

### Post by edstevens on 2019-11-14
Ubuntu 16.04 LTS, running Cinnamon desktop.
In the lower right corner of my status bar, I get an alert - red circle with horizontal white line.  Opening it, I get the following message:

An error occurred, please run Package Manager
 from the right-click menu or apt-get in a
 terminal to see what is wrong.
 The error message was: ‘Error: Opening the
 cache (E:Unable to parse package file /var/lib/
 apt/lists/
 ppa.launchpad.net_libreoffice__ppa__ubuntu__dists__xenial__Release
 (1). E:The package lists or status file could not 
 be parsed or opened.)’. This usually means that
 your installed packages have unmet
 dependencies.

I'm not sure what to do with it.  Nothing seems to be mis-behaving. The suggestion to run apt-get does not suggest what command line options should be supplied with it.  And I don't know what it means by the "right-click menu"   Right-click on the 'menu' icon only configures the menu itself.

---

### Post by TheFu on 2019-11-14
I suspect the PPA for libreoffice on xenial (16.04) has been killed off.  If true, no more updates, fixes, will be available.
The version I have installed without the PPA is:
```
libreoffice-gnome   1:5.1.6~rc2-0ubuntu1~xenial10
```

Your situation will determine the best corrective action to be taken.  Options are:
[LIST]
[*]wait a few days and see of the PPA comes back.
[*]do nothing. Live with the unpatched version currently installed
[*]remove the PPA, update then upgrade and live with whatever version gets installed.
[/LIST]

I would do nothing for a week, then decide from the other two options.

---

### Post by Dennis N on 2019-11-14
If you are looking for a later version, LibreOffice supplies an appimage that will give you the latest version. I found it works very well.

[https://www.libreoffice.org/download/appimage/](https://www.libreoffice.org/download/appimage/)

Also, there is a snap package if that suits you:

[https://snapcraft.io/libreoffice](https://snapcraft.io/libreoffice)

---

### Post by TheFu on 2019-11-14
Some storage limitations with Snaps: 
[https://forum.snapcraft.io/t/libreoffice-snap-cant-find-my-other-hard-disk/6456](https://forum.snapcraft.io/t/libreoffice-snap-cant-find-my-other-hard-disk/6456)

May not be important at all for many people.

---

### Post by edstevens on 2019-12-13
Sorry for the very late reply.  I've been juggling several chainsaws, and this issue has until now been a low priority.  So, how do I 'remove the ppa'?  I'm not at the moment looking for updates to LO.  But I do have Firefox complaining about not being the latest version and blocking my access to certain web pages - like Amazon My Music.  When I try to update that with apt-get, I get the same error as reported at the start of this thread.

---

### Post by TheFu on 2019-12-13
Amazon changed their DRM for music which broke all my Linux access last month sometime. I don't use it much, so it isn't the end of the world. Also, have a cheap Fire 8 tablet, so the amazon music stuff works with that.  Yep, just tried A-Music and it doesn't work even after I "allow DRM"

As for removing a PPA, there is a program that does it, or you can go into the Repo settings for the GUI package manager you use or you can go into /etc/apt/sources.d/ and find the libreoffice PPA file there, move it somewhere else.
[B]sudo apt update
sudo apt upgrade
[/B] should get the main Canonical repo version installed.  In theory.

---

### Post by mc4man on 2019-12-13
The libreoffice ppa's I see are active for 16.04 but anyway, just
Open Software & Updates > Other
Highlight the ppa, click remove. 

Refresh sources & see..

---

### Post by edstevens on 2019-12-13
> **mc4man said:**
> The libreoffice ppa's I see are active for 16.04 but anyway, just
Open Software & Updates > Other
Highlight the ppa, click remove. 

Refresh sources & see..

Now things a getting real bizzare!
I'm running the Cinnamon desktop. I click on "menu" in the task bar, then select "Administration", then "Software Updater" ... and absolutely nothing happens. Nothing opens.

---

### Post by edstevens on 2019-12-13
> **TheFu said:**
> Amazon changed their DRM for music which broke all my Linux access last month sometime. I don't use it much, so it isn't the end of the world. Also, have a cheap Fire 8 tablet, so the amazon music stuff works with that.  Yep, just tried A-Music and it doesn't work even after I "allow DRM"

As for removing a PPA, there is a program that does it, or you can go into the Repo settings for the GUI package manager you use or you can go into /etc/apt/sources.d/ and find the libreoffice PPA file there, move it somewhere else.
[B]sudo apt update
sudo apt upgrade
[/B] should get the main Canonical repo version installed.  In theory.

I have no /etc/apt/sources.d, though I do have a /etc/apt/sources.list.d
[INDENT][FONT=courier new]ed@ed-Gazelle-00:/etc/apt$ pwd
/etc/apt
ed@ed-Gazelle-00:/etc/apt$ ll
total 56
drwxr-xr-x   7 root root  4096 Mar 27  2019 ./
drwxr-xr-x 158 root root 12288 Jun 22 14:27 ../
drwxr-xr-x   2 root root  4096 Jun 20 06:09 apt.conf.d/
drwxr-xr-x   2 root root  4096 Mar 14  2019 auth.conf.d/
drwxr-xr-x   2 root root  4096 Apr 14  2016 preferences.d/
-rw-rw-r--   1 root root  3010 Dec 23  2018 sources.list
drwxr-xr-x   2 root root  4096 Dec 23  2018 sources.list.d/
-rw-rw-r--   1 root root  3010 Dec 23  2018 sources.list.save
-rw-r--r--   1 root root 12255 Jul 19  2016 trusted.gpg
drwxr-xr-x   2 root root  4096 Dec 23  2018 trusted.gpg.d/
ed@ed-Gazelle-00:/etc/apt$ 

[/FONT][/INDENT]
And within sources.list.d[INDENT][FONT=courier new]ed@ed-Gazelle-00:/etc/apt/sources.list.d$ pwd
/etc/apt/sources.list.d
[email]ed@ed-Gazelle-00:/etc/apt/sources.list[/email].d$ ll
total 36
drwxr-xr-x 2 root root 4096 Dec 23  2018 ./
drwxr-xr-x 7 root root 4096 Mar 27  2019 ../
-rw-r--r-- 1 root root  274 Dec 23  2018 libreoffice-ubuntu-ppa-xenial.list
-rw-r--r-- 1 root root  274 Dec 23  2018 libreoffice-ubuntu-ppa-xenial.list.save
-rw-r--r-- 1 root root  140 Dec 23  2018 system76-dev-ubuntu-stable-xenial.list
-rw-r--r-- 1 root root  140 Dec 23  2018 system76-dev-ubuntu-stable-xenial.list.save
-rw-r--r-- 1 root root    0 Dec 16  2016 tualatrix-ubuntu-ppa-xenial.list
-rw-r--r-- 1 root root    0 Dec 16  2016 tualatrix-ubuntu-ppa-xenial.list.save
-rw-r--r-- 1 root root  136 Dec 23  2018 webupd8team-ubuntu-java-xenial.list
-rw-r--r-- 1 root root  175 Dec 23  2018 xenial-partner.list
-rw-r--r-- 1 root root  175 Dec 23  2018 xenial-partner.list.save
[email]ed@ed-Gazelle-00:/etc/apt/sources.list[/email].d$ 
[/FONT][/INDENT]

The sudo apt commands returned a variety of errors, which may or may not be expected.  Of course they are buried in a very lengthy output.

---

### Post by TheFu on 2019-12-13
My mistake.  /etc/apt/sources.list.d/ is the directory.  I use tab-completion for stuff like this so I don't have to remember exact details, just enough to discover the correct answer while typing.

I'd move the libreoffice-ubuntu-ppa-xeni* files somewhere else.
Then do the update/upgrade process I wrote above.

If everything works ok, delete the 2 files you moved.  If not, put them back and do the update/upgrade process again. Shouldn't be any worse than it was.

---

### Post by edstevens on 2019-12-14
To quote Albert the Alligator (From the Pogo comic strip), "this just  gets curioser and curioser."  As I was going to try to remove the file  from /etc/apt/sources.list.d,  I happened to notice that the alert that  has been on my desktop, that was the source of the original question in  this thread and was still there yesterday, is now gone.  Guessing  something  about the sudo apt command I ran yesterday finally cleared it  and I just now noticed. And while yesterday I reported that the  Software Updater would not open, today it does.  And opens with "failed  to download repository information. Check your internet connection.  [settings] [try again][ok]."
Click OK and it brings up a list of  installed software with a checkbox next to each, and the message "some  software couldn't be checked for updates". click OK and enter root  password, and we get 'requires installation of untrusted packages'.   Click 'ok' and it just goes away.

---

### Post by QIII on 2019-12-14
Just a literary point here -- that is actually from Lewis Carroll: 

> 
"Curiouser and Curiouser!" Cried Alice (she was so much surprised, that for the moment she quite forgot how to speak good English). 


Carry on!  :)

---

### Post by edstevens on 2019-12-15
I guess I failed to pick up that Walt Kelly was borrowing from Lewis Carrol.  Ah well, as a kid I was much more into Pogo than Alice.  ;)

---

### Post by stereomac2 on 2019-12-15
I don't know how much help I'll be because I shouldn't post to what I would perceive is an advanced question, but, I'm think I'm having the same problem you are.  The difficulty lies in getting back your security and system updates after inadvertently changing your sources.lists or /var/lib/apt/lists. 

 I love Ubuntu and I've had so much help reading through forums on the internet.  I couldn't thank you people enough, might as well start now.  

I don't have a good answer for your problem but i'm totally interested.  I'll be paying much more attention to my PPA in the future.

---

