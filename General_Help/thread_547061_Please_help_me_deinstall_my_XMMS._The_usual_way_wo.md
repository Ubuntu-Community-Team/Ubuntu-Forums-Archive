---
title: "Please help me deinstall my XMMS. The usual way won't work."
date: 2007-09-09
forum: General Help
---

### Post by iamcelestial on 2007-09-09
Hey guys, new to the GNU/Linux world, tried Ubuntu and I am loving it.

Now to the problem : After I installed Ubuntu I immediately installed XMMS, which I like alot (I am so used to winamp). It was all doing greatly, but today it started crashing. I don't know why, one thing I did was to remove Totem, I don't know if that's connected somehow.

Anyway, I tried to remove XMMS(using sudo apt-get --purge remove xmms) and do a fresh install a couple of times - with no success, it keeps crashing. 

It "loads" in to the bottom pannel, without displaying any windows or reacting when I click on it. The system monitor shows me that it is actually running and using more and more RAM until I kill it. 

Does anybody know how to remove it completely from my system, so that I can do a really clean install, or how can I make it work again?

---

### Post by p_quarles on 2007-09-09
If the problem is with the XMMS config file, you would have to remove that yourself, manually:
```
sudo rm /home/username/.xmms/config
```
Then reinstall, and it will set up a new default config file.

If that doesn't work, you might at least try reinstalling Totem. I believe that's part of the base Ubuntu-desktop package, and by removing it you may have removed some basic GUI stuff. 

Another thing: you could try Audacious. It's another WinAmp-like player, but has a few more features than XMMS.

---

### Post by iamcelestial on 2007-09-09
Hi and many thanks for the quick answer. 

I did what you told me and it couldn't find the file - I assume that it has already been cleaned. I also tried removing it the way totem-gstreamer was supposed to be removed in this topic

[http://ubuntuforums.org/showthread.php?t=370854&highlight=totem](http://ubuntuforums.org/showthread.php?t=370854&highlight=totem)

and this "dpkg-query -L "  thing said it couldn't find anything.

It still won't run though, so it might be the second thing you suggested.  I tried downoading Totem from the synaptic menu, I clicked on everything that had the name totem in it but somehow no new icon(of totem) is showing in the "applications ->sounds and video". Any ideas?

apt-get says that totem is installed :s

---

### Post by PurposeOfReason on 2007-09-09
Have you tried just opening synaptic and marking XMMS for uninstallation?

---

### Post by p_quarles on 2007-09-09
> **PurposeOfReason said:**
> Have you tried just opening synaptic and marking XMMS for uninstallation?
Synaptic is just a front-end for apt, so that wouldn't do anything different.

Apt-get remove doesn't remove config files from the home folder. Are you sure it's not there? Note that the directory is "~/.xmms" including the dot.

---

### Post by iamcelestial on 2007-09-09
yes, xmms is out now (supposedly), nothing shows that it is there. so my problem must lie in the previously deinstalled totem.

when i write your line this is what i get :
rm: cannot remove `/home/celestial/.xmms/config': No such file or directory

now i just tried audacious and it works.(MANY thanks for the tip, I thought audacious is the same as audacity, which I didn't like)

*edit* xmms keeps crashing the way it did after the fresh install, but at least now i have audacious

---

### Post by p_quarles on 2007-09-09
That's odd. Anyway, audacious should do the job for you, but if you want XMMS back, you might attempting to fix broken packages:
```
sudo dpkg --configure -a
```
Uninstalling Totem may have broken the ubuntu-desktop package (which normally isn't important -- it's a dummy package), and fixing it *might* help. I wouldn't bet on it, though, as XMMS doesn't depend on Gnome or GTK. Maybe worth a try, though.

---

### Post by iamcelestial on 2007-09-09
> **p_quarles said:**
> That's odd. Anyway, audacious should do the job for you, but if you want XMMS back, you might attempting to fix broken packages:
```
sudo dpkg --configure -a
```
Uninstalling Totem may have broken the ubuntu-desktop package (which normally isn't important -- it's a dummy package), and fixing it *might* help. I wouldn't bet on it, though, as XMMS doesn't depend on Gnome or GTK. Maybe worth a try, though.


hey, thanks alot again. i did the command line you wrote and i was promted to enter my password. I entered it and then without any messages i was at the exit point again. 


celestial@station1:~$ sudo dpkg --configure -a
Password:
celestial@station1:~$ 
 
is this normal?

 I browsed around the forums for totem and it seems that it might screw up your system if you deinstall it :( However, I cant seem to be able to reinstall it again (see previous post). Oh well, at least thanks to your tip i am able to listen to .mp3 files with a winampish player - just what I wanted on the first place when i installed XMMS.

---

