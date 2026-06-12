---
title: "TuxGuitar on Gutsy"
date: 2007-12-18
forum: General Help
---

### Post by sajro on 2007-12-18
Hello people.

I"m trying to tab out a few of my band's songs in TuxGuitar. Well, I would if I had TG installed. I can't figure out how to install it.

I downloaded the Ubuntu binary .deb and after running it through gdebi (and gdebi-gtk not that it makes a difference :razz: ), nothing happens. apt-cache has never heard of tuxguitar and ofcourse neither has my menu.

How do I install this program on Gutsy so I can :guitar: ?

Thanks in advance from a newb.

---

### Post by jesushero on 2007-12-18
Hey, haven't heard of TuxGuitar before, but installing stuff that's not on synaptic package manager is always harder. Package Manager has 7 Guitar Tab programs that you can download and install automatically. 

If you insist on using TuxGuitar, either double click on the .deb file which should launch an installer, or use the terminal, sudo dpkg *the name of the file*.deb which should do a command line install. 

Or at least I hope so... Good luck!

---

### Post by sajro on 2007-12-18
Okay I'm working on it. If it doesn't work I'll use one from Synaptic.

TG should put a repository on their site for Ubuntu/Debian/Debian-based OS users (and even the evil rpm).

---

### Post by www.rzr.online.fr on 2008-03-03
> **sajro said:**
> Hello people.

I"m trying to tab out a few of my band's songs in TuxGuitar. Well, I would if I had TG installed. I can't figure out how to install it.

I downloaded the Ubuntu binary .deb and after running it through gdebi (and gdebi-gtk not that it makes a difference :razz: ), nothing happens. apt-cache has never heard of tuxguitar and ofcourse neither has my menu.

How do I install this program on Gutsy so I can :guitar: ?

Thanks in advance from a newb.



Please can you test version 1.0 see [http://rzr.online.fr/q/tuxguitar](http://rzr.online.fr/q/tuxguitar)
I'll sync it to ubuntu then

---

### Post by habana on 2008-03-03
Hello folks

Thanks for this pointer to Tuxguitar - it's just what I've been looking for. I just downloaded the Ubuntu binary package, allowed the installer to find the dependencies and the program runs fine.

Hope it works for you Sajro

---

### Post by roofer on 2008-03-11
I just downloaded the 1.0 rc2 package for ubuntu 7.10.  I get the following error...

Java sound api cannot be loaded.

I did allow for the dependencies to be added and the program starts, just no sound.  I have java 1.5.0 loaded.  Is there another package dependency I missed?  Or, possibly someone knows of a quick fix.  If not, I'll try something esle, but tuxguitar looks promising.

Thanks,

-roofer

---

### Post by habana on 2008-03-11
> **roofer said:**
> I just downloaded the 1.0 rc2 package for ubuntu 7.10.  I get the following error...

Java sound api cannot be loaded.

I did allow for the dependencies to be added and the program starts, just no sound.  I have java 1.5.0 loaded.  Is there another package dependency I missed?  Or, possibly someone knows of a quick fix.  If not, I'll try something esle, but tuxguitar looks promising.

Thanks,

-roofer
Im a bit of a noob but are you sure you have java running - not just a plug-in for Firefox? Check you have java-common downloaded via Synaptic

---

### Post by ibuclaw on 2008-03-11
Hi, I got it to work.

I used the general bin installer, installed it in my /home/Public folder, needed the Java gm soundbank though. I found it [here.]("http://java.sun.com/products/java-media/sound/soundbanks.html")

Then when you load up TuxGuitar, go into "Tools>Plugins>Java Sound API>Configure" and select "Use Custom Soundbank".
Lastly, choose the .gm file you downloaded, restart and it works just fine.

I recommend the mid-sized gm file, it's not a brilliant sound that it makes, but it's the better of the three. If anyone knows where to get any others, I'll be greatly thankful.

Iain

---

### Post by ibuclaw on 2008-03-15
I've gotten the Ubuntu Package for TuxGuitar rc2 to work on my system too!

I think it's because they use OSS???

Anyhow, after installing, edit the gnome (or kde/xfce/etc) menu and change the TuxGuitar command from "tuxguitar" to:
```
 aoss tuxguitar 
```
Nothing else required!
Hope this helps people experiencing problems with it. I'll see if I can request this to be fixed.

Regards
Iain

---

### Post by LitusMayol on 2008-04-30
Hi everyone!

I've installed a new Ubuntu and then performed it to UbuntuStudio. I've installed TuxGuitar with the graphical installer. It appears in the main menu as I expected. But when I start it nothing happens. Just nothing if i do "gksu tuxguitar" happens this: 
```
litus@UbuntuStuio:~$ gksu tuxguitar
litus@UbuntuStuio:~$ 
```

So... Nothing at all. I've Ubuntu in another partition since 2 years and there I've installed TuxGuitar and it runs without any problem. 

Can anyone help me?



Thanks, and pardon the newbie.

---

### Post by www.rzr.online.fr on 2008-05-01
> **LitusMayol said:**
> Hi everyone!

Can anyone help me?
.

Install snapshot version of TG : 
  [http://rzr.online.fr/q/tuxguitar](http://rzr.online.fr/q/tuxguitar)

---

### Post by Blastomorpha on 2008-05-04
I've the same LitusMayol's problem!
What's this snapshot version?

---

### Post by www.rzr.online.fr on 2008-05-14
> **Blastomorpha said:**
> I've the same LitusMayol's problem!
What's this snapshot version?

svn version updated weekly at least

---

### Post by LitusMayol on 2008-05-15
> **www.rzr.online.fr said:**
> Install snapshot version of TG : 
  [http://rzr.online.fr/q/tuxguitar](http://rzr.online.fr/q/tuxguitar)

Thanks man! ;)
done!

---

