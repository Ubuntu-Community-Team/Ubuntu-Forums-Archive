---
title: "how to install beryl on ubuntu 8.04"
date: 2008-06-22
forum: General Help
---

### Post by ravindukelum on 2008-06-22
how to install beryl on ubuntu 8.04 please help me from the scratch i got nvidia drivers and ubuntu 8.04 installed

---

### Post by Forlong on 2008-06-22
You don't. Beryl is a discontinued project. Use Compiz instead -- it's installed by default.

Go to *System &#8594; Preferences &#8594; Appearance &#8594; Visual Effects* to enable it.

And go here if you want to set it up much further: [http://forlong.blogage.de/article/2008/4/26/How-to-set-up-Compiz-Fusion-074](http://forlong.blogage.de/article/2008/4/26/How-to-set-up-Compiz-Fusion-074)

---

### Post by Canis familiaris on 2008-06-22
Beryl is now defunct. It has been merged with Compiz and now we have compiz fusion.
For enabling compiz:
System->Preferences->Appearance
And choose visual effects tab and select your option.

---

### Post by Canis familiaris on 2008-06-22
To have more options:
Go to Synaptic:
Search for compiz.
And install compizconfig-seetings-manager.
And after it is installed Go to:
 System->Preferences->Advances Desktop Effects Settings

---

### Post by Charles Sloan on 2008-06-30
> **Anurag_panda said:**
> To have more options:
Go to Synaptic:
Search for compiz.
And install compizconfig-seetings-manager.
And after it is installed Go to:
 System->Preferences->Advances Desktop Effects Settings

Great post!

---

### Post by hey_ram on 2008-06-30
hey!

i have been reading up about compiz or compiz-fusion on these forums and would like to give it a try...

i did the following:
1. i went to systems->preferences->appearances->visual effects and chose extra.
2. opened synaptic and searched for compiz. however, the package titled 'compizconfig-settings-manager' is not there. 

it does have a package titled 'compizconfig-backend-gconf'. and the check box next to it is already coloured, meaning its installed right? 

my question is:
1. does my system (ubuntu 8.04) have compiz installed?
2. what do i need to do to install it in case it is not there?

thanx..

---

### Post by conqeror on 2008-07-16
> **hey_ram said:**
> hey!

i have been reading up about compiz or compiz-fusion on these forums and would like to give it a try...

i did the following:
1. i went to systems->preferences->appearances->visual effects and chose extra.
2. opened synaptic and searched for compiz. however, the package titled 'compizconfig-settings-manager' is not there. 

it does have a package titled 'compizconfig-backend-gconf'. and the check box next to it is already coloured, meaning its installed right? 

my question is:
1. does my system (ubuntu 8.04) have compiz installed?
2. what do i need to do to install it in case it is not there?

thanx..
1. yes you have got compiz installed but you can install advanced desktop effects
2. you must add medibuntu to your repositories:
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
```<-write this command to terminal
```
deb http://packages.medibuntu.org/ hardy free non-free #Medibuntu for Ubuntu 8.04
```<-go to System->Administration->Software sources->go to Third-Party software tab->and add what i wrote in code

sry 4 my english:rolleyes:

---

### Post by Sef on 2008-07-16
1) Applications > Add/Remove > Search: CCSM 

2) Read Forlong's Blog on how to [set up Compiz-Fusion]("http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion").

---

### Post by steveneddy on 2008-07-17
From [this web site]("http://www.compiz-fusion.org/"):

> 
Compiz Fusion is the result of a merge between the well-known Beryl composite window manager and Compiz Extras, a community set of improvements to the Compiz composite window manager.


And we have seen the posts that Beryl is dead.

There is a separate area on Ubuntu Forums about Desktop Effects:

[http://ubuntuforums.org/forumdisplay.php?f=330](http://ubuntuforums.org/forumdisplay.php?f=330)

Here is a script to DL some extras for Compiz:

[http://ubuntuforums.org/showpost.php?p=5166887&postcount=34](http://ubuntuforums.org/showpost.php?p=5166887&postcount=34)

Do not run the script as root.

---

