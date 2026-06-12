---
title: "[SOLVED] Real Player"
date: 2008-07-09
forum: General Help
---

### Post by Dyffo on 2008-07-09
I have downloaded  Real Player off the Web, it has arrived as a .bin file. can anyone help me with the installation procedure - at the moment I am getting nowhere !!

---

### Post by larka06 on 2008-07-09
jimmy the saint has a post that works

---

### Post by Cap'n Skyler on 2008-07-09
> **Dyffo said:**
> I have downloaded  Real Player off the Web, it has arrived as a .bin file. can anyone help me with the installation procedure - at the moment I am getting nowhere !!

there are much better players to use.amarok is good and can be installed from synaptic.
 are you trying to get rhapsody to work?:popcorn:

---

### Post by steveneddy on 2008-07-09
Gotta make it executable

cd to the file and execute this command

```
chmod +x RealPlayer11GOLD.bin
```

then in terminal

```
./RealPlayer11GOLD.bin
```

---

### Post by Sim777 on 2008-07-10
> **Cap'n Skyler said:**
> there are much better players to use.amarok is good and can be installed from synaptic.
 are you trying to get rhapsody to work?:popcorn:



Is there a codecs that enables user to play .rm in totem?

---

### Post by Dyffo on 2008-07-10
Sorry  - but amarok is no use,I need a  GOOD Video Media Player, also some of my streaming videos will only play on either Windows Media player or Real player !!

---

### Post by mahboop on 2008-07-11
> **Sim777 said:**
> Is there a codecs that enables user to play .rm in totem?
[CENTER][B][COLOR="Green"]anyone??

--
see you[/COLOR][/B][/CENTER]

---

### Post by Dyffo on 2008-07-11
Hi Guys - this is the one - it does everything and in HD as well !!!. It has a version specifiacally for UBUNTU includes repositories etc VERY easy to install. I have forgotten the Real Player ???
	Miro - free, open source internet tv and video player
A free, open source Internet TV and video player that can automatically download videos from RSS-based channels. Features a built-in BitTorrent client. For Windows, Mac OS X and GNU/Linux.
[www.getdemocracy.com/](www.getdemocracy.com/) [www.getdemocracy.com/](www.getdemocracy.com/) · Cached

---

### Post by bodhi.zazen on 2008-07-11
> **Dyffo said:**
> I have downloaded  Real Player off the Web, it has arrived as a .bin file. can anyone help me with the installation procedure - at the moment I am getting nowhere !!

There are some formats that work ONLY IN REALPLAYER.

There is a .deb and it is easy to install :

[https://help.ubuntu.com/community/RealPlayerInstallationMethods?action=show&redirect=RealPlayer#Install%20RealPlayer.deb%20using%20dkpg](https://help.ubuntu.com/community/RealPlayerInstallationMethods?action=show&redirect=RealPlayer#Install%20RealPlayer.deb%20using%20dkpg)

---

### Post by jessejazza on 2008-07-11
> **steveneddy said:**
> Gotta make it executable

cd to the file and execute this command

```
chmod +x RealPlayer11GOLD.bin
```

then in terminal

```
./RealPlayer11GOLD.bin
```

I've used this and it was fine. This was the only way i could get streaming video to work in Firefox. Helix??

Ralplayer provides all one's needs i've found.

---

### Post by Dyffo on 2008-07-11
> **bodhi.zazen said:**
> There are some formats that work ONLY IN REALPLAYER.

There is a .deb and it is easy to install :

[https://help.ubuntu.com/community/RealPlayerInstallationMethods?action=show&redirect=RealPlayer#Install%20RealPlayer.deb%20using%20dkpg](https://help.ubuntu.com/community/RealPlayerInstallationMethods?action=show&redirect=RealPlayer#Install%20RealPlayer.deb%20using%20dkpg)

Got it and YES IT WORKS  THANKS a Bundle - have now got more Players than you can imagine !!! there cannot be a file I cannot play now

---

### Post by Ataris on 2008-07-11
Go back to the download page and download the RedHat file (the link is below the Download button). You will get an .rpm file instead of a .bin file. Make sure the file is on your desktop. Then you will need to install Alien by typing: ```
sudo apt-get install alien
``` After that, enter the next command:
```

cd ~/Desktop/
sudo alien RealPlayerGOLD.rpm

```
Wait for the terminal to say that the deb package is finished, and then on your desktop you will find RealPlayer.deb. Simply open the .deb package and it will install.

You can run RealPlayer by opening Nautilus and going to /opt/RealPlayer/. You will find the file there. Enjoy!

---

### Post by bodhi.zazen on 2008-07-11
> **Ataris said:**
> Go back to the download page and download the RedHat file (the link is below the Download button). You will get an .rpm file instead of a .bin file. Make sure the file is on your desktop. Then you will need to install Alien by typing: ```
sudo apt-get install alien
``` After that, enter the next command:
```

cd ~/Desktop/
sudo alien RealPlayerGOLD.rpm

```Wait for the terminal to say that the deb package is finished, and then on your desktop you will find RealPlayer.deb. Simply open the .deb package and it will install.

You can run RealPlayer by opening Nautilus and going to /opt/RealPlayer/. You will find the file there. Enjoy!

naw, don't do that.

First there is a .deb that is working just fine, see my previous post ....

Second, if at all possible, go for installing from source rather then alien. In this case, the .bin also works.

---

### Post by Ataris on 2008-07-11
> **bodhi.zazen said:**
> naw, don't do that.

First there is a .deb that is working just fine, see my previous post ....

Second, if at all possible, go for installing from source rather then alien. In this case, the .bin also works.

Really? Compiling things from source tends to produce all kinds of problems. Alien is an easy solution if you know where to find the program after installation.

---

### Post by bodhi.zazen on 2008-07-11
Yea, alien can potentially trash you system as .rpm are packaged in a different way then .deb

Source is as clean as a package manager, save the source code in ~/src

Look at this :

[http://kitenet.net/~joey/code/alien/](http://kitenet.net/~joey/code/alien/)

And an example of what *can* happen :

[http://ubuntuforums.org/showthread.php?t=151997](http://ubuntuforums.org/showthread.php?t=151997)

Yes, it is an old thread, but post #2 is a nice discussion of what may happen with alien.

I agree alien *usually* works, BUT if there is a problem it can be catastrophic.

---

### Post by steveneddy on 2008-07-12
> **Ataris said:**
> Really? **[COLOR="Blue"]Compiling things from source tends to produce all kinds of problems.[/COLOR]** Alien is an easy solution if you know where to find the program after installation.

You're kidding me, right?

compiling from source on your system gives you a better install than from a repository.

And from .rpm?

Why? Especially if you can compile from source.

Alien should only be used if the software you need isn't available anywhere else and you really need to have it today.

Most developers will post it in source on the web page where you got the .rpm file if you just e-mail them. May take a little bit, but they generally have it in source anyway.

I consider using alien like buying a container of chocolate milk, and using some crafty ways making it white milk. Both milk, but different. Alien works, but it is possible to get a buggy application doing this than going for an all source install.

Gentoo and Slack both install everything from source, which is why it is so popular. Everything runs great when it is made for your machine.

---

### Post by Ataris on 2008-07-13
I'll agree that applications don't always work correctly, but compiling from source requires many different libraries, etc. When I try to compile anything it always gives me an error.

---

### Post by steveneddy on 2008-07-14
> **Ataris said:**
> I'll agree that applications don't always work correctly, but compiling from source requires many different libraries, etc. When I try to compile anything it always gives me an error.

Well - it tells you which libs to install.

Just install them.

---

