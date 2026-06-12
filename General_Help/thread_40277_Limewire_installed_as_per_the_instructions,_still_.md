---
title: "Limewire installed as per the instructions, still ain't working"
date: 2005-06-08
forum: General Help
---

### Post by duffmckagan on 2005-06-08
I installed Limewire as mentioned in the Unofficial Guide.

But still I am unable to launch it off from the Applications -->Internet -->Limewire menu.

I guess i committed a small mistake. Linux being case sensitive, is creating problems I suppose.

Here is the mistake I committed.
Instead of installing Limewire in /opt/Limewire (Look at the capital L)
I installed it in /opt/limewire.

To make a compensation, in the launcher menu too, I entered the path as /opt/limewire.

But, all in vain, Limewire isn't working.

---

### Post by zyiro on 2005-06-09
to be quite honest this is going to be an ongoing problem.  Your best bet will be to install GTK-Gnutella - [http://gtk-gnutella.sourceforge.net/](http://gtk-gnutella.sourceforge.net/)  its in the apt repository to install see below.

```
sudo apt-get install gtk-gnutella
```

it will appear in your menu under internet and to run it from teminal just gtk-gnutella.  it uses the same database that limewire uses so you wont notice any difference in content.

-Garrett

---

### Post by duffmckagan on 2005-06-09
Yeah right, the content will be the same, but the speed is ought to vary.

Can you give me the name of the software that is going to be installed?

I mean, Gnutella is the name of the network, and Limewire, Bearshare, etc. are the clients.

Is Gnutella too a client?


Moreover, how do I Uninstall the Limewire I have already installed?

---

### Post by bored2k on 2005-06-09
Ok Limewire IMO owns any Gnutella Linux client, so here is how to get it working:

If you did [http://ubuntuguide.org/#jre](http://ubuntuguide.org/#jre) and downloaded and extracted Limewire. Go to its directory (using your file manager), then right click on runLime.sh - properties - permissions and checkmark on every Execute box. Then double clic on it or inside a terminal cd yourself in that folder and do ./runLime.sh.

You could also have Nicotine (soulseek client), amule (edonkey client), bittorrent (...), apollon (gnutella, fasttrack -kazaa-, opennap and a some more plugins), giftd, etc. 

The best one IMO is Limewire (i have a Limewire Pro account :D). You could also try installing WinMX through wine, wich is very good also.

---

### Post by duffmckagan on 2005-06-09
[QUOTE=bored2k]Ok Limewire IMO owns any Gnutella Linux client, so here is how to get it working:

If you did [http://ubuntuguide.org/#jre](http://ubuntuguide.org/#jre) and downloaded and extracted Limewire. Go to its directory (using your file manager), then right click on runLime.sh - properties - permissions and checkmark on every Execute box. Then double clic on it or inside a terminal cd yourself in that folder and do ./runLime.sh.

You could also have Nicotine (soulseek client), amule (edonkey client), bittorrent (...), apollon (gnutella, fasttrack -kazaa-, opennap and a some more plugins), giftd, etc. 

The best one IMO is Limewire (i have a Limewire Pro account :D). You could also try installing WinMX through wine, wich is very good also.[/QUOTE]
 I have Warty to mention again!


Now some new stuff here for me!

1. What is an IMO?....whats the full form?

---

### Post by bored2k on 2005-06-09
1. In my opinion . [http://it.acronymfinder.com/af-query.asp?string=exact&acronym=IMO](http://it.acronymfinder.com/af-query.asp?string=exact&acronym=IMO)

2. So you have warty huh ? *pas de problème*
Follow [Method 3: Build your own Java package for Ubuntu](http://www.ubuntulinux.org/wiki/Java)

It will work.

---

### Post by duffmckagan on 2005-06-09
But guys, didn't I mention Java is already installed and working fine?

This is when I do 

```
 java -version 
```

```

amit@ubuntu:~ $ java -version
java version "1.5.0_03"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_03-b07)
Java HotSpot(TM) Client VM (build 1.5.0_03-b07, mixed mode, sharing)

```

Thanks.

---

### Post by angrykeyboarder on 2005-06-13
[QUOTE=bored2k]Ok Limewire IMO owns any Gnutella Linux client, so here is how to get it working:

If you did [http://ubuntuguide.org/#jre]("http://ubuntuguide.org/#jre") and downloaded and extracted Limewire. Go to its directory (using your file manager), then right click on runLime.sh - properties - permissions and checkmark on every Execute box. Then double clic on it or inside a terminal cd yourself in that folder and do ./runLime.sh.

You could also have Nicotine (soulseek client), amule (edonkey client), bittorrent (...), apollon (gnutella, fasttrack -kazaa-, opennap and a some more plugins), giftd, etc. 

The best one IMO is Limewire (i have a Limewire Pro account :D). You could also try installing WinMX through wine, wich is very good also.[/QUOTE]

There's also giftoxic ( [http://giftoxic.sourceforge.net/]("http://giftoxic.sourceforge.net/") )which is all-in-one. 

sudo apt-get install giftoxic

---

### Post by duffmckagan on 2005-06-14
According me to Gnutella is better. :-\"
The thing that matters for me is Speed.

Well, I will try that too.
Thanks for the software. :grin:

---

### Post by bored2k on 2005-06-14
[QUOTE=duffmckagan]According me to Gnutella is better. :-\"
The thing that matters for me is Speed.

Well, I will try that too.
Thanks for the software. :grin:[/QUOTE]
 I have not found a faster client than Limewire. In others [apollon/giftoxic/etc] sometimes I even encounter queue lines, wich doesn't happen with my LimewireP account.

---

