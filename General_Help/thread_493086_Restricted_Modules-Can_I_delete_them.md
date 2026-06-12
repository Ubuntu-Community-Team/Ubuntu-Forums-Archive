---
title: "Restricted Modules-Can I delete them?"
date: 2007-07-05
forum: General Help
---

### Post by dkaddict on 2007-07-05
I really don't know what to do? I just read this post>>>

[http://ubuntuforums.org/showthread.php?t=484775&highlight=Latest+updates+2.6.20-16+restricted+modules](http://ubuntuforums.org/showthread.php?t=484775&highlight=Latest+updates+2.6.20-16+restricted+modules)

and would like to get rid of the 'restricted modules' packages that have been installed in my machine since I upgraded to Feisty. I THINK??? 

I am unsure if removing them will mess my comp up. As it stands, however, I am having similar problems as the person whos post I have linked above. My CD rom, which has always worked 100% A ok in Ubuntu is, it seems, having a go at becoming an AI. For example, I am happily surfing the web, listening to some tunes on one of my prefered net-radio stations, you know, the usual stuff, when al of a sudden my desktop is telling me I have inserted a cd into the cd-rom drive. I haven't done so, obviously, and the only way to return my system to its correct state is to reboot (NOT GOOD). If no reboot (log out then log in doesn't rectify my prob) I cannot open my cd rom drive. Right clicking the phantom icon and choosing 'eject' does zilch and pressing the little button on the actual drive does zilch too.

Ok, I may be jumping the gun in blaming the restricted modules packages but at the end of the day I can't see why I need them. I don't have any need for AIGLX as I have a crappy Via graphics set up which uses the Openchrome driver. I don't need 'mad wifi' as my wireless works fine. Blah blah blah...

Is there any way of getting rid of these seemingly unnecessary packages without creating the need for a fresh install? I am also pretty sure that I read somewhere on these forums that the latest restricted modules update screwed peoples wireless conections up. I haven't installed these two elements of the latest update yet for all of the above reasons. I get hassled by update notifier to install them when I boot but I can live with that. Obviously, if I don't have these packages, I wont get hassled so that would be a bonus.

I am really out of my depth with stuff that is to do with the Kernel so any advice would be well appreciated. If anyone knows what I mean?

Cheers

happy days

peace

dk

---

### Post by az on 2007-07-05
> **dkaddict said:**
> I really don't know what to do? I just read this post>>>

[http://ubuntuforums.org/showthread.php?t=484775&highlight=Latest+updates+2.6.20-16+restricted+modules](http://ubuntuforums.org/showthread.php?t=484775&highlight=Latest+updates+2.6.20-16+restricted+modules)

and would like to get rid of the 'restricted modules' packages that have been installed in my machine since I upgraded to Feisty. I THINK??? 

I am unsure if removing them will mess my comp up. As it stands, however, I am having similar problems as the person whos post I have linked above. My CD rom, which has always worked 100% A ok in Ubuntu is, it seems, having a go at becoming an AI. For example, I am happily surfing the web, listening to some tunes on one of my prefered net-radio stations, you know, the usual stuff, when al of a sudden my desktop is telling me I have inserted a cd into the cd-rom drive. I haven't done so, obviously, and the only way to return my system to its correct state is to reboot (NOT GOOD). If no reboot (log out then log in doesn't rectify my prob) I cannot open my cd rom drive. Right clicking the phantom icon and choosing 'eject' does zilch and pressing the little button on the actual drive does zilch too.

Ok, I may be jumping the gun in blaming the restricted modules packages but at the end of the day I can't see why I need them. I don't have any need for AIGLX as I have a crappy Via graphics set up which uses the Openchrome driver. I don't need 'mad wifi' as my wireless works fine. Blah blah blah...

Is there any way of getting rid of these seemingly unnecessary packages without creating the need for a fresh install? I am also pretty sure that I read somewhere on these forums that the latest restricted modules update screwed peoples wireless conections up. I haven't installed these two elements of the latest update yet for all of the above reasons. I get hassled by update notifier to install them when I boot but I can live with that. Obviously, if I don't have these packages, I wont get hassled so that would be a bonus.

I am really out of my depth with stuff that is to do with the Kernel so any advice would be well appreciated. If anyone knows what I mean?

Cheers

happy days

peace

dk

sudo apt-get remove linux-restricted-modules*


It will tell you that it will remove the linux-generic package along with that, but don't worry, you will still have the linux-image-generic package installed.

---

### Post by dkaddict on 2007-07-05
> **az said:**
> sudo apt-get remove linux-restricted-modules*


It will tell you that it will remove the linux-generic package along with that, but don't worry, you will still have the linux-image-generic package installed.

Ok,

Big thanx for taking the time to reply Az!

I will give 'apt-get remove...restricted-modules' a go. Gotta admit I have this feeling of impending doom though. 

If, hypothetically, removing the said package(s) has a detrimental effect on my beloved Ubuntu, I can simply 'sudo apt-get install linux-restricted-modules' and all will be as it was (with the addition of the updates I have absolutely no need for whatsoever)? Yeah???

peace & thanx again

dk

---

### Post by az on 2007-07-05
> **dkaddict said:**
> Ok,

Big thanx for taking the time to reply Az!

I will give 'apt-get remove...restricted-modules' a go. Gotta admit I have this feeling of impending doom though. 

If, hypothetically, removing the said package(s) has a detrimental effect on my beloved Ubuntu, I can simply 'sudo apt-get install linux-restricted-modules' and all will be as it was (with the addition of the updates I have absolutely no need for whatsoever)? Yeah???

peace & thanx again

dk

sudo apt-get install linux-restricted-modules-generic

But if your graphics card and wireless are not using restricted modules, then you are good to go.

---

### Post by dkaddict on 2007-07-06
Nice one Az,

Removed the restricted and all is still working as it always has.

God bless you m8

peace

dk

---

