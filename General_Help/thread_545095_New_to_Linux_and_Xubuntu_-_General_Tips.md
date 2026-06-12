---
title: "New to Linux and Xubuntu - General Tips"
date: 2007-09-07
forum: General Help
---

### Post by spooter on 2007-09-07
Hi all,

I am new to linux and decided on Xubuntu which I have installed onto my system will Windows as a dual boot option.  Im am going to try and use Xubuntu as my main system though.  

I was wondering what tips people I have to make the system run at its best?

Whats the best program for Xubuntu to rename the tags on mp3 files?

I have managed to install all the Java, mp3 support etc using the automatix program easily and have installed CS Source using Wine although yet to test.  

My main thing is to make everything run as fast as possible.  I think sometimes its a little slow opening the home folder?  is this heard off?

What should I start reading up about to learn more about Linux and Xubunu?  I am used to supporting Windows and would like to learn Linux to this level as well eventually.

Cheers for your advice everyone?

---

### Post by ajgreeny on 2007-09-07
Can't answer your specific questions but for general info etc on ubuntu go to:-
[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

It has just about everything you could ever want in "how to" information.

---

### Post by mojoman on 2007-09-07
Well, for tags I use Ex Falso or Audio Tag Tool and none of them use any Gnome or KDE libraries. I prefer Ex Falso but both get the job done. Did I mention that none of them uses any Gnome or KDE libraries? :wink:

If you want to keep it lean, mean and fast you should avoid using applications that load the heavier Gnome and KDE libraries that are not required by Xfce4. 

Xubuntu doesn't ship with a good CD/DVD-burning app and I would recommend Graveman as it doesn't use any of the Gnome or KDE libraries. :mrgreen:

When it comes to video I would recommend Xine (my personal favorite) MPlayer (I don't like it myself but it is a good player, no doubt about that) or vlc (it simply rocks and will play just about anything but it can be a bit daunting to configure it). None of them use the heavier Gnome or KDE libraries. :biggrin:

There are light-weight applications for just about anything or at least not-so-light-weight-but-still-not-depending-on-Gnome-or-KDE applications for just about anything. I myself like Xfce because I don't want to squander my systems resources on the desktop itself and use some resource intensive applications though I prefer light and quick. Let me know what type of application you need and I'll try to help out.

To install (some of) the stuff I've mentioned, open a terminal and type:
```
sudo apt-get install exfalso
sudo apt-get install tagtool 
sudo apt-get install graveman
sudo apt-get install xine-ui
```

Also, here is a [blogg]("http://xubuntu.wordpress.com/") on Xubuntu

About the home folder being slow, I'm sorry to say I can't help you on that one. Is it on a separate partition or in the root partition?

/mojoman

---

