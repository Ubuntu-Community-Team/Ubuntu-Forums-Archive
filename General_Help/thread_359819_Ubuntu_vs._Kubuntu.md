---
title: "Ubuntu vs. Kubuntu"
date: 2007-02-12
forum: General Help
---

### Post by WildcatRay on 2007-02-12
Is there an article (or forum thread(s)) somewhere that can help me decide which OS (Ubuntu or Kubuntu) I should install that will provide me the best, robust, and/or most featured-filled installation? I have copies of both available. Though my system is not new, it is a Pentium IV 1.6 GHz, 512kB of RAM with 160 GB Seagate (7200 RPM) HDD, so I don't think I need to worry about limited system resources.

---

### Post by rsambuca on 2007-02-12
You can find multitudes of websites comparing the two, but here is a good starting point.  [[COLOR="Red"]Gnome vs KDE comparison[/COLOR]]("http://www.psychocats.net/ubuntu/kdegnome")

Your rig should run both desktop environments quite easily.  As you hard drive space seems adequate, I would suggest just installing both desktops on your system and login to whichever you choose.  You can install either one, say ubuntu for example, and then install the other with the simple command: sudo aptitude install kubuntu-desktop

Then you can play around with them both and see for yourself which you prefer.

---

### Post by seppo on 2007-02-12
Technically speaking it is 1 OS. Kubuntu is based on Ubuntu. Kubuntu is nothing but Ubuntu with KDE preinstalled as default desktop environment. The base is the same.

I would recommend to install vmware workstation and install Ubuntu. Once you have explored gnome, you can switch to KDE install by simply running:

```
sudo apt-get install kubuntu-desktop
```Exlporing it yourself gives you a better idea what fits you.

---

### Post by FenrisAbraxas on 2007-02-12
> **seppo said:**
> Technically speaking it is 1 OS. Kubuntu is based on Ubuntu. Kubuntu is nothing but Ubuntu with KDE preinstalled as default desktop environment. The base is the same.

I would recommend to install vmware workstation and install Ubuntu. Once you have explored gnome, you can switch to KDE install by simply running:

```
sudo apt-get install kubuntu-desktop
```Exlporing it yourself gives you a better idea what fits you.

Ok, i think i heard too much about this and want to say something:
1.- Installing Ubuntu DOESNT INSTALL GNOME, it install a Debian based system with a DE (Gnome).
2.- you don't install Kubuntu... you install KDE which is a DE not an OS. On top of a Debian Base.
3.-installing KDE over Ubuntu will NOT break anything... if you want to use gnome apps in KDE if u install Kubuntu youll end up with lost of Gnome libraries BUT IT WILL NOT BREAK ANYTHING.
4.-In the remote case installing Gnome and KDE on the same Ubuntu system will make thing to break, don't start to a flame war, but UBUNTU SUX! (And excuse my french).

I have a Gentoo installation since 2005 with KDE, Gnome, Enlightnement (or whatever is spelled), IceWM and FluxBox (uninstalled it a little while ago) and i didn't experienced ANY break in functionality, they are just Desktops and windows managers... they don't even have important config files in /etc ... 

So, my opinion after the rant... Try both, in my PERSONAL experience, i dont keep any :lolflag: i use KDE to show off Linux when people tell me Vista is the "1337z0r" in 3D enviroments. IMHO enlightenment (again, or whatever is spelled) is by far the lightest and more usable WM (yeah, it stll is considered a Window Manager not a DE Desktop Enviroment).

Remember when you choose to use Linux you have the freedom to choose how to customize your computer, you have the freedom to choose what your computer should look and display, it's when you should start to try different things and keep what you like and discard what you don't want.

I really hope this _NOT_ start a flame war.

Good luck making up your mind.

P.S. today i was answering some posts in which many people don't recomend installing KDE if you installed Ubuntu. And the advie on "vmware" just make me want to say this lol sorry :D. I just recommend vmware to install windows inside Linux or Linux inside windows (specially when you just want to add a DE).

---

### Post by rsambuca on 2007-02-12
Fenris, I think you need to take a break from your computer.  You are sounding a little bit stressed out right now.  Usually long ranting posts like that do not help anything, and tend to scare off new users.

I do agree with your point about not bothering with VMware in this case.

---

### Post by seppo on 2007-02-12
:lolflag: Fenris,  relax dude :wink:

I think you misinterpreted my post a bit. I did not recommend VMware, because of breaking things. Most of the time I use VMware to explore new Linux based system, because of the ease. If I don't like it, I can just delete the VM and still have a functioning PC. Quite handy, if you haven't made a choice yet. Once you made your choice you can wipe out your Winbl0ws and get working right away.

About your statements:

1) 1 and 2 don't see the relevant part of this post (and it is incorrect). Anyway:

From kubuntu.org front page:  **Kubuntu is a user friendly operating system** based on KDE, the K Desktop Environment.  With a predictable 6 month release cycle and part of the Ubuntu project, Kubuntu is the GNU/Linux distribution for everyone.
From the ubuntu.com homepage:
**Ubuntu is a complete Linux-based operating system**, freely available with both community and professional support. It is developed by a large community and we invite you to participate too!

