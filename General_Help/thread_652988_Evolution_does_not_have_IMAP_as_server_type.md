---
title: "Evolution does not have IMAP as server type"
date: 2007-12-29
forum: General Help
---

### Post by kolslorr on 2007-12-29
Hello pple....

ok i admit I am an idiot, i 'upgraded' my gutsy Evolution today to the Hardy pre-release, because I'd like to use the built-in Google calendar support.

After upgrade, Evolution totally broke, and I have to reinstall back the one from main repo...

Alright... the reinstallation broke many other stuffs.... like the gnome-panel.. but i somehow manage to fix all these...

EXCEPT.... Reinstalled Evolution doesnt work.... particulary... the IMAP support is MISSING. :(

I have installed from Synaptics all Evolution related plugins... including the IMAP one... but still no good...

See the attachment pls... theres no IMAP server type i can find from the drop down...

:(:(:(

---

### Post by kolslorr on 2007-12-29
anyone... pls help...

or... tell me how to properly reinstall evolution... pls...

:(:(

---

### Post by kolslorr on 2007-12-30
wow... what a good forum

---

### Post by RC Howe on 2007-12-30
you may want to try in the console *sudo dpkg-reconfigure evolution*, or *sudo apt-get remove evolution* then *sudo apt-get install evolution*

---

### Post by kolslorr on 2007-12-30
> **RC Howe said:**
> you may want to try in the console *sudo dpkg-reconfigure evolution*, or *sudo apt-get remove evolution* then *sudo apt-get install evolution*

Thank you sir, i will try the reconfigure tonight...

not very optimistic abt the remove and install though... as I have tried the same thing via synaptics...

---

### Post by kolslorr on 2007-12-31
Unfortunately, nothing works. 

Evolution is still broken, and I am surprised a total reinstallation doesnt help. Have to switch back to Thunderbird.

File a bug - [https://bugs.launchpad.net/ubuntu/+bug/179507](https://bugs.launchpad.net/ubuntu/+bug/179507)

---

### Post by jeffus_il on 2007-12-31
Thunderbird has Google calendar support.

Install the "lightning" plugin, it works with Google.

---

### Post by dcstar on 2007-12-31
> **kolslorr said:**
> Unfortunately, nothing works. 

Evolution is still broken, and I am surprised a total reinstallation doesnt help. Have to switch back to Thunderbird.
.........]

Why should a re-install to an old version somehow "downgrade" the data structure which has probably been changed?

Rename the (hidden) .evolution directory, restart Evolution and then manually copy the mail files back from the old directory.

---

### Post by kolslorr on 2007-12-31
> **jeffus_il said:**
> Thunderbird has Google calendar support.

Install the "lightning" plugin, it works with Google.

Yup... i know... and I am using it now...

the thing is... Multisync ONLY works with Evolution... and I would like to sync up my google calendar with my K800i phone... 

Unless u tell me that its possible to sync thunderbird+lightning with my phone?... then i wld gladly ditch Evo forever and ever.

:)

---

### Post by kolslorr on 2007-12-31
> **dcstar said:**
> Why should a re-install to an old version somehow "downgrade" the data structure which has probably been changed?

Rename the (hidden) .evolution directory, restart Evolution and then manually copy the mail files back from the old directory.

Hello sir, I did what you said earlier too... in fact i totally remove the .evolution folder under my profile... relaunch evo... and still... the Receiving Server Type is still missing POP or IMAP....

any other suggestions? :confused::confused:

---

### Post by forestpixie on 2007-12-31
have you tried doing a purge and reinstall once the hidden folder has been moved

---

### Post by kolslorr on 2007-12-31
> **forestpixie said:**
> have you tried doing a purge and reinstall once the hidden folder has been moved

can u kindly tell me how to do a purge uninstall?...

sorry, newbie here... :lolflag:

---

### Post by forestpixie on 2007-12-31
don't be sorry - 8 months ago I wanted to know how to bump threads :D

```
sudo apt-get remove --purge <*packagename*>
```

---

### Post by kolslorr on 2007-12-31
> **forestpixie said:**
> don't be sorry - 8 months ago I wanted to know how to bump threads :D

```
sudo apt-get remove --purge <*packagename*>
```

:confused::confused::mad::mad:

Purge... doesnt work...

just to let u all know.. after purging... i did a 'find | grep evolution' at root... and remove ALL evolution related files and folders.... still no good....

I guess this evolution isnt designed for reinstallation... what crap...

I'll wait for Hardy to do a total reinstall of Ubuntu... and that will definitely fix it...

but still... Evolution is crap if it doesnt allow simple reinstallation.

---

### Post by forestpixie on 2007-12-31
you could try to install ubunut-desktop again if you've not changed much else

sudo aptitude install ubuntu-desktop

tbh it doesn't make a lot of sense to me why it won't work

what exactly do you get in the dropdown server type box

---

### Post by kolslorr on 2007-12-31
finally i got found the way to take screenshot of the dropdown!!!....

I have even tried to compile 2.12.2 from scratch.... and that gave me even more problem... i give up...

---

### Post by forestpixie on 2007-12-31
I have no idea what's going on there then - have you looked in the hardy forum to see if there's anything there

---

### Post by dcstar on 2007-12-31
> **kolslorr said:**
> ......
but still... Evolution is crap if it doesnt allow simple reinstallation.

Rubbish, Evolution is tightly integrated into the Gnome desktop and newer versions can make significant changes to that environment.

Just because you decided to try and force a version of Evolution designed for a later desktop onto a system that it was never intended to run on and then experience problems, is not the fault of the Evolution designers.

There is a reason that later versions of Evolution are rarely made available as backports, and that is because they break things in the Gnome environment, as you should now realise.

---

### Post by forestpixie on 2007-12-31
> **dcstar said:**
> Just because you decided to try and force a version of Evolution designed for a later desktop onto a system that it was never intended to run on and then experience problems, is not the fault of the Evolution designers.

+1

to be honest - as a 'newbie' myself I'd not be trying to play with hardy stuff just yet - I had enough fun with gutsy when it was nearly beta!

And I had to do a reinstall too - all part of the learning

---

### Post by kolslorr on 2007-12-31
> **dcstar said:**
> Rubbish, Evolution is tightly integrated into the Gnome desktop and newer versions can make significant changes to that environment.

Just because you decided to try and force a version of Evolution designed for a later desktop onto a system that it was never intended to run on and then experience problems, is not the fault of the Evolution designers.

There is a reason that later versions of Evolution are rarely made available as backports, and that is because they break things in the Gnome environment, as you should now realise.

okok, in the very first post i already said I am an idiot... so do bear with me. :)

I acted smart to try the new Evolution... yes.. it didnit work and I had no complaint.... 

my only grunt is... why is it so difficult to do a simple reinstallation??? 

Dont get me wrong, I am prepared to reinstall Ubuntu totally if such dumb things happen due to my stupidness... i just like to find out if there is an easier way out... and reinstalling a piece of software shd not be too difficult to do.

---

### Post by kolslorr on 2007-12-31
> **forestpixie said:**
> +1

to be honest - as a 'newbie' myself I'd not be trying to play with hardy stuff just yet - I had enough fun with gutsy when it was nearly beta!

And I had to do a reinstall too - all part of the learning

yeah... no problem... i am learning too... and it has been fun... 

:lolflag::lolflag:

---

### Post by forestpixie on 2007-12-31
I'd be inclined to bite the bullet now after a couple of days - hope someone else can deliver a ray of sunshine

but if not - new years resolution - carry on installing things that break - cos it just adds to the learning :)

---

### Post by dcstar on 2007-12-31
> **kolslorr said:**
> 
..........
my only grunt is... why is it so difficult to do a simple reinstallation??? 

Dont get me wrong, I am prepared to reinstall Ubuntu totally if such dumb things happen due to my stupidness... i just like to find out if there is an easier way out... and reinstalling a piece of software shd not be too difficult to do.

It is NOT a "simple reinstallation", **you** have broken the underlying environment that Evolution relies upon and runs in.

You **might** be able to escape by creating a new user account and seeing if Evolution behaves under a totally fresh user environment, but it is still possible that critical system configuration files have been changed and the only way out is to back up your user data and reinstall Ubuntu.

---

