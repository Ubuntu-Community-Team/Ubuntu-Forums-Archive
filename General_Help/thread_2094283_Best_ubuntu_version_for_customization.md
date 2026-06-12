---
title: "Best ubuntu version for customization?"
date: 2012-12-13
forum: General Help
---

### Post by CorruptDNA on 2012-12-13
I would like to know what is the best ubuntu version i should install for customizations? 

- I would like to be able to customize the login screen
- Customize the desktop
- and not have the long bar to the left that is in the new ubuntus .. the one u cannot get rid of. 

and also would like to know, how to install it without deleting my windows partition because last time i ended up doing that.

Any suggestions ?

---

### Post by TBABill on 2012-12-13
You'll need a different desktop environment to get rid of the Unity launcher. You can install KDE, Xfce, LXDE, Cinnamon. KDE probably has the most customization but others are very customizable as well. Unity seems to be lease customizable at this time.
 
To save your windows partition(s), defrag, make sure you know every partition on the system and shrink the large Windows partition and create a new partition in that new space. Gparted is good for that and you can do it from a LiveCD/DVD/USB.

---

### Post by CorruptDNA on 2012-12-13
> **TBABill said:**
> You'll need a different desktop environment to get rid of the Unity launcher. You can install KDE, Xfce, LXDE, Cinnamon. KDE probably has the most customization but others are very customizable as well. Unity seems to be lease customizable at this time.
 
To save your windows partition(s), defrag, make sure you know every partition on the system and shrink the large Windows partition and create a new partition in that new space. Gparted is good for that and you can do it from a LiveCD/DVD/USB.

lol, but i want to use ubuntu since it has the fastest booting time.. I think since karmic kaola, we have been unable to customize the login screen.. which version was karmic kaola? 
Oke, so you are saying that i should create a new partition and install ubuntu on that.. how large should it be .. ?

---

### Post by Cheesemill on 2012-12-13
You can still customize the login screen, googling for 'lightdm customization' returns loads of hits.

To get rid of Unity (that provides the dash you want to get rid of) you need to install a different DE (desktop environment). You can either install K/X/L ubuntu from scratch or add their DE's to your existing installation by installing the relevant package (kubuntu-desktop, xubuntu-desktop etc.).

---

### Post by haqking on 2012-12-13
> **CorruptDNA said:**
> **lol, but i want to use ubuntu** since it has the fastest booting time.. I think since karmic kaola, we have been unable to customize the login screen.. which version was karmic kaola? 
Oke, so you are saying that i should create a new partition and install ubuntu on that.. how large should it be .. ?

You can use Ubuntu, they are talking about a different DE, you can have multiple DE's installed in any version of Ubuntu all providing different levels of configuration, i personally prefer KDE which is highly configurable and customizable

---

### Post by snowpine on 2012-12-13
Here is a good tutorial to install a minimal, unthemed, "bare-bones" Ubuntu system:

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

From there you can customize in a million different ways, enjoy! :)

---

### Post by CaptainMark on 2012-12-13
I would use Linux Mint, its built from Ubuntu and is completely compatible with it but has all the features your looking for

---

### Post by Mark Phelps on 2012-12-13
> **TBABill said:**
> ... Gparted is good for that and you can do it from a LiveCD/DVD/USB.

Actually, with Win7 -- NO -- it is NOT good for that, as it can end up corrupting the Windows filesystem and rendering Win7 unbootable -- thus, very hard to fix.

When Win7 is the OS, the safe way to do this is to use the Win7 Disk Management utility to shrink the partition.  Not as flexible as GParted, but it doesn't run the risk of filesystem corruption.

---

### Post by CorruptDNA on 2012-12-13
> **Mark Phelps said:**
> Actually, with Win7 -- NO -- it is NOT good for that, as it can end up corrupting the Windows filesystem and rendering Win7 unbootable -- thus, very hard to fix.

When Win7 is the OS, the safe way to do this is to use the Win7 Disk Management utility to shrink the partition.  Not as flexible as GParted, but it doesn't run the risk of filesystem corruption.

oke so what you are saying is i make a seperate partition for ubuntu and install it there.. but dont u need 2 partitions to install ubuntu? im confused now.. >.> .. cause last time it asked for two and i ended up formatting a drive.. and what should i choose Fat,NFS (im a complete noob, sorry guys) which ones best or the fastest..

---