3) I've never said it will

4) So if Ubuntu sucks,what are you doing in the Ubuntu support fora?

---

### Post by esaym on 2007-02-12
If you have both live cds then just try them both.  I have used kde all my life and have never even seen gnome.  I just burned a standard ubuntu cd and I am fixing to stick it in and check out gnome... ;)

---

### Post by teaker1s on 2007-02-12
can have both with both gnome and kde installed-select session at login

---

### Post by FenrisAbraxas on 2007-02-12
> **seppo said:**
> :lolflag: Fenris,  relax dude :wink:

I think you misinterpreted my post a bit. I did not recommend VMware, because of breaking things. Most of the time I use VMware to explore new Linux based system, because of the ease. If I don't like it, I can just delete the VM and still have a functioning PC. Quite handy, if you haven't made a choice yet. Once you made your choice you can wipe out your Winbl0ws and get working right away.

About your statements:

1) 1 and 2 don't see the relevant part of this post (and it is incorrect). Anyway:

From kubuntu.org front page:  **Kubuntu is a user friendly operating system** based on KDE, the K Desktop Environment.  With a predictable 6 month release cycle and part of the Ubuntu project, Kubuntu is the GNU/Linux distribution for everyone.
From the ubuntu.com homepage:
**Ubuntu is a complete Linux-based operating system**, freely available with both community and professional support. It is developed by a large community and we invite you to participate too!

3) I've never said it will

4) So if Ubuntu sucks,what are you doing in the Ubuntu support fora?

First of all i think i am stressed out lotsa work and way too much coffe sorry :P 

1 and 2.- Kubuntu is not an OS is more like another Debian based Distro based on Ubuntu.


3.- No, but i think i edited below, i read lots of post suggesting installing KDE in Ubuntu or Gnome in Kubuntu will break the system. And sorry i thought you were suggesting WildcatRay should install Ubuntu then use vmware to install Kubuntu.


4.-I never stated that Ubuntu Sucked, i said "if installing 2 DE in (K)Ubuntu break the system then sux". Because IMO installing the DE doesnt touch any important config files at all. And im here because i like to help others... though right now i went a little crazy about this :P really everyone using Kubuntu will say Gnome will break the system and Ubuntu users will say Kubuntu will break the system. And i think thats FUD (Fear Uncertainty and Doubt) to the new users willing to try something different.

#-o For now i'll stay away from ANY Ubuntu vs Kubuntu Threads :P 

My apologize to everyone for this rant :( ](*,) will you forgive me guys? [-o<

---

### Post by igknighted on 2007-02-12
More to the OP's point, I find that Ubuntu has more development and more users posting here to give help, so that would be where I start.  I prefer KDE over gnome, but find Ubuntu preferable to Kubuntu in terms of the final product.  I would try Ubuntu then install kde-base onto the system, and adding other apps you desire.  I think this is a better way to go than Kubuntu.  See [www.psychocats.net](www.psychocats.net) for more info on installing kde-base.

---

### Post by teaker1s on 2007-02-13
your choices are 
1) just install kde desktop=kde as login option
2)install kubuntu-desktop=ubuntu customised kde with choice of kde or gnome as desktop
you can either choose ubuntu or kubuntu usplash/artwork
you can choose gdm or kdm login manager

either way you can have kde and gnome on one system.

---

### Post by g8m on 2007-02-13
I hate choices.

Gnome was developed because there were some open source licensing issues with the qt libraries  
 which are at the base of kde.

As far as I know, those issues are resolved. Qt is opensource now. So why are there still 2 desktops. Why not combine the strong points of both in one killer desktop.

Strong points of KDE are qt, applications, configurable.

Strong points of Gnome, even my grandmother can work with Gnome, it's simple.

hmm, I don think that those points can be combined....

---

### Post by teaker1s on 2007-02-13
desktops are about choice-choose the one that suits you

---

### Post by WildcatRay on 2007-02-14
Thanks for the info.

---

### Post by maxamillion on 2007-02-14
I use Xfce, but I would use Gnome instead of KDE for a few reasons:
-heavy memory footprint
-cluttered menus (often redundant)
-I can't stand Qt

I will say that Konqueror is a brilliant application despite my distaste of KDE.

Just a personal preference though.

Xfce is really nice, its fast, blah blah ... you can read about it else where but I think what I like most about Xubuntu (other than its light weight nature) is its not automated to a level that annoys me, its like all the benefits of Ubuntu but with a debian level of interaction (which is honestly what I really want out of a desktop distro).

---

### Post by bg1256 on 2007-02-14
In my experience,

KDE:
Confusing layout - it seemed there was just too much going on in all the menus, and I couldn't find my way around.
But, it has some great native apps that don't seem to work quite as well in Gnome, or don't work at all, i.e., Superkaramba.

Gnome:
I much prefer the way Gnome looks and feels.  It's by no means perfect, though.
In contrast with KDE, the menus are sometimes lacking information, and installed programs don't always show up automatically.  That's probably my biggest complaint.
And I wish there was a good desktop widget program in Gnome! :)

---

