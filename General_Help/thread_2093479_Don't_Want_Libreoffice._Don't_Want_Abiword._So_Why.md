---
title: "Don't Want Libreoffice. Don't Want Abiword. So Why Force Me?"
date: 2012-12-10
forum: General Help
---

### Post by whitecat23 on 2012-12-10
Hello, I don't want either LibreOffice or Abiword on one of my Ubuntu (12.04) boxes. When I try to uninstall LibreOffice then apt-get automatically installs Abiword. Of course, Synaptic and Aptitude do the same, while dpkg simply refuses to remove several core LibreOffice packages because of certain ridiculous dependencies based off Gnome. This just doesn't seem right. I should be able to choose which, if any, office suite I want to use. So if anyone can please help - how do I get rid of LibreOffice without getting stuck with Abiword?

---

### Post by agxryt on 2012-12-10
> **whitecat23 said:**
> Hello, I don't want either LibreOffice or Abiword on one of my Ubuntu (12.04) boxes. When I try to uninstall LibreOffice then apt-get automatically installs Abiword. Of course, Synaptic and Aptitude do the same, while dpkg simply refuses to remove several core LibreOffice packages because of certain ridiculous dependencies based off Gnome. This just doesn't seem right. I should be able to choose which, if any, office suite I want to use. So if anyone can please help - how do I get rid of LibreOffice without getting stuck with Abiword?

Install another Office Suite? 

I know the same happens with browsers. You HAVE to have a browser. I had read why a little while back, but I'm not really sure anymore. I'm guessing it's the same with an office suite.

---

### Post by HermanAB on 2012-12-10
First of all, why worry about it?  Having more software on your computer ready to go, doesn't magically slow it down or some such.  There are thousands of programs installed on your system in /usr/bin that you may never even know about, nevermind ever use.

I would just remove the entries for LibreOffice and Abiword from the menus, for the simple reason that the use of shared libraries makes removing any large program risky, since it may remove something that another unrelated program needs.

---

### Post by cariboo on 2012-12-10
> **whitecat23 said:**
> Hello, I don't want either LibreOffice or Abiword on one of my Ubuntu (12.04) boxes. When I try to uninstall LibreOffice then apt-get automatically installs Abiword. Of course, Synaptic and Aptitude do the same, while dpkg simply refuses to remove several core LibreOffice packages because of certain ridiculous dependencies based off Gnome. This just doesn't seem right. I should be able to choose which, if any, office suite I want to use. So if anyone can please help - how do I get rid of LibreOffice without getting stuck with Abiword?

There are a couple of ways to only install what you want. The first is the [mini.iso]("https://help.ubuntu.com/community/Installation/MinimalCD") or remove the *-desktop meta package. The desktop meta packages include all the depends and recommends needed in order to install the default desktop system for whatever version you are using.

---

### Post by whitecat23 on 2012-12-10
Installing Abiword or Libreoffice is not a solution when I don't want them. The thing is this: Ubuntu seems to have, for some inexplicable reason, created some very fundamental dependencies to a particular office suite. The Gnome Desktop relies on having either of those two programs around when they have absolutely nothing to do with the operating system. I was never a fan of Libreoffice, and Abiword is just a piece of work. My philosophy is to pare everything down to an absolute minimum and build up using only what I need.
Don't get me wrong, Ubuntu is a good OS - but they have made a really stupid decision here. If they force this on us when will it end? OpenOffice 3.4 is not only the best office suite for Linux, but a good office suite by any standard. I use it by choice and I still wouldn't want that forced on me or on anyone else. Windows doesn't force an office suite down my throat (you can uninstall MS Office if you don't like it - I have), so why does Ubuntu feel it has to control that aspect of my experience? I thought Ubuntu was about choice...
An OS can function just fine without a word processor, a web browser, or whatever. It all depends on what you want to do with it. Sure, I can just leave it there and ignore it but that's not my point. If I want something off my computer then Ubuntu should provide a way for me to do that. It's not like LibreOffice is a critical system component.
Still would like to know how I can get this done. Thanks for the replies, BTW. I appreciate your viewpoint but disagee with getting locked into a vendor. That's one of the main reasons I didn't consider Windows 8 or OS X!
Is a Canonical employee listening?

---

### Post by bfmetcalf on 2012-12-10
You could switch to a distro like ArchLinux, that way YOU control exactly what goes onto your system as it only installs the base OS and you build on it from there.

---

### Post by lykwydchykyn on 2012-12-10
I don't seem to have this problem on my system, but my guess is that some big metapackage like ubuntu-desktop or desktop-base depends on an office suite.

