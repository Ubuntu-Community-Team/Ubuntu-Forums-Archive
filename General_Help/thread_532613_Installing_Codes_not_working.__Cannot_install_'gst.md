---
title: "Installing Codes: not working.  Cannot install 'gstreamer0.10-plugins-ugly'"
date: 2007-08-22
forum: General Help
---

### Post by swy000 on 2007-08-22
So I installed Ubuntu today and Im trying to work my way around. Moving away from windows and Im glad. im running into trouble. At first I couldnt install VLC and I put up a post in "Multimedia & Video" section and now I decided to play an mp3 and Movie player open up automatically. Once that happens, I get an error that it wont play and it asks if i want to download codecs. I click "Yes" once asked to install codecs but nothing happens. I get this error when I tick the first option (Gstreamer) and the error says this:
```

Cannot install 'gstreamer0.10-plugins-ugly'

This application conflicts with other installed software. To install 'gstreamer0.10-plugins-ugly' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.
```

Now im starting to think nothing I install is gonna work! Hehe...but im not giving up just yet!! :)

Im pretty sure multiverse and universe are on. They are both ticked. 

Any ideas?

---

### Post by jamvegan on 2007-08-23
Okay, it's telling you that synaptic can solve the conflict, so let's give that a try.  To open synaptic go to System->Administration->Synaptic Package Manager.  After you enter your password and wait a few moments for it to update itself, click the Search button, and enter gstreamer0.10-plugins-ugly in the dialog window.  When it appears in the list in the main window, click the box to the left of the package name and select Mark for Installation.  Then click the Apply button.  Now you may get a dialog telling you that other packages either need to be installed or removed.  Unless you see a compelling reason not to, tell it to go ahead, and it will install your new software.

---

### Post by swy000 on 2007-08-23
> **jamvegan said:**
> Okay, it's telling you that synaptic can solve the conflict, so let's give that a try.  To open synaptic go to System->Administration->Synaptic Package Manager.  After you enter your password and wait a few moments for it to update itself, click the Search button, and enter gstreamer0.10-plugins-ugly in the dialog window.  When it appears in the list in the main window, click the box to the left of the package name and select Mark for Installation.  Then click the Apply button.  Now you may get a dialog telling you that other packages either need to be installed or removed.  Unless you see a compelling reason not to, tell it to go ahead, and it will install your new software.

SO im getting the same errors im getting when I attempt to install vlc... (or at least they look the same, but not really the same file name). After I click apply to the other files that need to be installed, i get an error pop up that says:

```
gstreamer0.10-plugins-ugly:
 Depends: libid3tag0 (>=0.15.1b) but it is not installable
 Depends: libmad0 (>=0.15.1b) but it is not installable

```

Any ideas? Thnx...

Edit: here is an imagechack pic of the pop up -- [[IMG]http://img452.imageshack.us/img452/511/screenshotcm2.th.png[/IMG]](http://img452.imageshack.us/my.php?image=screenshotcm2.png)

---

### Post by jamvegan on 2007-08-23
Hm.  What happens if you search in Synaptic for libid3tag and/or libmad?  Do they come up in your results list?  Do they show that they are already installed, or not (either way, what version is shown)?  Incidentally, what version of Ubuntu are you running?  Oh, also, you mentioned that universe and multiverse are enabled.  What about restricted?

---

### Post by forestpixie on 2007-08-23
there are two in synaptic - gstreamer0.10-plugins-ugly and gstreamer0.10-plugins-ugly-multiverse, for some reason I have them both installed ;) - also you can get it from [here]("http://linuxappfinder.com/package/gstreamer0.10-plugins-ugly") if that helps you

---

### Post by swy000 on 2007-08-23
> **jamvegan said:**
> Hm.  What happens if you search in Synaptic for libid3tag and/or libmad?  Do they come up in your results list?  Do they show that they are already installed, or not (either way, what version is shown)?  Incidentally, what version of Ubuntu are you running?  Oh, also, you mentioned that universe and multiverse are enabled.  What about restricted?

ok so i checked all the above.
Both files dont exist. there is a file called ibmad-ocaml but not libmad0 as above. So i guess they're not there and no installed. Im running ubuntu 7.04. And yes, restricted is enabled. 
still cant seem to fix this... hate being a newb :p

---

### Post by angryfirelord on 2007-08-23
Don't even bother with gstreamer. It has caused me headaches.

Instead do this:
```
sudo apt-get install totem-xine libxine1-plugins
```
See if that works.

Also, if you're running an older version of Ubuntu, make sure universe and multiverse are enabled.

---

### Post by swy000 on 2007-08-23
> **forestpixie said:**
> there are two in synaptic - gstreamer0.10-plugins-ugly and gstreamer0.10-plugins-ugly-multiverse, for some reason I have them both installed ;) - also you can get it from [here]("http://linuxappfinder.com/package/gstreamer0.10-plugins-ugly") if that helps you

i found the gstreamer0.10-plugins-ugly but not the multiverse. the file exists in my packages, i just cant seem to install it. do i need to google for these files and download them? (the ones that need to be added)... maybe ill try that :s...

---

### Post by swy000 on 2007-08-23
> **angryfirelord said:**
> Don't even bother with gstreamer. It has caused me headaches.

Instead do this:
```
sudo apt-get install totem-xine libxine1-plugins
```
See if that works.

Also, if you're running an older version of Ubuntu, make sure universe and multiverse are enabled.

