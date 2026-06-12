---
title: "Making custom Ubuntu distro"
date: 2014-10-14
forum: General Help
---

### Post by Louis_Levene on 2014-10-14
I am not sure if I am posting this in the right place or not as this is my first time doing this, but I have a question about remastersys. I am trying to make a customized ubuntu distro using remastersys and one of the things I want it to do is hide the unity launcher by default, however when I do this and create the distro it still doesn't hide. Any help would be much appreciated as I have been searching for weeks still without an answer.

---

### Post by ajgreeny on 2014-10-14
I thought remastersys had gone belly-up and was no longer developed ar available, but I may be wrong.  It does apparently still work in Ubuntu 14.04 according to [http://ubuntuforums.org/showthread.php?t=2216890](http://ubuntuforums.org/showthread.php?t=2216890)

However have a look at [https://help.ubuntu.com/community/InstallCDCustomization](https://help.ubuntu.com/community/InstallCDCustomization) and also [https://launchpad.net/uck](https://launchpad.net/uck) which might help you with possible alternatives.

---

### Post by Bucky Ball on 2014-10-14
Welcome. So you are successfully creating the ISO, installing it, but the Unity Launcher is not hiding as it was on the install that you've cloned? Is that actually the question? How to get it to hide on the 'remastered' custom ISO?

I use Clonezilla to create custom ISOs, personally, but it doesn't appear you are having any issue with that part of the process ... :-k

---

### Post by sudodus on 2014-10-14
Do you want an ISO file, from which the users can install their systems, or do you want to a ready-made installed system, that it already tweaked?

Maybe the setting to hide the Unity launcher is a user setting, that the end user is supposed to set individually. So if you find the skeleton for it (I think in /etc/skel) and tweak that, it might survive. But I'm guessing here, I have not done it.

---

### Post by Louis_Levene on 2014-10-14
Thanks so much for all the suggestions! I've already tried tweaking things in /etc/skel but I'm going to try all the other suggestions and maybe an alternative to remastersys and then ill post what happens.

---

### Post by Louis_Levene on 2014-10-14
i tried everything and still no luck, i think it has something to do with remastersys not saving my applications because i set the homepage on firefox to google.com and that changes back to the default ubuntu page too:mad:.... any idea? thanks in advance!

---

### Post by Bucky Ball on 2014-10-14
Well, the Firefox settings are stored in the file /home/user/.mozilla. Your profile is there and so it the default homepage setting. Unless you copied your /home into the custom ISO it would be gone in the new install. That could be what's happening with the Unity launcher setting also (I imagine it is, in hindsight). That would be in /home somewhere too, probably. Or /root perhaps. A wiser head would know. 

Clonezilla may give a better result as it clones the whole partition, as is, into an ISO if you want (from memory, but haven't used in awhile). Perhaps there's a setting in remastersys that allows this, too. But cloning your entire /home directory to an ISO would be problematic I'd imagine.

If you back up just the .mozilla directory and whatever controls the Unity launcher, do your regular ISO clone with remastersys, then replace those directories in the custom ISO with the backed up ones once you've installed the custom ISO, that should work. I know it will for Firefox. You only need the profile, actually, not the whole .mozilla folder. 

Know little about Unity. Never used it. 

Good luck. ;)

---

### Post by Louis_Levene on 2014-10-15
i think i found a fix! i installed compiz and then hid the launcher from there and then moved the compiz config file to etc skel and it worked thanks so much for the help everyone! :D

---

### Post by Bucky Ball on 2014-10-15
Excellent news. Well done and good luck. ;)

---

### Post by sudodus on 2014-10-16
> **Bucky Ball said:**
> Excellent news. Well done and good luck. ;)

+1

And many thanks for sharing your solution, Louis_Levene :-)

---

