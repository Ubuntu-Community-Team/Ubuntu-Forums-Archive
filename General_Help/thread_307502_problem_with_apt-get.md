---
title: "problem with apt-get"
date: 2006-11-26
forum: General Help
---

### Post by BlueStreak on 2006-11-26
Ever since attempting to install openclipart I'm having big problems with managing packages.  Everytime I attempt to do something in either synaptic, apt-get, aptitude, automatix I get the following error:

E: openclipart: files list file for package `openclipart-png' contains empty filename

The clipart install failed saying it failed to fetch some files from the server (it wasn't real specific).  In synaptic it appears to be installed but any attempts to reinstall or remove result in the above error.

Note that I get this error regardless of what package I'm attempting to remove or install, even those completely unrelated to openclipart.

Please help.  thank you!

---

### Post by finferflu on 2006-11-26
Try this command:

```
sudo apt-get -f install
```

It usually solves some problems..

---

### Post by BlueStreak on 2006-11-26
Thanks finferflu, I tried that and got:

Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Still have the problem :(  I'm at a loss

---

### Post by BlueStreak on 2006-11-26
anyone else?  Sorry to bump this but I'm kinda screwed for getting new packages until we figure this out :(  Please help!

---

### Post by ardvark71 on 2006-11-26
Hi Bluestreak...

Kind of new with Linux so this might sound like a shot in the dark or completely dumb but I'm assuming your installation of openclipart was completed part way, meaning you have some files still installed. Is it possible to locate the main clipart folder and delete it as well as look around for other references to it?

Only think I can think of if your ability to install and uninstall is made defunct by the other services unless someone here knows where and how to change code or configurations.

Good luck!

:KS

---

### Post by BlueStreak on 2006-11-26
ardvark71, not dumb at all.  You're right that it was completed part way.  I've tried manually deleting all the associated files and it still won't work.  Seems no matter what I get that error :( !

---

### Post by ardvark71 on 2006-11-26
Hi Bluestreak...

Yikes! I apologize, that is as far as I know what to suggest.:(  Hope someone who knows more of what to do here will post...

Best Regards...

:KS

---

### Post by David Corrales on 2006-11-27
When I got that I did as ardvark71 said, delete all the files half installed. To see which files -exactly- got installed, go into the package properties inside synaptic. Then, be sure to remove all of them and rerun **sudo apt-get remove openclipart**. It'll complain about the package not having files but hopefully will be deleted from the package base and you'll get a functional apt again.

---

