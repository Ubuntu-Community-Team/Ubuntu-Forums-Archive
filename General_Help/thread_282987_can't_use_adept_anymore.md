---
title: "can't use adept anymore"
date: 2006-10-23
forum: General Help
---

### Post by rienm on 2006-10-23
hello

I posted my problem on the dutch forum, but till sofar no answer. This morning I used adept to install Sun JR programs, the program stuck, I closed it and got a warning that processes were not finished; stopped it in spite of this warning.
When I try to start Adept I get the folowing warning "

You will not be able to change your system settings in any way (install, remove or upgrade software), because another process is using the packaging system database (probably some other Adept application or apt-get or aptitude). Please close the other application before using this one.

I can't find processes named apt-get or aptitude inthe list of active processes.So I can't close any application.

Shutting down the computer does not help.
Is there anyone who can help me ?

---

### Post by aysiu on 2006-10-23
Have you tried any of these? ```
sudo killall adept
sudo killall dpkg
sudo dpkg --configure -a
```

---

### Post by rienm on 2006-10-23
thanks aysiu it worked out fine, but......
I get an announcement from the updater there are packages to update, when I try this the proces freezes because a confirmaton is expected that I can't give. 
When I try to remove these packages ( sun-java-bin and sun-java-jre ) I get an anouncement as" can not execute the changes. possibly problem in downloading some packages or it will brake some packages.

what can i do ???

---

### Post by rienm on 2006-10-23
should i remove the files file:///var/cache/apt/archives/sun-java5-bin_1.5.0-06-1_i386.deb
file:///var/cache/apt/archives/sun-java5-fonts_1.5.0-06-1_all.deb
file:///usr/share/app-install/desktop/sun-java5-java.desktop
file:///var/cache/apt/archives/sun-java5-jre_1.5.0-06-1_all.deb
 
since sun-java runtime has not been installed? When i remove the files out  of /var/cache/apt/archives package installer won't see them anymore ??

---

### Post by aysiu on 2006-10-23
Yes, you can try: ```
sudo aptitude clean
``` That clears out the /var/cache/apt/archives folder.

---

### Post by rienm on 2006-10-23
thanks I will try out tomorrow, its now 00.50 ,time to go to sleep
I'll let you know 
Rien

---

### Post by rienm on 2006-10-24
Well, I did remove with the rm command the files
/var/cache/apt/archives/sun*.

