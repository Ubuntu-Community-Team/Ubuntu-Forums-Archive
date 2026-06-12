---
title: "how do I get Kdesu?"
date: 2006-11-01
forum: General Help
---

### Post by maddbaron on 2006-11-01
I am using kubuntu edgy.

Whenever I try to add a program called Kompile in adept or konsole it gives me a message that says Break (install) in bright red letters or this:

> maddbaron@baronworks:~$ sudo apt-get install kompile
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kompile: Depends: kdesu but it is not installable
E: Broken packages


any one have any ideas?

---

### Post by Sef on 2006-11-01
> The following packages have unmet dependencies:
kompile: Depends: kdesu but it is not installable

Try this in Konsole:

kdesu aptitude update

kdesu aptitude install Kompile

---

### Post by maddbaron on 2006-11-01
the 1st part i think worked but the second part didnt.

> The following packages are BROKEN:
  kompile
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 175kB of archives. After unpacking 926kB will be used.
The following packages have unmet dependencies:
  kompile: Depends: kdesu which is a virtual package.
Resolving dependencies...
Unable to resolve dependencies!  Giving up...
Abort.

I guess kompile just doesnt work anymore. thank you for the help though.

---

### Post by Kobo_W_Italy on 2006-11-26
> **Sef said:**
> Try this in Konsole:

kdesu aptitude update


I've tried to do so but it says:

root@roby-desktop:/home/roby# sudo apt-get upgrade build-dep
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@roby-desktop:/home/roby# kdesu aptitude update
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdesu: cannot connect to X server :0.0


](*,)

---

### Post by Clouseau on 2007-02-02
I have a similar issue when starting Adept in Ubuntu 6.10 Edgy. I get this msg:

Failed to execute child process "kdesu" (No such file or directory)

Any ideas?

---

### Post by tokh on 2007-03-16
> **Clouseau said:**
> I have a similar issue when starting Adept in Ubuntu 6.10 Edgy. I get this msg:

Failed to execute child process "kdesu" (No such file or directory)

Any ideas?

i get the same error when i try to run adept. please help me (us)

---

### Post by kerry_s on 2007-03-16
Kdesu is part of kdebase, try reinstalling that.

---

### Post by tokh on 2007-03-16
hello,

i found the answer a little while after my first post here.

(from another thread)
Did you install Adept on Ubuntu/GNOME? If yes, try to edit your menu entry for Adept, and check if it says something like "kdesu adept_manager" (on Edgy) or "kdesu adept" (on Dapper). If you are on GNOME, change "kdesu" to "gksudo".

---

### Post by kerry_s on 2007-03-16
> **tokh said:**
> hello,

i found the answer a little while after my first post here.

(from another thread)
Did you install Adept on Ubuntu/GNOME? If yes, try to edit your menu entry for Adept, and check if it says something like "kdesu adept_manager" (on Edgy) or "kdesu adept" (on Dapper). If you are on GNOME, change "kdesu" to "gksudo".

In gnome, it's easier to just link, that way you don't have to hunt down and change all the kdesu and kdesudo.

sudo ln -s /usr/bin/gksu /usr/bin/kdesu
sudo ln -s /usr/bin/gksudo /usr/bin/kdesudo

---

