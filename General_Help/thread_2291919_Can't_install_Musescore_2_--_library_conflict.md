---
title: "Can't install Musescore 2 -- library conflict"
date: 2015-08-23
forum: General Help
---

### Post by VanillaMozilla on 2015-08-23
I'm using Trusty and trying to upgrade Musescore 1.3 to Musescore 2.0.  Version 2 is available in a PPA:  [https://launchpad.net/~mscore-ubuntu/+archive/ubuntu/mscore-stable](https://launchpad.net/~mscore-ubuntu/+archive/ubuntu/mscore-stable) .  Unfortunately, the new version will not install, and encounters a version conflict with libqt.

sudo apt-get update
sudo apt-get upgrade gets me:

The following packages have been kept back:
libqt5core5a libqt5dbus5 libqt5gui5 libqt5network5 libqt5opengl5
etc. (about 20-25 packages altogether).

It turns out that Musescore 2 requires at least version 5.3 of libqt5, while I have 5.2.1.  Even if I compile it myself, it still requires 5.3.  According to Synaptic, libqt5 was installed by the previous Musescore PPA, so maybe I could just uninstall all those packages or force update them to 5.3.

BUT there's a big problem.  If I try to update libqt5core5 manually with Synaptic, it wants to ***remove*** packages such as ubuntu-desktop, and many others!  Somehow this doesn't seem safe.

So, just what do I do?  Is there a way to run Musescore 2 on this computer, with the required libqt5 version 5.3?  Or will it destroy the desktop if I try?  There's more discussion here:  [https://musescore.org/en/node/74041](https://musescore.org/en/node/74041) .  I have also contacted the package maintainers, but have not received a reply.

---

### Post by mc4man on 2015-08-24
basically here - [http://ubuntuforums.org/showthread.php?t=2274951&p=13270676&viewfull=1#post13270676](http://ubuntuforums.org/showthread.php?t=2274951&p=13270676&viewfull=1#post13270676)
You could install & see if you miss any of the removed stuff, could be you don't use. possible some could be re-built to use the newer qt5
If unsuitable then install ppa-purge &  use on the ppa.

---

### Post by VanillaMozilla on 2015-08-24
Thanks.  I saw that question but missed the answer.  (red face)

See if I miss any removed stuff?  Are you sure?  That seems a little risky, to say the least.  Hence this question.

Here's what Synaptic says about the ubuntu-desktop package:
"This package depends on all of the packages in the Ubuntu desktop system

It is also used to help ensure proper upgrades, so it is recommended that
it not be removed."

All this information seems contradictory, which is why I asked.  I don't know why a package that was supposedly installed from a MuseScore PPA is required for the ubuntu-desktop package.  Nevertheless, removing it is intimidating in the extreme.  I'm not an expert on Ubuntu or Musescore packages.  Any other thoughts?

---

### Post by VanillaMozilla on 2015-08-24
OK, it turns out that ubuntu-desktop is indeed from libqt.  It's probably the qt interface for the QT library.

The Ubuntu instructions say to add the PPA, then
sudo apt-get update
to install the software, but in this case that leads to a conundrum.  The correct command in this case is
sudo apt-get install musescore,
which works flawlessly.

The PPA instructions could sure use a rewrite.

---

### Post by oscarivera9 on 2016-01-31
Although this thread is closed, I'm currently trying to decide whether or not to install musescore 2 under Ubuntu 14.04 since it removes packages which seem to be needed such as ubuntu desktop.  I've read all of the posts in this thread as well as the links provided and I'm still in the dark as to whether it's safe to remove these packages.
Any help would be appreciated.

---

### Post by VanillaMozilla on 2016-04-17
Sorry I didn't see your question until now.  By all means, you can install MuseScore 2 in Ubuntu.  It's greatly preferable to version 1.  But Ubuntu help with it is slow in coming.

Check the MuseScore forum if you still need help.  They are really on top of Ubuntu packaging.  Here's that previous link, in case it's appropriate:   [https://musescore.org/en/node/74041](https://musescore.org/en/node/74041) .

---

### Post by oscarivera9 on 2016-04-17
I've been getting by with Musescore 1 until now and I'll stick with it for the time being.  I had doubts about the upgrade due to some dependencies being uninstalled such as ubuntu-desktop so I didn't upgrade.  Ubuntu 16.04 LTS is almost out and after it's been out for a few weeks I plan to upgrade to it.  A few years ago I decided to only upgrade to LTS releases which is why I'm still using 14.04 and I imagine 16.04 should support Musescore 2 by default.
Thanks anyway.

---

### Post by ian-weisser on 2016-04-17
No need to imagine. Musescore 2.0.2 is in Ubuntu 16.04.

Remember to uninstall your PPA version of Musescore and disable the PPA source before upgrading.

---

### Post by Allisterguy on 2016-04-28
Hi
I have been running 14.4, 32 bit and have been using Musescore 2.0.2  I would  really like to upgrade to Musescore 2.0.3. ( amateur musician)
I have been unable to do this 
I am new to linux and was advised to use:-
 Sudo add-apt-repository ppa: mscore-unbutnu/mscore-stable
This seems not to work
If I go to Musescore web site, I can, and have, downloaded for Ubuntu museScore -2.0.3- i686 appimage
but not sure how to proceed
Any advice greatly appreciated.
Allister

---

### Post by ian-weisser on 2016-04-29
Those are totally different (and incompatible) methods of upgrading. You must pick one and stick with it.

Are you asking for help upgrading using the PPA?
Or are you asking for help upgrading from the Musescore website.

You can do either (it's *your* system). However, you will be upgrading from a supported (in this forum) version of Musescore to an unsupported (in this forum) version. If you run into problems, our most likely response will be for you to revert to the supported version.

Learning how to upgrade your software safely using a PPA is a fairly simple skill to learn.
Remember uninstall the software and disable the PPA before you upgrade to the next release of Ubuntu, or the non-Ubuntu version may break your system.

---

### Post by oscarivera9 on 2016-05-01
> **Allisterguy said:**
> Hi
I have been running 14.4, 32 bit and have been using Musescore 2.0.2  I would  really like to upgrade to Musescore 2.0.3. ( amateur musician)
I have been unable to do this 
I am new to linux and was advised to use:-
 Sudo add-apt-repository ppa: mscore-unbutnu/mscore-stable
This seems not to work
If I go to Musescore web site, I can, and have, downloaded for Ubuntu museScore -2.0.3- i686 appimage
but not sure how to proceed
Any advice greatly appreciated.
Allister

The following command which you mentioned doesn't install the software, it just adds the PPA repoository so that you can then install the software:
```
Sudo add-apt-repository ppa: mscore-unbutnu/mscore-stable
```

So, after typing that into a terminal, which seems like you've already done, you need to type the following into a terminal:
```
sudo apt-get update
```
and then,
```
sudo apt-get install musescore
```

I agree with [COLOR=#000000]ian-weisser that you should try to stick to doing it via PPA which seems to be what you've already tried instead of installing it through the website[/COLOR]

---

