---
title: "Compile hell - Tcl/Tk problems"
date: 2007-04-22
forum: General Help
---

### Post by oomingmak on 2007-04-22
I've been trying to find out how to install Tcl/Tk  for the last few hours and I'm getting nowhere. 

:frown: 

I first trawled the net for ages trying to find some clear install instructions, but nothing seemed to apply (they were all for other platforms or distros that were too different from mine for me to be sure that I'd be doing it correctly). I'm using 7.04 final. 

Eventually I found a post about aMSN that had some more relevant Tcl/Tk install instructions in it, so I tried to followed those, but I keep getting the same error at the end of the compile: 

```

Installing libtcl8.5.so to /usr/lib/
cp: cannot create regular file `/usr/lib/#inst.27808#': Permission denied
mv: cannot stat `/usr/lib/#inst.27808#': No such file or directory
chmod: cannot access `/usr/lib/libtcl8.5.so': No such file or directory
make: *** [install-binaries] Error 1
```

The compile command that they said to use was:

```
./configure --prefix=/usr; make; make install
```

I also tried it with sudo (just for the hell of it) seeing as the error message said something about chmod and access, but it made no difference.

I'd be grateful for any help because I don't know what to do next. In fact, I don't even know (or care) what Tcl/Tk is, all I want to do is open a few of my apps using keyboard shortcuts (which you wouldn't think was too much to ask, would you?). But strangely it seems that you need use a separate program to assign keyboard shortcuts to programs in Ubuntu, so I went looking for one and found xbindkeys. But the xbindkeys page says that it needs this Tcl/Tk thing (not that they bother to explain to you how to install it) and Tcl/Tk refuses to compile without errors.

---

### Post by hardyn on 2007-04-22
its a backwads way of doing things, but there is an install script for aMSN that also installs and compiles Tcl/Tk... might be an "around the block" method of doing it?
unless you need the newest version... i think it is also in the repos.

---

### Post by amohanty on 2007-04-22
> Installing libtcl8.5.so to /usr/lib/
cp: cannot create regular file `/usr/lib/#inst.27808#': Permission denied
mv: cannot stat `/usr/lib/#inst.27808#': No such file or directory
chmod: cannot access `/usr/lib/libtcl8.5.so': No such file or directory
make: *** [install-binaries] Error 1

1. Thats becuase you are probably trying to do a **make install** without an **sudo**. Try **sudo make install**

2. Why didnt you use synaptic to install xbindkeys. Or from the command line try:

sudo apt-get install xbindkeys

That will automatically install the required libraries.

> I also tried it with sudo (just for the hell of it) seeing as the error message said something about chmod and access, but it made no difference.

Can you post the exact message?

Finally:

> all I want to do is open a few of my apps using keyboard shortcuts (which you wouldn't think was too much to ask, would you?)

I am not sure about Fiesty (I am currently on edgy), seems unlikely its not there but is there a menu item: System->Preferences->Keyboard Shortcuts

HTH
AM

---

### Post by oomingmak on 2007-04-22
Thank you for your reply amohanty.


> **amohanty said:**
> 1. Thats becuase you are probably trying to do a **make install** without an **sudo**. Try **sudo make install**
I did ***try*** to use sudo, but I am new to linux, and I'm sure you can appreciate how bewildering all these strange commands are to a newbie.

What annoys me, is that people keep creating these supposedly "step-by-step" guides (with quoted code for you to cut and paste) but then they go and miss bits out and just expect you to know how to fix it. If I knew how to do that, then I wouldn't be cutting and pasting from a guide in the first place.

The following link

[http://amsn.sourceforge.net/wiki/tiki-index.php?page=Installation+Instructions](http://amsn.sourceforge.net/wiki/tiki-index.php?page=Installation+Instructions)

says use this command:
```
./configure --prefix=/usr; make; make install
```

When it didn't work, I looked at the text of the error message that resulted and it said something about chmod (which I thought might be something to do with permissions). So that's when i tried sudo, but I used it wrongly and put it at the beginning of the line instead of in front of the **make install**. I only put it at the beginning because most of the time (like when editing xorg.conf or using apt-get) sudo goes at the front. Of course, if the instructions had been quoted correctly in the first place, then this issue would have never arisen.

I've now re-run the commands with sudo in the right place and both of them have compiled without errors, but I still can't lauch the xbindkeys utility using:
```
xbindkeys_show
```


I get the error message:  

exec: 3: wish: not found


 
[quote=amohanty]2. Why didnt you use synaptic to install xbindkeys. Or from the command line try:

sudo apt-get install xbindkeys

That will automatically install the required libraries.[/quote]
I **did** use apt-get, but it doesn't install Tcl/Tk which is needed for the veiwer utility. 



[quote=amohanty]
I am not sure about Fiesty (I am currently on edgy), seems unlikely its not there but is there a menu item: System->Preferences->Keyboard Shortcuts[/QUOTE]
Nope, that only has options to launch web browser and email client (oh and the calculator). The rest of the settings are for things like window and workspace management. there is no facility to open things like OpenOffice apps, Gedit (or pretty much anything else) without an add-on. A pretty major oversight in my opinion.

I've got a step closer thanks to your help (now that the files have compiled) but I've now spent nearly 7 hours trying to get something to work that would have taken 10 seconds to do on Windows.

---

### Post by amohanty on 2007-04-22
Just out of curiosity, was there something that gaim could not provide that made you choose aMSN?

> What annoys me, is that people keep creating these supposedly "step-by-step" guides (with quoted code for you to cut and paste) but then they go and miss bits out and just expect you to know how to fix it. If I knew how to do that, then I wouldn't be cutting and pasting from a guide in the first place.

I would suggest that you _never_ cut and paste without understanding what you are doing. A used book on linux would be a great start, tldp.org is a huge repository and there are umpteen tutorials on linux online. The reason I suggest that is, because:

1. linux has various flavors, its not guaranteed that what you cut and paste will _always_ have the same result no matter what. The flavors are not very different, but different enough to cause trouble to the uninitiated.

2. if you don't understand what you are doing, the likelihood of causing severe damage is very high. 

> I've got a step closer thanks to your help (now that the files have compiled) but I've now spent nearly 7 hours trying to get something to work that would have taken 10 seconds to do on Windows.

I can understand that you are quite frustrated, but that would be considered flame bait. I am going to attribute it to sleeplessness :) and not respond. Please keep in mind, linux is not windows. Also keep in mind that you have invested _years_ 'learning' windows. aysiu has some nice essays on the topic [http://www.psychocats.net/essays/index.php](http://www.psychocats.net/essays/index.php)

Try installing xbindkeys-config and see if that meets your needs. That is a GTK based program which has a GUI to configure xbindkeys.

> I get the error message:

exec: 3: wish: not found


wish is the tcl/tk windowing shell (I think), I havent used that in a while. Try installing tk8.4 (i think it will automatically install tcl8.4 too)

> Nope, that only has options to launch web browser and email client (oh and the calculator). The rest of the settings are for things like window and workspace management. there is no facility to open things like OpenOffice apps, Gedit (or pretty much anything else) without an add-on. A pretty major oversight in my opinion.

This is surprising, you should have a hell of a lot more menu items if you did a standard desktop install. What version are you running?

HTH
AM

---

### Post by oomingmak on 2007-04-23
> **amohanty said:**
> Just out of curiosity, was there something that gaim could not provide that made you choose aMSN?
I am _not_ installing aMSN, it was the only reference that I could find that contained instructions on how to install Tcl/Tk. So I was just using the relevant parts of the instructions as a guide.

> **amohanty said:**
> 
I would suggest that you _never_ cut and paste without understanding what you are doing.
If that were the case then I'd never have been able start using Linux (I suspect the same holds true for a lot of other people too). One of the very first things I had to do when I first installed Ubuntu was to edit Grub (my MBR got trashed by an install of 6.06LTS) and then I had to edit xorg.conf. I didn't understand the layout of grub or menu.lst or know what sudo was, but if I hadn't done these things, then I wouldn't have even be able to boot or have a working desktop resolution for my 24" widescreen monitor. You've got to start somewhere, and over time I came to understand about elevating privileges to perform certain actions (hence sudo and gksudo). But when you can't get past the splash screen (because X keeps hanging) then the last thing you want to do is to have to go off for a few weeks to start studying bash commands from a book (while your computer sits there unbootable).

> **amohanty said:**
> 
2. if you don't understand what you are doing, the likelihood of causing severe damage is very high.
That's what disk images are for. I am learning Linux, all my Ubuntu installs are test installs that are "trashable". If they weren't, then I wouldn't be doing things like trying to install alpha software such as Beryl.

> **amohanty said:**
> 
I can understand that you are quite frustrated, but that would be considered flame bait. I am going to attribute it to sleeplessness :) and not respond.
Considered "flame bait" by whom? I ***_can_*** assign hotkeys in Windows for Start menu items in 10 seconds (that's the truth), and there ***isn't*** any facility to assign keyboard shortcuts for Gnome's Application menu items (e.g. OpenOffice, Gimp etc.) in Ubuntu (that's also the truth). Go and check for yourself if you don't believe me (Ubuntu Desktop install v7.04 final). I don't understand how that could be considered 'flame bait' :confused: 

> **amohanty said:**
> 
Also keep in mind that you have invested _years_ 'learning' windows.Who said I've invested years of learning into Windows? We are talking about assigning a keyboard shortcut here, not something like recompiling the kernel. It certainly doesn't take 'years' to discover how to assign shortcuts in Windows, because it's right there in front of you on the context menu of each item. Surely the fact that I am trying to find a solution by installing xbindkeys shows that I'm persevering (rather than going off in a huff).

> **amohanty said:**
> 
Try installing xbindkeys-config and see if that meets your needs. That is a GTK based program which has a GUI to configure xbindkeys.
Thank you.    :) 

Now this sounds like the perfect solution! I don't know how I had not heard of this before. :oops:  The whole Tcl/Tk fiasco was basically solely for the purpose of getting a GUI for xbindkeys to view the key assignments that had been made. I did not see xbindkeys-config mentioned anywhere on the xbindkeys web site (maybe because it's done by a different developer). The only thing mentioned was xbindkeys_show (which the developer said required the installation of Tcl/Tk) ....................... and that's where we came in.

Thanks again for the heads up about xbindkeys-config, I'll try it later today.

:cool:

---

