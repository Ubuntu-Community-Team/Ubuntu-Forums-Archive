---
title: "How to get back toolbar in Gedit?"
date: 2016-06-04
forum: General Help
---

### Post by abcuser on 2016-06-04
Hi,
I used Ubuntu 14.04 LTS where Gedit looked fantastic having excellent toolbar. Now I installed Ubuntu 16.04 and there is minimalistic toolbar which is pretty much not really useful. How to get back toolbar in Gedit?
Thanks

**EDIT:** Solution is at post number 20:  [http://ubuntuforums.org/showthread.php?t=2326742&page=2&p=13508865#post13508865](http://ubuntuforums.org/showthread.php?t=2326742&page=2&p=13508865#post13508865)

---

### Post by HermanAB on 2016-06-04
I'd suggest that you install Geany and forget about Gedit.

---

### Post by vasa1 on 2016-06-04
> **HermanAB said:**
> I'd suggest that you install Geany and forget about Gedit.
+1 ;)

Or maybe try the editor (pluma?) that Ubuntu Mate provides? I think that that's a gedit clone but still "old-fashioned".

---

### Post by fthx on 2016-06-04
> **abcuser said:**
> Hi,
I used Ubuntu 14.04 LTS where Gedit looked fantastic having excellent toolbar. Now I installed Ubuntu 16.04 and there is minimalistic toolbar which is pretty much not really useful. How to get back toolbar in Gedit?
Thanks

Because *I* prefer to answer your question rather than talking about another text editor :-# : you could try to install the Gedit version of Trusty (I think it is 3.10 ?). The new Gnome apps appearance moves away a lot of toolbars and as far I know you can't bring them back.

---

