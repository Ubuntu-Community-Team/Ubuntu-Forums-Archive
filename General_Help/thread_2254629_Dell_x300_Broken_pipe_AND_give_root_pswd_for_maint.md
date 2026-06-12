---
title: "Dell x300 Broken pipe AND give root pswd for maint"
date: 2014-11-28
forum: General Help
---

### Post by zeezee22 on 2014-11-28
Heya,

I have a Dell x300 on xubuntu 12.04 that ran fine until I had it up with a problem with the audio.... it hadn't initialized - so I rebooted and was rewarded with a broken pipe for the reaon of 'failed to add phy80211' - I think, because it's doesn't always say so and when it does.... too fast! 

Anything I have read suggests going into terminal, yet dropping to shell root menu asks for 'root password for maintenance' - so I give it the password and it gives me the fingers in ears treatment by asking the same question again. I have been around in circles looking for a workaround and the best I come up with is adding init=/bin/bash to the kernel startup... and it just looks at me, blinkingly as if I asked it for a coffee. I don't feel confident I have been doing that part right, because I don't find anything that says 'kernel' to add the init command to.

If you haven't already guessed... I'm in that dangerous land of I know something about these machines, tho I am not too sure altogether what.... so please bear with me... please?

Aaaanyways, forgetting about the password, I have asked it to repair broken packages and it complains that it doesn't have network access, so I ask it to Enable networking and it does that, then just sits there and smiles sweetly, without giving so much as a terminal prompt to go on with. Someone else suggested someone to  enable networking thru command prompt instead of recovery menu... which we have already established, doesn't work for me here...

So yeah.... I'm felling somewhat 'Grrr...' and all, ready to rip the HDD out and strangle it on another machine until it surrenders the data before formatting it again yet it's an IDE.... I'm just in a grump over having to download yet another cd to boot live, that I don't really know what to do with right now...

Has anyone got any thoughts or ideas? I'm feeling backed into a corner here....

Many thanx.

Zz

---

### Post by mörgæs on 2014-11-30
You don't have to remove the hard disk to save the files. It's easier to do in a live boot.

---

### Post by zeezee22 on 2014-12-01
Yea, I got that far. I'm using live boot right now (with the aid of a few 'how to.. with live cd' threads), popping all over the web to see if there's anything else useful to my limited understanding before I rip the thing apart to start again - very Windows-esque! :o
The only practical course of action I've managed to devise is to do a file system check, which resulted nothing I can see.
Right now I'm at the part looking for data to salvage as well as a "repair broken packages with live cd" instruction manual (which sounds much 'more' and 'bigger' and 'better' than "check file system"!)
Consider this one 'solved' and let's move on from here, may we?

---

### Post by zeezee22 on 2014-12-01
For the benefit of any readers to this story, left hanging....
I really dunno what happened - tho' none of my data showed up in the file system to be saved! I did have a few users, yet only found one listed in /home, and all of the folders in there were comepletely empty.
Following advice found elsewhere, I ran gparted to check the file system and, knowing the partition was pretty full up, I made three partitions into two. The system booted fine after that - minus all data and all users. I looks like I've got a fresh install without doing a fresh install. 
Meh, I may as well do a fresh install from here.
Case closed.

---

### Post by mörgæs on 2014-12-01
> **zeezee22 said:**
> 
Consider this one 'solved' and let's move on from here, may we?

You may. Please use Thread Tools for marking the thread solved.

---

