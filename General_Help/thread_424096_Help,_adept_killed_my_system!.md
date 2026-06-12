---
title: "Help, adept killed my system!"
date: 2007-04-26
forum: General Help
---

### Post by fallingleaf on 2007-04-26
Running Kubuntu Feisty.  I was having trouble with xine, and I ran xine-check.  It said I needed xine-libs installed so I went to adept and searched xine.  Found a lot of things but wasn't clear which one I needed and I clicked several of them to install, clicked apply, and it went and removed three hundred plus packages!  I tried reinstalling kubuntu-desktop, but next time I booted I got a black screen with a flashing cursor, no GUI.

---

### Post by Iarwain ben-adar on 2007-04-26
You say you tried reinstalling kubuntu-desktop,
what errors did you get?


Iarwain

---

### Post by fallingleaf on 2007-04-26
I didn't get any errors

---

### Post by Iarwain ben-adar on 2007-04-26
Can you try to install it via Command Line?
(login, and then type "sudo aptitude install kubuntu-desktop" without the quotes)


Iarwain

---

### Post by fallingleaf on 2007-04-26
OK, it seems the problem was my xorg.conf.  I thought I had put it back to the original version that was installed, but it still had the section "extensions" with "composite disable" for using fglrx driver for ATI.  when I ran startx from cli it gave a parse error.  I commented out the section and now I am back on.  

In the process of trying to reinstall stuff I ended up installing a whole bunch of stuff I don't need: extra language packs, gnome desktop etc.  Is there some simple way to get things back to normal without losing all my settings?  Is there some way to prevent adept from randomly uninstalling my whole system?

---

### Post by Iarwain ben-adar on 2007-04-26
Well, there is a very simple way to prevent adept from such a thing:
Look at what it says about packages to delete ;)

It is good you found what your error was. To get your system back to normal, i don't know.
You can try to uninstall all the stuff you don't need though.. A tip for easier removal,
use aptitude instead of apt-get (if you use command line). Don't know a way to make removal of meta-packages easier in GUI :s

Second tip,
use the command line (i use yakuake to type in codes easily)
```
sudo aptitude install yakuake
```

To install stuff via CLI (Command Line Interface):
```
sudo aptitude install 'something'
```
(Replace 'something' with the stuff you want to install, but w/o the "", and you can auto-complete the package name with the TAB-key)

To search for a package, 
```
apt-cache search name
```
(Replace name with a word you want to search for)

These are things i use, and it helps me keeping my system doing what i want (Adept doesn't show me enough info, and is too slow for my taste)


Iarwain

---

### Post by fallingleaf on 2007-04-26
Thanks Iarwain,

 I generally use command line to install if I know the package name, but for browsing for other packages Adept is nice.    Problem is, unless you click preview, it doesn't warn you what it is about to do.  I was using Synaptic with Gnome on Edgy, but I changed to KDE when I upgraded to Feisty.  I find the search feature in Adept to be much quicker and easier to use than Synaptic.  But Synaptic always tells you what it's going to do before it does it.

Actually, I had a similar  thing happen using apt-get before.  I got in the habit of saying yes to whatever it asked me and it uninstalled a bunch of stuff.  I hit Ctrl-C in the middle of it in a panic, probably made it worse.   It took a while to get back to normal.

---

### Post by Iarwain ben-adar on 2007-04-27
No problem ;)

Just remember that you can search for packages in command line, and auto-complete the name by pressing the TAB-key 


Iarwain

---