### Post by mc4man on 2016-06-04
You can use an older version of gedit **&** gedit-plugins (that used a toolbar, no csd) in 16.04 though it would or should have to be built for 16.04 
(- did so here prior to Ubuntu fixing csd for an ubuntu session, could stick in a ppa though I would question interest in such.
However it seems all the previous toolbar functions are in the gedit menus so the question would be  - 
Did Gnome manage to improve gedit/gedit plugins from 3.10 to 3.18 that would make the slight inconvenience of going to the menus worth it? You'd hope they did manage to do something(s) useful in 2+ yrs. other than adjust the interface...

---

### Post by CantankRus on 2016-06-04
I find gedit still works fine for me if I change the menu preferences in Appearances > Behaviour
except I can't get any menus in a root gedit window no matter the preferences.
Can anyone get a menu when running "gksudo gedit".

---

### Post by vasa1 on 2016-06-04
Here's what I get with *gksudo gedit* but this is with the Openbox session of Lubuntu and gedit was installed with *--no-install-recommends*

---

### Post by CantankRus on 2016-06-04
> **vasa1 said:**
> Here's what I get with *gksudo gedit* but this is with the Openbox session of Lubuntu and gedit was installed with *--no-install-recommends*
Yeah, other sessions are ok but the unity plugin handles the decorations in Ubuntu and has the option to draw menus in the titlebar.
I don't know why I can't get a menu in the titlebar of a root gedit window?

---

### Post by mc4man on 2016-06-04
> **CantankRus said:**
> Yeah, other sessions are ok but the unity plugin handles the decorations in Ubuntu and has the option to draw menus in the titlebar.
I don't know why I can't get a menu in the titlebar of a root gedit window?
Root gui windows in Ubuntu can't use the global menu so typically they'd be in the app title/menu? bar. (ie. ck. a root nautilus window. 
However in the case of the newer gedit there is no title/menubar that accepts menus, the way you are getting them now is thru locally integrated menus, ie a unity option. That option can not be used by root for various reasons.

So a root gedit preferences can only be set thru a root dconf-editor. (sudo -H dconf-editor or gksudo dconf-editor
Note that not all schemas, keys, options exposed in a root dconf-editor can be used or changed so care is needed in the root dconf-editor.
For a root gedit I only set line numbers,  a color scheme & make sure no backups,  as in screen, scheme of oblivion.

---

### Post by mc4man on 2016-06-04
If one decided to use the older gedit in 16.04 then a root gedit would automatically have the menus & pref's in the gedit window as in screen

---

### Post by CantankRus on 2016-06-04
> **mc4man said:**
> If one decided to use the older gedit in 16.04 then a root gedit would automatically have the menus & pref's in the gedit window as in screen

What would be the process of building and installing older gedit and gedit-plugins versions.
I have rarely compiled anything.

---

### Post by mc4man on 2016-06-05
> **CantankRus said:**
> What would be the process of building and installing older gedit and gedit-plugins versions.
I have rarely compiled anything.Well you'd get both the gedit & gedit-plugin sources from wily, build gedit, then the plugins as plugins need gedit-dev headers.
Too much of a pita really. I've found the best is to just do debian package builds inc. relevant patches if needed & let LP take care of it all. (organize, build, package, sources, changes, ect.
So here - read & act if desired. (published  in 1/2 hr. or less, page will show updates

[https://launchpad.net/~mc3man/+archive/ubuntu/older](https://launchpad.net/~mc3man/+archive/ubuntu/older)

---

### Post by CantankRus on 2016-06-05
> **mc4man said:**
> Well you'd get both the gedit & gedit-plugin sources from wily, build gedit, then the plugins as plugins need gedit-dev headers.
Too much of a pita really. I've found the best is to just do debian package builds inc. relevant patches if needed & let LP take care of it all. (organize, build, package, sources, changes, ect.
So here - read & act if desired. (published  in 1/2 hr. or less, page will show updates

[https://launchpad.net/~mc3man/+archive/ubuntu/older](https://launchpad.net/~mc3man/+archive/ubuntu/older)
Ok thanks.
I found this [**_[COLOR="#B22222"]askubuntu answer[/COLOR]_**]("http://askubuntu.com/questions/766055/how-do-i-downgrade-gedit-to-a-previous-3-10-4-version-in-ubuntu-16-04-lts") and am halfway through doing it.
Using a PPA build looks far easier.

---

### Post by mc4man on 2016-06-05
> **CantankRus said:**
> Ok thanks.
I found this [**_[COLOR="#B22222"]askubuntu answer[/COLOR]_**]("http://askubuntu.com/questions/766055/how-do-i-downgrade-gedit-to-a-previous-3-10-4-version-in-ubuntu-16-04-lts") and am halfway through doing it.
Using a PPA build looks far easier.
Yeah, I'd say so... at least in regards to gedit & gedit-plugins

---

### Post by CantankRus on 2016-06-05
Thanks mc4man,
I am now using the ppa and menus are back. :)
The askubuntu link I provided earlier has a script to automate the downgrade and reversal which also works.
Would you recommend locking your ppa versions.
I usually disable ppas like this and every so often enable to check for updates.

---

### Post by abcuser on 2016-06-05
> **mc4man said:**
> If one decided to use the older gedit in 16.04 then a root gedit would automatically have the menus & pref's in the gedit window as in screen
This looks excellent. How did you install previous version of Gedit?

---

### Post by CantankRus on 2016-06-05
> **abcuser said:**
> This looks excellent. How did you install previous version of Gedit?

Go to the ppa link in mc4man's [**_[COLOR="#B22222"]post #12[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=2326742&p=13499456#post13499456") and follow instructions.

---

### Post by mc4man on 2016-06-05
> **CantankRus said:**
> Thanks mc4man,
I am now using the ppa and menus are back. :)
The askubuntu link I provided earlier has a script to automate the downgrade and reversal which also works.
Would you recommend locking your ppa versions.
I usually disable ppas like this and every so often enable to check for updates.
No 
The ppa versions are currently seen by apt as higher than what's in xenial so no reason to lock. The odds of gedit in 16.04 getting an update to the real 3.18 that pushes it ahead are slim.
As far as the ppa version it won't get updated unless the above happens or in the unlikely chance that an improvement to 3.10 presents itself.

---

### Post by CantankRus on 2016-06-12
[COLOR="#FF0000"]EDIT:[/COLOR] Disregard... purges successfully. I forgot when playing around I had put packages on hold.

Hi mc4man,
Do you know why gedit doesn't return to default version when I purge your ppa?
```
**[COLOR="#006400"]glen@Xenial:~$[/COLOR] egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*.list**
/etc/apt/sources.list:deb http://archive.canonical.com/ubuntu xenial partner
/etc/apt/sources.list:deb http://ftp.iinet.net.au/pub/ubuntu/ xenial main restricted universe multiverse
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu/ xenial-security main restricted multiverse universe
/etc/apt/sources.list:deb http://ftp.iinet.net.au/pub/ubuntu/ xenial-updates main restricted multiverse universe
/etc/apt/sources.list:deb http://ftp.iinet.net.au/pub/ubuntu/ xenial-backports main restricted multiverse universe
/etc/apt/sources.list.d/mc3man-ubuntu-older-xenial.list:deb http://ppa.launchpad.net/mc3man/older/ubuntu xenial main #gedit-older version
/etc/apt/sources.list.d/opera-developer.list:deb https://deb.opera.com/opera-developer/ stable non-free #Opera Browser (final releases)

**[COLOR="#006400"]glen@Xenial:~$[/COLOR] sudo ppa-purge ppa:mc3man/older**
Updating packages lists
PPA to be removed: mc3man older
Package revert list generated:

Disabling mc3man PPA from 
/etc/apt/sources.list.d/mc3man-ubuntu-older-xenial.list
Updating packages lists
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gtk3-engines-unico linux-headers-4.4.0-21 linux-headers-4.4.0-21-generic linux-image-4.4.0-21-generic linux-image-extra-4.4.0-21-generic
Use 'sudo apt autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 4 not to upgrade.
PPA purged successfully

**[COLOR="#006400"]glen@Xenial:~$[/COLOR] egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*.list**
/etc/apt/sources.list:deb http://archive.canonical.com/ubuntu xenial partner
/etc/apt/sources.list:deb http://ftp.iinet.net.au/pub/ubuntu/ xenial main restricted universe multiverse
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu/ xenial-security main restricted multiverse universe
/etc/apt/sources.list:deb http://ftp.iinet.net.au/pub/ubuntu/ xenial-updates main restricted multiverse universe
/etc/apt/sources.list:deb http://ftp.iinet.net.au/pub/ubuntu/ xenial-backports main restricted multiverse universe
/etc/apt/sources.list.d/opera-developer.list:deb https://deb.opera.com/opera-developer/ stable non-free #Opera Browser (final releases)

**[COLOR="#006400"]glen@Xenial:~$[/COLOR] apt-cache policy gedit**
gedit:
  Installed: 3.18.3.is.really.3.10.4-0ubuntu13
  Candidate: 3.18.3.is.really.3.10.4-0ubuntu13
  Version table:
 *** 3.18.3.is.really.3.10.4-0ubuntu13 100
        100 /var/lib/dpkg/status
     3.18.3-0ubuntu4 500
        500 http://ftp.iinet.net.au/pub/ubuntu xenial/main amd64 Packages
```

---

### Post by abcuser on 2016-06-24
Hi,
sorry for late reply. Now I have executed bellow commands in terminal and gedit with toolbar is back. It is older version of Gedit 3.10 instead of 3.18 officially in Ubuntu 16.04, but who cares, I million times like toolbar more then a new version has to offer.

```

sudo apt-add-repository ppa:mc3man/older
sudo apt update
sudo apt install gedit gedit-plugins
sudo apt autoremove
apt-cache policy gedit
gedit &

```

As seen from: "apt-cache policy gedit" the output is:
```

gedit:
  Installed: 3.18.3.is.really.3.10.4-0ubuntu13
  Candidate: 3.18.3.is.really.3.10.4-0ubuntu13
  Version table:
 *** 3.18.3.is.really.3.10.4-0ubuntu13 500
        500 http://ppa.launchpad.net/mc3man/older/ubuntu xenial/main i386 Packages
        100 /var/lib/dpkg/status
     3.18.3-0ubuntu4 500
        500 http://si.archive.ubuntu.com/ubuntu xenial/main i386 Packages

```
Because of naming "is.really." it is very likely that future potential Gedit fixes in 3.18.3-xxx will not override currently installed 3.10.4, because of whole naming thing. Clever in did.

Problem solved! Thanks a million for this gedit toolbar solution.

Thanks a lot for help!

---

