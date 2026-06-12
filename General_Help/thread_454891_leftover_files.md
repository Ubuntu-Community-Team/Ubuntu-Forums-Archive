---
title: "leftover files"
date: 2007-05-26
forum: General Help
---

### Post by Norehca on 2007-05-26
where are games/apps stored in the file system? when i uninstall them do they leave behind files / folders? can i defragment the filesystem or is there no need? any help much appreciated.

---

### Post by m.musashi on 2007-05-26
In general, if you remove something in Linux it will be gone. However, there are shared libraries and these will not be removed - because something else might be using them. That's a good thing. However, if something is no longer being used you will get a message saying something is no longer needed and to use autoremove to get rid of it (if you are using a terminal - I don't know if synaptic does that or not). To remove the unneeded stuff do
```
sudo apt-get autoremove
```
As for defragmenting, that is a windows bug. No need to do that in Linux.

EDIT: oh, one more thing...don't go removing folders or files from your root partition. That is a surefire way to screw everything up. Let the built in tools do their job (i.e. synaptic, apt-get).

EDIT: here is an example. Just cleaned up some stuff.
```
jim@feisty:~$ sudo apt-get autoremove
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgnucrypto-java liblog4j1.2-java libswt3.2-gtk-java libseda-java
  libcommons-cli-java libgtk-jni libcairo-java libbcprov-java libglib-java
  libgtk-java libswt3.2-gtk-jni
The following packages will be REMOVED:
  libbcprov-java libcairo-java libcommons-cli-java libglib-java
  libgnucrypto-java libgtk-java libgtk-jni liblog4j1.2-java libseda-java
  libswt3.2-gtk-java libswt3.2-gtk-jni
0 upgraded, 0 newly installed, 11 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 7545kB disk space will be freed.
Do you want to continue [Y/n]?
```

---

### Post by Norehca on 2007-05-26
thanks alot. that was a quick response. i appreciate your speed. now if i use that auto command, will this simply search for uneeded files and delete them as you mentioned? and if you dont mind answering whats the difference between apt-get aptitude and wget, or whatever else there is.

---

### Post by m.musashi on 2007-05-26
I just edited while you were posting. Check my first post for an autoremove example. Basically, yes, it removes what is no longer being used.

apt-get is the debian tool for managing packages. I think pretty much all debian based distros will use it. However, some will have a gui front end as well to make it easier (debatable). Synaptic is the ubuntu front end. Aptitude is a different tool that is supposed to be better about managing dependencies - especially with meta-packages. You can read more [here](http://www.psychocats.net/ubuntu/aptitude). wget is for downloading files. Put in a web address of a file and it "gets" it.

---

### Post by Norehca on 2007-05-26
thank you very much. i really appreciate your help. this is a great community! :D

---

### Post by m.musashi on 2007-05-26
Yep. After hanging out here for about 18 months now I've learned a lot. I was totally new to Linux when I installed ubuntu in Oct 2005. These forums were/are just plain awesome. Now I try to repay my debt by helping others. Glad I was able to help (sometimes I'm not:().

---

### Post by Norehca on 2007-05-26
i spoke a bit too soon. im still thankful but ive run into one more question. what i got from that page you sent me is basically aptitude seems to be better. unlike apt-get it removes all the apps you installed, apt-get only uninstalls the core packages? so whats the point of apt-get?

---

### Post by m.musashi on 2007-05-26
Well, that's kind of a personal preference thing. Apt-get now has the autoremove option so it isn't much different from aptitude. In the past I guess it was possible to use apt-get a lot and end up with unused files but maybe no one thought that was all that bad. I don't really know. Those who thought that it was bad started to use aptitude and the apt-get people added autoremove. Apt-get is still the basis of a debian distro and just about everyone here will give you commands involving apt-get. You can substitute aptitude if you want. I'm afraid I can't say much else without resorting to bias. It's kind of like saying that gnome or kde is better. Just read a little, play a little and decide which you like best. However, it seems smart to use one or the other rather than both and Synaptic is a front end for apt-get.

For what it's worth, I use apt-get but have used aptitude to install things like kde-desktop. With autoremove now that is probably not all that important. Sorry if that's kind of vague.

---

### Post by OrangeCrate on 2007-05-26
Here are some additional instructions on removing junk files:

[http://doc.gwos.org/index.php/RemoveJunkFiles](http://doc.gwos.org/index.php/RemoveJunkFiles)

---

### Post by Norehca on 2007-05-26
i just noticed today after unhiding the files in my home folder that even using these commands the programs leave behind sometimes ALL of the files! like after uninstaling wine a while back i saw the .wine directory with all of the files still in it. i used the autoremove, autoclean and got nothing. so i simply deleted the folder along with the folders of games that i had previously uninstalled. is this safe if i know whats not installed?

---

### Post by lluisanunez on 2007-05-26
Yes you can. The hidden subdirectories under your home directory contain the user files of every application (config, etc). You can remove these subdirectories if you do not use the apps.
But if you leave them, and later reinstall these apps, you will find them all configured with your preferences.

---

### Post by Norehca on 2007-05-26
thanks alot everyone. i really appreciate all of your help.

---

### Post by rillip on 2007-05-26
tried to hit caps lock and accidently hit tab.  Please see post below.

---

### Post by rillip on 2007-05-26
As for aptitude vs apt-get, your post indicates aptitude is more appearling because it auto removes things.  I can see the appeal, and most poeple who use it have no issues.  But some people end up in a situation like this:

Hey, I don't use KMail.  Let's uninstall it.

Aptitude says great, uninstalled.  Also, you're no longer using the package kubuntu-desktop, I'll remove that for you too.

Ookay, that was the meta package for Kubuntu.  You just single handedly fuggered your install, none of your apps are going to run, your desktop will likely be all messed up... it will be very very bad.  That's a kind of over-the-top example, but you can see how something like that could happen, yes? It does to some people, but not to most.  That's why some perfer apt-get.  There are other considerations, of course, like the front end for it, but those are aesthetic.

As for your actual issue, I think the files you are seeing are in your home directory, yes?  These aren't the actual files for the programs, but your user settings.  That's typically all that's stored in the home directory.  In general, I'd say you can safely delete things in your home directory.  Outside of that, I would be very, very sure you're not using the program.  Shared libraries should be installed outside of the actual program directory, so that shouldn't affect anything, but if you accidently delete one with a shared file, you'll get error messages, have to research it, figure out how to reinstall the shared file without the program, etc.  Just be very careful, and remember that EVERYONE should have a backup of their important files.

---

