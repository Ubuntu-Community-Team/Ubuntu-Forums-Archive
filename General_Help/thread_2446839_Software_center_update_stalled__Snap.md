---
title: "Software center update stalled ? Snap ?"
date: 2020-07-07
forum: General Help
---

### Post by John_Kirk on 2020-07-07
As a usual software update was near complete the notification stalled on 'snap ?'

I then noticed that the software center had gone.
can't seem to install it as it appears to be locked
After some hunting for a solution i'm guessing that snap is a new software center ??

Anyway I ... this is where I am..

```
:~$ snap changesID   Status  Spawn               Ready               Summary
43   Error   today at 12:23 BST  today at 17:41 BST  Install "snap-store" snap from "stable/ubuntu-20.04" channel
:~$ snap abort snap-store
error: cannot find change with id "snap-store"
:~$ 



```

If I could re-initiate the whole update that would be great ???? as I fear other upgrades included may have also been compromised.. but I 'think' Ubuntu Studio thinks its still installing snap ??? so not allowing me to freshly install it ?

erm..
help .. please.

---

### Post by John_Kirk on 2020-07-09
can I install synaptic and get that to fix the software center ?

---

### Post by grahammechanical on 2020-07-09
There have been a few things happening regarding the Ubuntu Software Center store in Ubuntu 20.04 that may apply to Ubuntu Studio.

1) Ubuntu Software Center was a re-branded Gnome Software. 2)The developers brought in a Snap Store to install snaps. 3) The Snap Store had a lot of work done to it and it became Ubuntu Software with the re-branded Gnome Software being removed. There was a period when my 20.04 system had two Ubuntu Software apps each with its own icon as well as a Snap Store icon. At present this system does not have a Ubuntu Software icon of any kind. They have both been removed. It has a Snap Store that should have been re-labeled Ubuntu Software.

To sort your problem out you could load into Recovery Mode at the Grub menu. We get to it by selecting Advanced options for Ubuntu. At the Recovery menu select Network to establish an Internet connection. When back at the Recovery menu select Root Shell prompt and at the command line type

```
apt update
apt upgrade
```

The system should update/upgrade. When it is finished type

```
exit
```

to return to the Recovery menu and the select Resume to finish boot the OS. You should end up at a desktop running in basic video mode. Shutdown and reboot to load a video driver.

Regards

---

### Post by John_Kirk on 2020-07-10
Many thanks..

What do I press when the computer restarts to enter the grub menu ?

And... after the procedures will my desktop, dater, home folder all be intact ?

---

### Post by Impavidus on 2020-07-11
I may not completely understand your problem. Maybe some background helps.

There are two ways in which software gets packaged for Ubuntu. Two main ways, there are some others. There are deb packages and snap packages. They both have their own set of tools to install or remove them. Deb packages use dpkg, apt and synaptic, snap packages use snap. They are mostly independent, except that the tools that handle snap packages come from deb packages themselves, some higher-level tools (like Ubuntu Software or whatever it's called now) can interact with both sets of tools to handle both types of packages (easy and integrated, but it causes confusion) and some deb packages trigger the installation of snap packages. All important stuff is in deb packages. I've never had any snaps on my system, so I don't know them very well.

If you're worried that your updates to ordinary deb packages are compromised, run this:```
sudo apt update
sudo apt upgrade
```That will check for upgrades for your deb packages, then download and install those upgrades. If it reports no errors, your deb packages are fine. I'll leave it to someone else to check-up your snaps.

As long as you don't start partitioning or reinstalling Ubuntu (or running stupid commands), your data are safe. As long as you've got backups (you should), your data are safe too.

---

### Post by John_Kirk on 2020-07-11
Apt upgrade went well with 20 items updated

About Snap... this is in my menu but clicking it does nothing. (see image)  [IMG]https://ibb.co/fG0xjM2[/IMG]

[[IMG]https://i.ibb.co/jZ4rnhT/snap.png[/IMG]]("https://imgbb.com/")

---

### Post by Dennis N on 2020-07-11
Snap only runs in the terminal. It's the management tool for Snap applications. Try running 'snap' in the terminal for more information.

---

### Post by John_Kirk on 2020-07-11
so... Ubuntu Studio has no software centre now ?

---

### Post by Dennis N on 2020-07-11
> **John_Kirk said:**
> so... Ubuntu Studio has no software centre now ?

I don't use Ubuntu Studio, so I'm not sure what it provides you for finding software. It could be called '**Ubuntu Software**' or just '**Software**'.

---

### Post by monkeybrain20122 on 2020-07-12
> **John_Kirk said:**
> so... Ubuntu Studio has no software centre now ?

Here on my 20.04 the software store is good old gnome-software,  "ubuntu-software" is a dummy package that points to the same thing, the  snap integration is provided by gnome-software-plugin-snap, so in the  software store you find both snap and apt packages (also there is  gnome-software-plugin-flatpak if you want flatpak pages to be accessible  from software store) I suppose you can install gnome-software and  plugin(s) on ubuntu studio if they are not already installed.

---

### Post by John_Kirk on 2020-07-12
The software store is nowhere to be seen under any search

---

### Post by monkeybrain20122 on 2020-07-12
> **John_Kirk said:**
> The software store is nowhere to be seen under any search

Then just install it
```

sudo apt install gnome-software
```

---

### Post by Dennis N on 2020-07-12
> The software store is nowhere to be seen under any search. 
To install the default software store that you get in a new Ubuntu 20.04 install, you would install a snap package:

You must install from the terminal:
```
snap install --channel=latest/stable/ubuntu-20.04 snap-store
```

It will have an icon labeled "Ubuntu Software".

---

### Post by John_Kirk on 2020-07-12
> **monkeybrain20122 said:**
> Then just install it
```

sudo apt install gnome-software
```

Ubuntu Studio is using XFCE .. do I still need gnome-software ?

---

### Post by monkeybrain20122 on 2020-07-12
> **John_Kirk said:**
> Ubuntu Studio is using XFCE .. do I still need gnome-software ?

What is xubuntu's app store, does it have one? Find out and install that one I guess.

---

### Post by John_Kirk on 2020-07-12
Many thanks for all the replys guys :)

---

### Post by Dennis N on 2020-07-12
> **John_Kirk said:**
> Ubuntu Studio is using XFCE .. do I still need gnome-software ?
Ubuntu Studio 20.04 would have that installed by default. So you should not need to install it.
From the .manifest file of Ubuntu Studio (list of default packages on iso):
```

gnome-software	3.36.0-0ubuntu3
gnome-software-common	3.36.0-0ubuntu3
gnome-software-plugin-snap	3.36.0-0ubuntu3

```

---

### Post by John_Kirk on 2020-07-13
Fixed... Thanks Dennis N.

snap install --channel=latest/stable/ubuntu-20.04 snap-store
That was the fix. :) 

I just want Ubuntu Studio to be as it was intended.. Back on the rails now.
Thanks everyone

---