Sometimes these situations feel like you are being "forced" but that's not the situation at all.  It can be tricky to get the dependencies just right so that installing and removing packages do "the right thing" consistently, and occasionally you just end up with a weird situation like this.

Probably the thing to do is use synaptic to look at the properties of abiword and check the "dependencies" tab.  Switch the dropdown to "dependants", and this should give you a clue as to which program is requiring abiword.  Looks like ubuntu-gnome-desktop, gnome, xubuntu-desktop, and lubuntu-desktop all require it, so if you've got any of those metapackages installed, you have to uninstall them.

Keep in mind that uninstalling a metapackage will mark all its dependencies as auto-removable, so you need to mark those as manually installed to make sure you don't end up losing your desktop.

Seems like a big deal to go through, but like I said it can be a tricky dance to make sure packages behave like people think they should.

---

### Post by houseworkshy on 2012-12-10
The post about things depending on other things and the one suggesting  using the mini iso are both valid.  I've had a couple of experiances  involving this.  In one I wanted to remove the weather function and it  wanted to drag the entire desktop with it.  In another I wanted to play a  fairly graphically rich desktop game ( 0 ad ) on a machine with 1,8 gig  ram and it was stuttering a bit, so I booted to the comand line  thinking to free up some ram and improve performance.  On trying to run  it from there it simply wouldn't go because it needed X.  
If the  problem is resources you could try running whatever it is that you want  to run from the command line and see if it goes before trying the mini  iso.  
Another choice would be to boot into a lighter distro than  ubuntu, slitaz ( [http://www.slitaz.org](http://www.slitaz.org) ) and antiX  (  [http://antix.mepis.org/index.php?title=Main_Page](http://antix.mepis.org/index.php?title=Main_Page) ) are both excellent,  for whatever task it is.  If the task is regular duel booting may be an  option.  
My own old machine ( duel core 1,8 gig ram ) is still fine for  most tasks in Ubuntu but not for high end games or media manipulation now that a gig  is used for the gui so I duel boot,  a tweeked Mepris which is as nippy on my machine as Ubuntu 7.04 was,  for the more intensive tasks.

If it's about security then not enableing macros in the word processors helps but they're pretty secure anyway.

Edit
I took so long posting the above I got signed out and missed the last few posts.  Now I understand, you want what is often called a "barebones" system.  Well there are lots of them.  If you use this page
[http://distrowatch.com/search.php](http://distrowatch.com/search.php)
Ticking  "no desktop" will bring up a lot of candidates.  Also differant gui's often have differant software bundles with them and one may suit your needs better,  some of the very light ones have little more than an installer with them.  
Distros are always a meta packges anyway, somewhere between full bells, whistles and dependancies and fully customiseable barebones there will probably be one to suit.

---

### Post by whitecat23 on 2012-12-11
Moving to another distro is not an option given that Ubuntu 12.04 seems to work quite well in other respects. I'll just install the dependencies and hope they make Apache OpenOffice an option in the near future. Since version 3.4 it's been spectacular in my opinion, and I highly recommend it. Thanks all.

---

### Post by NightsShadeQueen on 2012-12-11
I'm pretty sure removing ubuntu-desktop doesn't actually do anything unless you're trying to upgrade between different versions.

Had to remove to get rid of pulseaudio*, didn't notice anything different.

---

### Post by mastablasta on 2012-12-11
> **whitecat23 said:**
>  The Gnome Desktop relies on having either of those two programs around when they have absolutely nothing to do with the operating system. 

COuld it be that documentation or browser connections are connected to libre office or some other office programme that can read the format?!?
 
> 
OpenOffice 3.4 is not only the best office suite for Linux, but a good office suite by any standard. 
libre office was made because development on openoffice stopped or was held back by oracle. so libre office first fixed plenty of bugs from openoffice, improved compatibility with MS office and added a few new features. so yeah there is a difference between them.
 
> 
I use it by choice and I still wouldn't want that forced on me or on anyone else. Windows doesn't force an office suite down my throat (you can uninstall MS Office if you don't like it - I have), so why does Ubuntu feel it has to control that aspect of my experience? I thought Ubuntu was about choice...

Try to uninstall explorer in windows. also remove word pad. see if it's easy.
 
> 
An OS can function just fine without a word processor, a web browser, or whatever. It all depends on what you want to do with it. 
 
you are correct. hence the mini.iso. installs basic os, you add what you need to it and that's it. you can use command line only (no GUI), if you want to. you can also remove drivers and modules you don't need from kernel and compile your own mini kernel that works only on your maschine. so many choices....
 
but that's not the point here. the point is that people want an OS that is easy to install and has many things preinstalled for them (inlducing media player, browser, office suite, emailclient, IM porgramme...). which is why many use Ubuntu (or Mint which has even more stuff preinstalled).

---

### Post by Rebelli0us on 2012-12-11
I'm not crazy about Libreoffice and Abiword is a dog. But what **do** you use instead? I've looked in Synaptic for a basic RTF text editor and haven't found any. It's mostly arcane code editors for programmers.

---

### Post by NightsShadeQueen on 2012-12-11
For me, emacs covers 90% of text editing needs. Latex covers the next 9%. For the last 1%, well, most of the time Google Docs works.

For presentations - well, I'm not a fan of Impress, so I tend to go for the Google presentation. It's nice when I have to present on someone else's computer, too. I can be sure that my formatting won't go wonky.

For spreadsheets - either Google spreadsheets or I just use python (via IDLE).

I still keep Libreoffice on my machine, mostly because it does come in handy every now and then.

---

### Post by Bucky Ball on 2012-12-11
> **whitecat23 said:**
> I'll just install the dependencies ... Thanks all.

Please mark thread as solved from Thread Tools if you're satisfied it is.

---

### Post by vasa1 on 2012-12-11
Very interesting thread! So far I was only aware of the "requirement" to have a browser installed.

---

### Post by agxryt on 2012-12-11
> **whitecat23 said:**
> My philosophy is to pare everything down to an absolute minimum and build up using only what I need.

Then you may want to look at something like gentoo, arch, or slackware.

Ubuntu is designed to be a) usable, and b) usable by non-linux users. Hence why EVERYTHING is already done.

If you're looking to build your own OS, then it's not really for you.

---

### Post by Bucky Ball on 2012-12-11
> **agxryt said:**
> 

If you're looking to build your own OS, then it's not really for you.

Not true. Try the minimal install, mini.iso

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

You call the shots. It only installs the Ubuntu base which is at the bottom of all the Ubuntu flavours, not apps.

---

### Post by agxryt on 2012-12-11
> **Bucky Ball said:**
> Not true. Try the minimal install, mini.iso

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

You call the shots. It only installs the Ubuntu base which is at the bottom of all the Ubuntu flavours, not apps.

I've never heard of this before. I'm actually going to download it right meow!

What's the difference between using this, downloading XFCE and using XFCE applications, and just using lubuntu? Can I still get the same lightweight OS?

---

### Post by zombifier25 on 2012-12-11
> **agxryt said:**
> I've never heard of this before. I'm actually going to download it right meow!

What's the difference between using this, downloading XFCE and using XFCE applications, and just using lubuntu? Can I still get the same lightweight OS?

The difference is that with Lubuntu and Xubuntu, you're still presented with a full system, complete with word processors and stuffs. With Minimal, you can have an extremely barebone and lightweight system, so barebone that you can just slap Openbox and Firefox on the thing and call it a day :P

---

### Post by Bucky Ball on 2012-12-11
> **zombifier25 said:**
> The difference is that with Lubuntu and Xubuntu, you're still presented with a full system, complete with word processors and stuffs. With Minimal, you can have an extremely barebone and lightweight system, so barebone that you can just slap Openbox and Firefox on the thing and call it a day :P

+1. Lol. Exactly.

As I said, you only get the Ubuntu base system, no apps. You could, in fact, then install xubuntu-desktop and it would be pretty much the same as a regular Xubuntu install. So no point!

But, you could install lxde or xfce4 desktop environment and whatever apps you use regularly and call it a day. This will not be a full blown Xubuntu or Lubuntu but your own personal hybrid (as minimal installs are destined to be). ;)

---

### Post by agxryt on 2012-12-11
> **Bucky Ball said:**
> +1. Lol. Exactly.

As I said, you only get the Ubuntu base system, no apps. You could, in fact, then install xubuntu-desktop and it would be pretty much the same as a regular Xubuntu install. So no point!

But, you could install lxde or xfce4 desktop environment and whatever apps you use regularly and call it a day. This will not be a full blown Xubuntu or Lubuntu but your own personal hybrid (as minimal installs are destined to be). ;)

Thanks guys!

Is there a guide somewhere on what exactly is needed? Like OpenBox would be essentially, lightdm, etc. Or are those all pre-installed?

---

### Post by zombifier25 on 2012-12-11
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

Replace icewm with whatever WM you want. After finishing, you can start installing whatever app you want.

---

### Post by agxryt on 2012-12-11
> **zombifier25 said:**
> [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

Replace icewm with whatever WM you want. After finishing, you can start installing whatever app you want.

Thank you!!! :D

---