### Post by COMECON on 2012-12-13
I definitely recommend you using Xubuntu, if you want to customizate your desktop. In the few weeks I've been working with it, it has been from [this](http://i1285.photobucket.com/albums/a599/tomeuari/Xubuntu-Desktop-1.png) (oldie gnome2 style) to [this](http://i1285.photobucket.com/albums/a599/tomeuari/XmasCap.png) (docky style, actual). You can see more screenshots of my desktop, if you're interested, on [thread=2089919]this thread[/thread]. Precisely, my first post on that thread was the start of my love with XFCE... :P

Catbuntu

PS: Consider also Kubuntu and Lubuntu as good flavours for customizating. Of course, that's just a personal prefference... But I preffer XFCE because it's between the ultra-lightweight of LXDE and the... heavyness of KDE.

PS2: The linux partitions are usually in the ext4 format. You only need one partition, where Ubuntu will be installed, and a swap partition, with the swap filesystem and more or less your ammount of RAM of size.

---

### Post by Lars Noodén on 2012-12-13
For your ubuntu partition, you should stick with the EXT4 or EXT3.  FAT and NTFS are unsuitable for Linux systems and questionable in general.  

About the desktop environment, you have another vote for KDE (or Kubuntu) here.  It is the most customizable of the desktop environments.

---

### Post by CorruptDNA on 2012-12-13
> **Lars Noodén said:**
> For your ubuntu partition, you should stick with the EXT4 or EXT3.  FAT and NTFS are unsuitable for Linux systems and questionable in general.  

About the desktop environment, you have another vote for KDE (or Kubuntu) here.  It is the most customizable of the desktop environments.

oke so i will be installing ubuntu.. after i finish installing, how am i supposed to install kubuntu?

---

### Post by addegsson on 2012-12-13
Kubuntu!

---

### Post by CaptainMark on 2012-12-14
> **CorruptDNA said:**
> oke so i will be installing ubuntu.. after i finish installing, how am i supposed to install kubuntu?If you want the whole Kubuntu experience including their themes and applications (recommended) ```
sudo apt-get install kubuntu-desktop
```if you want just vanilla kde and to customise it yourself```
sudo apt-get install kde-standard
```

---

### Post by CorruptDNA on 2012-12-15
> **CaptainMark said:**
> If you want the whole Kubuntu experience including their themes and applications (recommended) ```
sudo apt-get install kubuntu-desktop
```if you want just vanilla kde and to customise it yourself```
sudo apt-get install kde-standard
```

thanks a lot bro :) .. one more question if its not a lot for you guys.. been a big help.. 
how do u customize grub to originally load windows 7 unless i press a specific button to choose the different os's installed..

Update: i tried to install kubuntu, but the terminal response was:
Could not find package or something like that.. >.> 

myname@myname-laptop:~$     sudo apt-get install kubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package kubuntu-desktop

i think i fixed this problem by running sudo apt-get update
sudo apt-get upgrade
will post when i finish installing kubuntu

---

### Post by offgridguy on 2012-12-15
> **haqking said:**
> you can use ubuntu, they are talking about a different de, you can have multiple de's installed in any version of ubuntu all providing different levels of configuration, i personally prefer kde which is highly configurable and customizable
+1,

---

### Post by cmcanulty on 2012-12-15
Try classic you can customize it just like gnome 2 or ubuntu before Unity
[http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed]("http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed")

---

### Post by silverhaze06 on 2012-12-16
You can also try the "tweak tool" package and "ubuntu-tweak" to customize unity. I prefer using this because from my experience installing a ton of different DE's tend to slow my computers down after a while and increase the chances of programs crashing. I've done it a few times and just ended up doing a fresh re-install of ubuntu. And with these it makes it much easier to use themes, icons and shells from [gnome-look.org]("www.gnome-look.org").

---

### Post by MoebusNet on 2012-12-16
To start with a minimal install and go from there try:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by Mopar1973Man on 2012-12-16
Since all flavors of Ubuntu are basically the same core just different DE's I started with Ubuntu 12.04 got it to run the way I wanted. Then when I got spare time I started tweaking the desktop, adding, removing, trying different apps and setting. So now I've got a mix of Lubuntu and Ubuntu and pretty happy with the setup. All I can say is research and try thing that's the only way to learn which you like the best.

---

### Post by Gaygerbil on 2012-12-16
You could probably get what you're wanting with Xubuntu, Lubuntu, Linux Mint, etc. I'd recommend Linux Mint for you honestly seems like you're just tired of Unity and want customization which it has.

---

