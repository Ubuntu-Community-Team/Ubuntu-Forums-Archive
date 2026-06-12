---
title: "Is there way to move the Unity launcher to the bottom?"
date: 2012-11-18
forum: General Help
---

### Post by CProgramming on 2012-11-18
Damn, Ubuntu is so customizable , but such a simply option doesn't exist?? 

Guys, Is there a way to move the Unity launcher to the bottom of the screen, under Ubuntu 12.04? I search about it a lot. I really thank you. 

(I'm sorry about this writing-style, I'm too much influenced from american movies ^^)

---

### Post by Mark Phelps on 2012-11-18
Ubuntu lost its reputation for lots of desktop customization when Unity took over ...

But to answer your question, see the details in the following link:

[http://askubuntu.com/questions/33605/can-i-move-the-unity-launcher]("http://askubuntu.com/questions/33605/can-i-move-the-unity-launcher")

---

### Post by mcduck on 2012-11-18
> **Mark Phelps said:**
> Ubuntu lost its reputation for lots of desktop customization when Unity took over ...
...in most cases due to people not understanding which changes were actually caused bu Unity, and which by Gnome's decisions in the Gnome2 to Gnome3 transition (and of course the simple fact that the changes in GTK and desktop components mean that many customization tools need to be rewritten).
> **Mark Phelps said:**
> 
But to answer your question, see the details in the following link:

[http://askubuntu.com/questions/33605/can-i-move-the-unity-launcher]("http://askubuntu.com/questions/33605/can-i-move-the-unity-launcher")
Keep in mind that those instructions, and the PPA repository mentioned in them, are only for Ubuntu 11.10.

---

### Post by CProgramming on 2012-11-18
> **mcduck said:**
> ...in most cases due to people not understanding which changes were actually caused bu Unity, and which by Gnome's decisions in the Gnome2 to Gnome3 transition (and of course the simple fact that the changes in GTK and desktop components mean that many customization tools need to be rewritten).

Keep in mind that those instructions, and the PPA repository mentioned in them, are only for Ubuntu 11.10.

As you said so is there workaround for 12.04??

---

### Post by NikTh on 2012-11-18
> **CProgramming said:**
> As you said so is there workaround for 12.04??

Hi , 
there is not a workaround for 12.04 . A similar conversation took place few months ago here in forum. Take a look => [http://ubuntuforums.org/showthread.php?t=1976480](http://ubuntuforums.org/showthread.php?t=1976480)

Thanks

---

### Post by philinux on 2012-11-18
The OP could use something like Docky instead.

---

### Post by raja.genupula on 2012-11-18
> **philinux said:**
> The OP could use something like Docky instead.

Yes thats the better way rather than playing with unity .

---

### Post by mc4man on 2012-11-18
haven't tried docky in quite some time as unity launcher on the side is ok here.
Have from time to time tried out plank, both in unity & gnome-shell (more so in GS  because of below
The latest works pretty good, supports quicklists & window lists
[https://launchpad.net/~ricotz/+archive/docky](https://launchpad.net/~ricotz/+archive/docky)

---

### Post by philinux on 2012-11-18
> **mc4man said:**
> haven't tried docky in quite some time as unity launcher on the side is ok here.
Have from time to time tried out plank, both in unity & gnome-shell (more so in GS  because of below
The latest works pretty good, supports quicklists & window lists
[https://launchpad.net/~ricotz/+archive/docky](https://launchpad.net/~ricotz/+archive/docky)

That's the one Plank. Lol :p

---

### Post by mc4man on 2012-11-23
> **philinux said:**
> That's the one Plank. Lol :p
Decided to have a bit of a fool around in 13.04 with plank in unity
Actually starting to like better than the unity launcher, reasons repeated - 
Dodge
Window lists
Supports quicklists
Supports DnD (though doesn't grey like unity launcher
Min on left click
Scroll on icon with multiple windows open to focus..

Some config isn't well exposed though looking thru ~/.config/plank/* is informative

Added a first try at a Dash/Dash lens icon, may be other ways but xdotool works pretty good  - screen

---

### Post by rickyrockrat on 2013-01-15
So having heard such awful things about unity, I decided to just forego using it until now, since I need to develop an appindicator. Did we just go back in time and become worse than Microsoft? What the heck were they thinking!?? I find it astounding that I can't move the launcher without major contortions.
The rest of my comments are unprintable, other than why anyone would want to use the interface? 

To the original op: You can install gnome-session-fallback, or one of the other window managers as suggested.  I personally use xfce4 (which is essentially Xubuntu), and have used it ever since KDE went to their plasma desktop.  I just hope xfce4 doesn't decide to re-write their interface, since it is completely configurable, and quite easy to do so. It is one of those interfaces that doesn't get in the way of getting real work done.

Cheers.

---

### Post by meteorrock on 2013-01-19
~~~~~~~~~~~~~Working workaround~~~~~~~~~~~~


Just download Docky. You can autohide that launcher in the system settings >> appearance >> behavior tab. It will still be there but out of the way. To bring it back, just hit your superkey, the windows emblem key on your keyboard. It will appear for a few seconds to get into the main default launcher that comes by default with Ubuntu 12.10.  Here is the link for docky,  if you want to take a look over that app. [http://wiki.go-docky.com/index.php?title=Welcome_to_the_Docky_wiki](http://wiki.go-docky.com/index.php?title=Welcome_to_the_Docky_wiki)

~~~~~~~~~~~~~~~~

To get into the options on docky,  as it will install itself at the bottom of your screen running the code below,straight after its done after you input that code below, just hit on the anchor icon, there are options in there to change your docky to a taskbar with glass effects if you want. It is really customizable out of the box.  It even starts up with what apps you had in your launcher by default. It can not get any simpler or more beautiful. It even has an autohide feature if you want in its options for a full screen experience and ACTUALLY works when you mouse over it, unlike the default launcher with Unity. 

It even comes with a "Window Dodge" option, where it will appear when you exit out of your web browser, and hide itself when you open up your web browser. Quite the amazing program. Great job by the developers for that app, I say.

Here is the terminal code for docky. 

```
sudo add-apt-repository ppa:docky-core/stable 
``````
  sudo apt-get update 
``````
sudo apt-get install docky 
```With the ppa, it will update with sudo apt-get update. 

I just tried it out and it works good. That launcher on the  left side is just a big mistake with that unity interface.

---

