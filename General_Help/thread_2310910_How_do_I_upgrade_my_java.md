---
title: "How do I upgrade my java?"
date: 2016-01-22
forum: General Help
---

### Post by nzdreamer55 on 2016-01-22
Hello everyone,


I currently am running ubuntu for the pi and installed java.  I noticed that there is an update for java for windows and so I suspect that I need to update my pi machine.  How would I do this?


Previously I downloaded  Java SE Development Kit 1.8.65 and I think that this had java in it and I installed it from here.  I was hoping that I could install it from an easier place.


On the java site there is a place
http://java.com/en/download/manual.jsp


where I can find a linux version
http://javadl.sun.com/webapps/download/AutoDL?BundleId=114679


and the instructions just say to unpack the tarball and install.  I guess I am not sure how to uninstall the previous version if this is what I need to do.


So any help is much appericiated

---

### Post by Petro Dawg on 2016-01-23
Need to stop thinking of Linux like Windows.  Usually if you install software through the built in software center, it will be forever updated through the usual system update process.  When Ubuntu updates, it will install updates for all software installed so long as that software is in the Ubuntu repositories.

If you downloaded a package and installed it directly from a .zip or .deb file you may need to check the site you downloaded it from to see if there has been an update released.  In which case you just download it and reinstall as far as I know.

---

### Post by Dreamer Fithp Apprentice on 2016-01-23
> **nzdreamer55 said:**
> I noticed that there is an update for java for windows and so I suspect that I need to update my pi machineFalse assumption behind your sound reasoning. There is no special reason for the devs to bring out new linux and windows versions synchronously.> **nzdreamer55 said:**
> I currently am running ubuntuYou should specify the version.> **nzdreamer55 said:**
> update my pi machine.  How would I do  this?Open a terminal. Type ```
sudo apt-get  update
```Press the enter key. It will ask for your password. Type it  in. Press the enter key. Let it work. It will probably take a couple of  minutes. When it finishes type```
sudo apt-get dist-upgrade
```and  press the enter key. Let it work. When it finishes you should have  everything up to date.> **nzdreamer55 said:**
> On the java site there is a place
[http://java.com/en/download/manual.jsp](http://java.com/en/download/manual.jsp)

where I can find a linux version
[http://javadl.sun.com/webapps/download/AutoDL?BundleId=114679](http://javadl.sun.com/webapps/download/AutoDL?BundleId=114679)

and the instructions just say to unpack the tarball and  install.Best not to do it that way unless there is some  specific, articulable reason not to use the version in the repository  instead.> **nzdreamer55 said:**
> I guess I am not sure how to uninstall the  previous version if this is what I need to do.Normally, you  don't. Very rarely, if you installed some non-native version like you  did, you might. Usually not even then. And when you do, it is usually  easiest to look where you downloaded, extracted, maybe even compiled,  the software, and find the "something.deb" file. Then open this with  gdebi (install that if it turns out you need it) and select uninstall.  But normally, you can ignore that.

So,

how easy is that, hunh?

---

