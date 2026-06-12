---
title: "Some questions from a new Xubuntu user"
date: 2007-01-19
forum: General Help
---

### Post by Z__ on 2007-01-19
Hi, 

I just installed Xubuntu Edgy and got most things working, I love it.

1- Directory structure is a little different from other distros. Where should user applications be installed and applications available to all user be installed? It would be great if there is a link that explains directory structure in Ubuntu. I install some programs myself and I need to put them in correct locations (not using app-get since it does not have latest versions).

2- When apt-get is used to install a new package. Where does it install it? For example I checked for firefox but it there are files all over the place. I'm trying to understand how it works, I thought in Linux all application files are in one folder.

3- How can I modify services (daemons) and view startup items

4- How do I access my USB devices (hard disk, mp3 player, etc...)

5- I work from home sometimes and I need to connect to my work's VPN. Is it possible to use Cisco VPN Client for Linux on Ubuntu? [Some info **about **it]("http://www.cisco.com/univercd/cc/td/doc/product/vpn/client/rel_4_8/48client.htm#wp1495572")

6- When I use command uname -r at the end of my kernek type it says generic. Is that fine? Would it be better if I get some other kernel that would work better for my hardware (Intel Xeon CPU, 2.5 GB  RAM)

7- How can I optimize my system like things to enable/disable or uninstall.

Thanks for all of your help.

---

### Post by Littleweseth on 2007-01-19
1 ) Usually, you won't directly 'install' apps that you download from the internet - in the case of prepackaged software like .deb files and .rpm's, you'll use sudo dpkg -i <package.deb> and sudo alien -i <package.rpm> to start the installation, and the system will take care of putting the files where they need to go.

In the case of programs distributed as source, you'll usually unzip them somewhere, then run a few commands that compile the app and distribute the necessary files around your system, Most source packages have a 'readme' file inside that details the process.

2 ) There is no 'one install place'. Different programs end up in different places, and different bits of programs end up in various folders according to what function they have. For example, the documentation might end up in one folder, the sound files might show in in another, etc.

3 ) Use bootup manager (sudo aptitude install bum.)

4 ) The directory /media/ links to all your devices, or you can find the 'Computer' equivalent in xubuntu (sorry, I don't have an xubuntu system to hand.)

6 ) You can install a more specific kernel with synaptic. Kernels live in the 'base' section of the repositories.

7 ) Use BUM as above to edit startup services, and use Synaptic to uninstall packages you're never going to use. Good candidates for removal are the various internationalisation packages you're not going to use, and the international fonts.

Hope this helps.
-lws

---

### Post by Dave54 on 2007-01-19
Hello.

> It would be great if there is a link that explains directory structure in Ubuntu.
If you follow the links from [https://help.ubuntu.com/community/]("https://help.ubuntu.com/community/"), all sorts of information is revealed. You just have to find it. :wink: 

> How can I modify services (daemons) and view startup items
You can go to System > Preferences > Sessions. Bum may be better, I've never tried it.

> How do I access my USB devices (hard disk, mp3 player, etc...)
Most USB Devces will have an icon on the desktop when connected (at least in ubuntu)

Have fun!
-Dave

---

### Post by rasgryphon on 2007-01-20
> **Z__ said:**
> 
5- I work from home sometimes and I need to connect to my work's VPN. Is it possible to use Cisco VPN Client for Linux on Ubuntu? [Some info **about **it]("http://www.cisco.com/univercd/cc/td/doc/product/vpn/client/rel_4_8/48client.htm#wp1495572")
Thanks for all of your help.

You can use the linux version of the cisco vpn client, if you search these forums i have seen a few tutorials for it.  Another option is to use vpnc, which is an open source vpn client and works just as well.  

```
sudo apt-get install vpnc
```

---

