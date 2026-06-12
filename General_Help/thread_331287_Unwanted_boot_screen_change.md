---
title: "Unwanted boot screen change"
date: 2007-01-04
forum: General Help
---

### Post by Turner.kj on 2007-01-04
I inadvertently changed my boot-up screen from the ubuntu screen to the edubuntu.  This how I did it; I install the edubuntu packages so I could see the artwork and themes edubuntu had to offer.  After seeing some of the changes, I decided to uninstall all the edubuntu packages.  I then noticed that my bootup screen is now the red edubuntu screen.  How do I get back to the ubuntu bootup screen?

---

### Post by strabes on 2007-01-04
sudo update-alternatives --config usplash-artwork.so

Select the one you want.

---

### Post by Turner.kj on 2007-01-04
This did not work for me, I received the following message:

There is only 1 program which provides usplash-artwork.so
(/usr/lib/usplash/usplash-theme-ubuntu.so). Nothing to configure.


Just to be clear, this is the boot-up screen, not the logon screen.

I thank you in advance for any help.

---

### Post by Rab22 on 2007-01-04
> **Turner.kj said:**
> This did not work for me, I received the following message:

There is only 1 program which provides usplash-artwork.so
(/usr/lib/usplash/usplash-theme-ubuntu.so). Nothing to configure.


Just to be clear, this is the boot-up screen, not the logon screen.

I thank you in advance for any help.

Interestingly, the update-alternative doesn't work for me either. I do get a list (three options which is correct) and I select the one I would like. When I shutdown it does show the correct one (the one I've selected). However, upon start up, it shows the usplash with the highest priority in the alternatives list.

I figure the easiest thing to do would be remove the usplash (it's the Kubuntu one that is causing the problems btw), and if I ever wanted it back simply add it again with the same priority the others have (currently the others have a 10, and kubuntu has a 55). Unless of course, someone knows how to change the priority without removing the alternative -- my researching has not found a simple answer to that.  

Here is a screenshot of the settings update-alternatives has,
[IMG]http://www.rab22.ws/images/misc/console1.png[/IMG]

What I find interesting is that there is an astrick by the one I've selected; yet a plus sign by the one that is giving me trouble. I assume that this is because, as the '--display' option states, that the kubuntu usplash is the 'best' option. However, this seems to really take away from any type of 'manual' settings. That is, if it's going to keep defaulting to the highest prioritized alternative.

---

### Post by Rab22 on 2007-01-04
Interesting update. I removed and re-installed the usplash-theme-kubuntu.so with a priority of 10. I reset the default theme to usplash-theme-ubuntu.so (it now has the plus and the astrick). However, after restarting, Kubuntu splash **STILL** shows up. Yet, again, ubuntu splash shows up for shutdown.

I have no idea what this problem could be now. Does anyone know if there is a configuration option somewhere that installing kubuntu does?!

---

### Post by ovidescu on 2007-01-09
I have the same problem. Installed KDE to check it out, removed it using aptitude, Ubuntu splash at shutdown, Kubuntu splash at startup.
Hopefully someone will come with the solution for this, as it is kinda irritating for me to see the Kubuntu splash.
I am also trying to change the splash screen using "Configuration editor". Will let you know if I am successful.

Ovidiu

---

### Post by mcduck on 2007-01-09
I'm using Start-Up Manager to change my boot splashes and options. You may want to give it a try: [http://www.ubuntuforums.org/showthread.php?t=295524]("http://www.ubuntuforums.org/showthread.php?t=295524")

---

### Post by silverglade00 on 2007-04-03
I got this to work on Feisty Beta using the following, as given above:

```
sudo update-alternatives --config usplash-artwork.so

```
Choose the one you want by picking the corresponding number, then give it this command to put the new splash screen back into the initramfs, as found [_[COLOR="Blue"]here[/COLOR]_]("https://help.ubuntu.com/community/USplashCustomizationHowto"):

```
sudo dpkg-reconfigure linux-image-$(uname -r)
```

It will give a warning about passing the wrong /sbin/something_or_other during the text flying by, but it works just fine. 

This is with an updated kernel. I have not tried the older kernel that is still in my menu.lst.

---

