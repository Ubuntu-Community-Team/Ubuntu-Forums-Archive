---
title: "Ignoring specific packages with update manager"
date: 2007-02-28
forum: General Help
---

### Post by AlcoJaguar on 2007-02-28
I was wondering if there was a way to ignore specific packages so that I wouldn't always be asked to update a certain set. I'm aware of dpkg and placing holds, but I've been asked repeatedly to update a debian package I compiled from source (wine 0.9.31). In the update manager it keeps asking me to update from 0.9.31 to 0.9.31 which is odd but understandable as I didn't install it through apt in the first place but I have the sources in my sources.list.d directory as to pull the package source to build it.

Any suggestions?

---

### Post by P86 on 2007-03-01
I'm looking for a way to do this in Kubuntu. I installed a package that is newer than the version listed in Adept Notifier. How can I get it to ignore this package?!?

---

### Post by AlcoJaguar on 2007-03-01
Well I found something that works, though it'll ignore any version of the package (you can un-ignore the package once you know there's a newer version than the one you have).

First you want a list of the packages and their current states (install, hold, removed, etc...) by typing into a terminal:
```
sudo dpkg --get-selections packageName > listOfPackages.txt
```

Open up that file you just created (listOfPackages.txt) and change 'install' on the same line as the package you want to ignore to 'hold'.

Once you've done that, save the file, and go back to your terminal and type:
```
sudo dpkg --set-selections < listOfPackages.txt
```

Then just to make sure everything is updated type:
```
sudo apt-get update
```
Or in the update notification window click 'Update', they do the same thing.

That should get rid of the needless notifications, just make sure that when there's a newer version to do these steps again only instead replace the word 'hold' with 'install'.

---

### Post by pingvin on 2007-04-19
Thanks for this post - does exactly what I needed. I have an old version of Kxdocker for transparency reasons (a very old graphics card!), and it was a pain having to un-tick it in the graphical package manager each time there were updates to install.
Much appreciated!
Mike

---

### Post by P86 on 2007-04-21
Maybe I'm missing something simple, but after doing step 1, I got the following error message and a blank text file: 

"No packages found matching packageName."

---

### Post by pingvin on 2007-04-24
packageName would be where you insert the name of the package, in my case "kxdocker" (but without the speech marks)

Mike

---

### Post by P86 on 2007-04-25
LOL. Ok, yeah I was missing something simple! Thanks for the reply...

---

### Post by the dsc on 2008-04-23
Unfortunately it does not set us free from the notifications of adept notifier, apparently. All it did was to set "no change" as default, instead of "upgrade", which is something already anyway.

Apparently the GNOME equivalent does not have that flaw. Sigh. I don't want to install it... 

(I'm using debian etch, however)

---