After restart package updater still mentionned the same files to update and, using Adept the sun packages were highlighted as updatable.How can I remove this ? 
How can I update these packages, while downloading does not work ( hangs with 5 % => details ==> screen in which a knob <OK> is to be seen, doubble clicking or a return does not have any effect, so Adept keeps on hanging

I feer that downloading other packages / updates will not work because of the problem with sun-java packages, so either I wont to remove these packages or to install them

answers ??

---

### Post by rienm on 2006-10-24
hope AYSIU reads this, see my previous questions please; re install Kubuntu??
Other solutions ??

---

### Post by aysiu on 2006-10-24
Can you post the output of this command? ```
sudo aptitude update && sudo aptitude dist-upgrade
```

---

### Post by rienm on 2006-10-24
hello Aysiu , well here it is, in dutch..
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd... Klaar
Initialiseren van pakketstatussen... Klaar
Building tag database... Klaar
Haal:1 [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy Release.gpg [189B]
Haal:2 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Haal:3 [http://kubuntu.org](http://kubuntu.org) dapper Release.gpg [189B]
Geraakt: [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Geraakt: [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy Release
Haal:4 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper Release.gpg [189B]
Haal:5 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Geraakt: [http://kubuntu.org](http://kubuntu.org) dapper Release
Geraakt: [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper Release
Geraakt: [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper-updates Release
Fout [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy Release

Geraakt: [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Haal:6 [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy Release [8288B]
Geraakt: [http://kubuntu.org](http://kubuntu.org) dapper/main Packages
Geraakt: [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Geraakt: [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Geraakt: [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper/main Packages
Negeer [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy Release
Geraakt: [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper/restricted Packages
Geraakt: [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper/main Sources
Geraakt: [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Packages
Geraakt: [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Geraakt: [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Packages
Geraakt: [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper/restricted Sources
Geraakt: [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper/universe Packages
Geraakt: [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper/multiverse Packages
Geraakt: [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper/universe Sources
Geraakt: [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper/multiverse Sources
Geraakt: [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper-updates/main Packages
Geraakt: [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper-updates/restricted Packages
Geraakt: [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper-updates/main Sources
Geraakt: [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper-updates/restricted Sources
8481B opgehaald in 0s (15,3kB/s)
Pakketlijsten worden ingelezen... Klaar
W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy Release: The following sign                                                              atures couldn't be verified because the public key is not available: NO_PUBKEY F                                                              120156012B83718
W: U kunt misschien 'apt-get update' uitvoeren om deze problemen te verhelpen
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd... Klaar
Initialiseren van pakketstatussen... Klaar
Building tag database... Klaar
De volgende pakketten zullen worden opgewaardeerd:
  libpq4 libqt3-mt sun-java5-bin sun-java5-jre
4 pakketten opgewaardeerd, 0 nieuwe geïnstalleerd, 0 te verwijderen en 0 niet opwaarderen.
Heb 29,7MB/32,8MB archieven nodig. Na uitpakken zal 83,3MB worden gebruikt.
Wilt u verder gaan? [Y/n/?]

---

### Post by aysiu on 2006-10-24
Okay, so there's a GPG signature error. That's okay. What happens if you say "yes"? Does it want to install these packages? What does it want to do? My Dutch is a little rusty. ```
libpq4 libqt3-mt sun-java5-bin sun-java5-jre
```

---

### Post by rienm on 2006-10-24
it is 00.35 here in Holland, so i am going to sleep

some translations: haal = get
                   geraakt = touched
                   fout = wrong, false
                   negeer = ignore
                   pakket = package
                   boom - tree
                   klaar = ready
but perhaps you understood the structure

tomorrow morning i hope to see your advice

Rien

---

### Post by rienm on 2006-10-24
SUCCEDED !!!!!!!!!

Thank you AYsiu very, very much.
Now I could confirm the licence agreement

I will sleep better now 

Rien

---

### Post by Pelekophori on 2006-10-24
> **rienm said:**
> 
How can I update these packages, while downloading does not work ( hangs with 5 % => details ==> screen in which a knob <OK> is to be seen, doubble clicking or a return does not have any effect, so Adept keeps on hanging


I had what I think was probably the same problem installing sun java.  The "ok" I got stuck on was to accept the license, but as you've noted pressing enter or clicking on the ok wouldn't work.  It was very frustrating.  However I accidentally solved the problem.  I mistakenly brushed another key which caused the window's focus to shift to the ok, thereby highlighting it.  At that point pressing enter worked and the rest of the package downloaded and installed ok.  

Now the million dollar question is what was the key?  This is where my answer gets a bit crap, because I'm not entirely sure.  However I think that it was the tab key.  So try pressing tab when you get that ok and see if it highlights.  If it does then pressing enter should work.

---

### Post by rienm on 2006-10-25
thanks !

---

### Post by Jason Quinn on 2006-10-31
Man, I'm having the same problem. It appears that java is asking a confirm question during the installation (which is show when you click on "Show Details") but I can't figure out how to confirm it.

Jason

---

### Post by Arby on 2006-11-01
Jason: I hit the exact same problem just now. The solution is to install java using the commandline with the following commands ```
sudo apt-get install sun-java5-jre
sudo apt-get install sun-java5-bin
``` When you do it from the commandline the license agreement is displayed correctly and you can confirm it by using tab until OK is highlighted.

Everything worked just fine for me after that. I'm going to log this at launchpad as a bug in adept, I was just checking to see if anyone else has had the same problem :)

---

