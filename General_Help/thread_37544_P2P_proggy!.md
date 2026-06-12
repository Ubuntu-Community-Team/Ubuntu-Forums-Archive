---
title: "P2P proggy!"
date: 2005-05-27
forum: General Help
---

### Post by catastrophee on 2005-05-27
I need to install a P2P program like limewire! Ive been to ubuntuguide.com and tried their version of limewire but could not complete the installation... 

Can anyone help me install something please thanks :)

---

### Post by cdhotfire on 2005-05-27
amule, best of the best.
```

$ sudo apt-get install amule
$ amule

```

then your downloading like a pro.:wink:

---

### Post by bored2k on 2005-05-27
[QUOTE=cdhotfire]amule, best of the best.
```

$ sudo apt-get install amule
$ amule

```

then your downloading like a pro.:wink:[/QUOTE]
 apollon and giftd. This will get you the GNUTELLA (limewire) network. Adding the fasttrack plugin to be able to connect to the KAZAA network of course ;).

My favorite is my sweet Limewire 4.8.1 Pro ;)

Theres also nicotine wich connects to the SOulseek servers.

[http://www.ubuntulinux.org/wiki/FileSharingP2PPeerToPeer](http://www.ubuntulinux.org/wiki/FileSharingP2PPeerToPeer)

---

### Post by picpak on 2005-05-27
Gtk-Gnutella:

```
sudo apt-get gtk-gnutella
```

More stable than Limewire.

---

### Post by SGC on 2005-05-27
Try this to install limewire, it works for me:

download the rpm from [limewire website](http://www.limewire.com/english/content/downloadfree.shtml)  and then converting it using alien, like this:

```
alien LIMEWIRE_PACKAGE.rpm
```
change the LIMEWIRE_PACKAGE.rpm to the name of the package that you downloaded.

after running the previous command you will got a .deb package, install it with dpkg like this:
```
dpkg -i LIMEWIRE_PACKAGE.deb
```

change LIMEWIRE_PACKAGE.deb to the package name that you get from the conversion.

---

### Post by cdhotfire on 2005-05-27
> **bored2k]apollon and giftd. This will get you the GNUTELLA (limewire) network. Adding the fasttrack plugin to be able to connect to the KAZAA network of course  said:**
> http://www.ubuntulinux.org/wiki/FileSharingP2PPeerToPeer[/url]

I wonder where you got this so called "Pro" version.:-\"

---

### Post by catastrophee on 2005-05-27
E: Couldn't find package amule

E: Invalid operation gtk-gnutella

$ sudo apt-get install amule
bash: $: command not found

---

### Post by MrTom on 2005-05-27
I think he meant 

```
sudo apt-get install gtk-gnutella
```

;)

---

### Post by catastrophee on 2005-05-27
sudo apt-get install gtk-gnutella
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gtk-gnutella



( im not liking this) Its xo frkeing complicated.... i guess thats what ljinux is gonna be like... very complicated... 
ineed somuchhelp!!!!

---

### Post by catastrophee on 2005-05-27
Ive got gaim :) lol [email]juggalo_j1@hotmail.com[/email] if any1, i mean any1 wants to help thru IM go ahead and add me. I stil lwant help here though!!

---

### Post by drummer on 2005-05-27
[QUOTE=catastrophee]Ive got gaim :) lol [email="juggalo_j1@hotmail.com"]juggalo_j1@hotmail.com[/email] if any1, i mean any1 wants to help thru IM go ahead and add me. I stil lwant help here though!![/QUOTE]
i'd vote for gtk-gnutella myself.. but you may not have the extra repositories installed if apt can't find the gtk-gnutella package (it's in the universe repository), so have a look at the starter guide on how to add extra repositories if you haven't done that already.

Also, the version in the repositories is a bit old.. there's a new version on the gtk-gnutella website that has some bug fixes ( [GTK2-gtk-gnutella_0.95.3-0_i386.deb]("http://prdownloads.sourceforge.net/gtk-gnutella/GTK2-gtk-gnutella_0.95.3-0_i386.deb?download") ). I'd install first from apt-get after adding extra repositories (to make sure dependencies are solved) then install the newer version using ```
sudo dpkg -i GTK2-gtk-gnutella_0.95.3-0_i386.deb
```[url="http://prdownloads.sourceforge.net/gtk-gnutella/GTK2-gtk-gnutella_0.95.3-0_i386.deb?download"]
[/url]

---

### Post by bored2k on 2005-05-27
[QUOTE=cdhotfire]I wonder where you got this so called "Pro" version.:-\"[/QUOTE]
 It's a 100 percent legal, no piracy.

---

### Post by crane on 2005-05-27
[QUOTE=catastrophee]E: Couldn't find package amule

E: Invalid operation gtk-gnutella

$ sudo apt-get install amule
bash: $: command not found[/QUOTE]
Try aMule

---

### Post by cdhotfire on 2005-05-27
[QUOTE=bored2k]It's a 100 percent legal, no piracy.[/QUOTE]

not what i meant, dude.:smile:

but why did you pay?

if theres plenty of good ones out there.:?

---

### Post by cdhotfire on 2005-05-27
[QUOTE=crane]Try aMule[/QUOTE]

um caps or non caps does not matter on packages.

Catas guy, do you have universe repos on?

[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

then

```

$ sudo apt-get install amule

```

also make sure if you have router, to foward the ports asked by amule.;-)

---

### Post by catastrophee on 2005-05-28
When installing the extra repositories i got a popup something in gedit but i couldnt find the text it told me to find. I check it all and it wanst the same. So it didnt work.

Why are things so difficult!? 

Right now my ubuntu linux wont even start up for some reason it will only go in recovery mode.... itl just hang at a black screen.

---