i got this as an output... missing smthn maybe???

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libxinel-plugins

```

on another note, on the top right of the desktop, ubuntu says you have 117 updates that can be downloaded... should i download them first and then try? (they are in the update manager... somehow i think i need to select the ones i need and not all 117)

---

### Post by jamvegan on 2007-08-23
> ok so i checked all the above.
Both files dont exist. there is a file called ibmad-ocaml but not libmad0 as above. So i guess they're not there and no installed. Im running ubuntu 7.04. And yes, restricted is enabled.

Hm.  I have a clean install of 7.04 on one of my machines, and those libraries are listed in Synaptic for me.  Try clicking the Reload button in Synaptic, and then check for them again.

---

### Post by jamvegan on 2007-08-23
> on another note, on the top right of the desktop, ubuntu says you have 117 updates that can be downloaded... should i download them first and then try? (they are in the update manager... somehow i think i need to select the ones i need and not all 117)

I would definitely recommend running all of these updates.  They are security or performance enhancements to software that you already have installed.  It is certainly possible that you don't "need" some of them, but keeping up with Ubuntu's updates should help to keep your system running safely and smoothly.

---

### Post by swy000 on 2007-08-23
> **jamvegan said:**
> Hm.  I have a clean install of 7.04 on one of my machines, and those libraries are listed in Synaptic for me.  Try clicking the Reload button in Synaptic, and then check for them again.

so odd really...im searching under "ALL". I cant find it. is it under smthn else???
Here is a picture I guess of where im searching (looking for libmad0):

[[IMG]http://img250.imageshack.us/img250/7946/screenshot1pc9.th.png[/IMG]](http://img250.imageshack.us/my.php?image=screenshot1pc9.png)

---

### Post by jamvegan on 2007-08-23
Yeah, it should be there as 'libmad0'.  Did you try the Reload button?

---

### Post by swy000 on 2007-08-23
> **jamvegan said:**
> Yeah, it should be there as 'libmad0'.  Did you try the Reload button?

yup. tried reload then looked. found nothing. the picture i pasted shows my search. i dont know if you saw that. im running the 117 updates, nearly done. they are installing. maybe it will be there then :S ?!?! now its just wishful thinking....

---

### Post by swy000 on 2007-08-23
Ok, reload just finished. I cant find libmad0 still. 

This might be important, when i hit "Reload" and it download 37 errors, i get a pop up error message:

> Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)


---

### Post by jamvegan on 2007-08-24
> This might be important, when i hit "Reload" and it download 37 errors, i get a pop up error message...
Yep, that's important. :-)

Okay, I'm going to suggest that you compare your /etc/apt/sources.list to mine.  Here's mine:
```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse
```
If you make any changes in yours, either by editing this file or checking or unchecking repositories in Synaptic, you need to run ```
sudo apt-get update
``` or click Reload for the changes to take effect.

Let me know whether or not you find anything there that needs to be fixed.

---

### Post by swy000 on 2007-08-24
ok well, here's mine: they are the same based on my comparison

> # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

---

### Post by jamvegan on 2007-08-24
In this thread: [http://ubuntuforums.org/showthread.php?p=3204431](http://ubuntuforums.org/showthread.php?p=3204431) I found the following solution (hopefully):
```
sudo rm /var/lib/apt/lists/partial/*
```
Then try Reload or ```
sudo apt-get update
``` again.

---

### Post by swy000 on 2007-08-24
> **jamvegan said:**
> In this thread: [http://ubuntuforums.org/showthread.php?p=3204431](http://ubuntuforums.org/showthread.php?p=3204431) I found the following solution (hopefully):
```
sudo rm /var/lib/apt/lists/partial/*
```
Then try Reload or ```
sudo apt-get update
``` again.

THAT WORKED!!! ok no caps i know!! that worked!!!!
ok now you need to tell me what that did...did it remove partial installed files/downloaded???? it even fixed my VLC installation..i tired redownloading VLC and it worked.... that's a magic line right there.....!!! what did it do exactly??? im off to bed, ill research it tomorrow.....

go ubuntu!

---

### Post by jamvegan on 2007-08-24
My understanding of the issue is that something, possibly Ubuntu's servers being too busy while you were trying to update your computer, causes apt to be unable to fully download the lists of available packages that it uses, leaving a corrupted file behind in /var/lib/apt/lists/partial/ which causes the problem that you experienced.

Anyway, glad it's fixed for you, now! :)

---

### Post by swy000 on 2007-08-24
nice nice...awesome... ill go post the link to this thread in the other VLC thread I opened....

wats funny is the last time i was downloading VLC, it did a sudo apt-update and it never finished, so that was it. 

Is there anywhere I can get a full understanding of what these commands are? (i can probably find them in the ubuntu documentation or just google actually :) )

thnx again!

---

### Post by jamvegan on 2007-08-24
A good overview of many of the commands used in this thread can be found in [Using the Terminal]("https://help.ubuntu.com/community/UsingTheTerminal").

As far as getting a deeper understanding of configurations and other issues, the Ubuntu documentation is often helpful, but Google is almost always useful (in fact, I often find that the most useful results that I find in Google point here!).

Have fun with the UNIX/Linux command line. ;)

---

### Post by Herman on 2007-08-25
Hello jamvegan 

Thanks jamvegan, your solution worked for solving that same problem in a friend's computer, that I'm working on. :)

Regards, Herman :)

---

