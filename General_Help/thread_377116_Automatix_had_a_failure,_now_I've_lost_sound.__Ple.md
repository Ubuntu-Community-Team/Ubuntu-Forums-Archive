---
title: "Automatix had a failure, now I've lost sound.  Please help!"
date: 2007-03-05
forum: General Help
---

### Post by zami on 2007-03-05
I hope someone can help me with this.  I very happily used Automatix to install a few things -
-AUD-DVD Codecs
-Listen Media Manager
-Media Players
-Multimedia Codecs
-RealPlayer
-Sun Java 1.6 JRE

All those went fine one by one, and had restarts between the installs.

Then I tried to install two things at once -
-Flash Player
-MPlayer and FF Plugin

One installation failed... it said something about not being able to connect to some remote something.  I didn't pay too much attention as these were  last and least important things I was installing.  I figured I could try again later and it might connect.  No biggy.

**But!  Now I have no sound!**

I've checked nothing is muted or turned down.
I've gone into System > Preferences > Sound and tested every bloody option available with no results.

I can see in Amarok (for example) that music files are trying to play, I see the little sound analyzer going.  But I hear nothing.

I've since tried reinstalling / uninstalling / reinstalling the two installs that originally failed and caused the problem, and they've since installed fine, but I've still got no sound.  Tried uninstalling them - still no sound.

Any clues where I should go from here?

-zami

---

### Post by strabes on 2007-03-05
In amarok you have to install specific codecs to play mp3s: ```
sudo aptitude install libxine-extracodecs
```

I would recommend not using automatix because it tends to break upgrades and things. My installs seem to last much longer without breaking when I don't automatix. Besides, you can get everything you need from [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats).

Try running "alsamixer" and unmuting and turning everything up.

---

### Post by zami on 2007-03-05
I've got the libxine-extracodecs installed (double checked) so that's not it, but I thank you for the suggestion.

I'm not usually a fan of Automatix - it's very convenient *when* it works, but as you said, it's a lot less headache down the road if you just install everything standalone.

Uhg.  I just got lazy.  I've been wrestling with getting Ubuntu on my husband's computer for four or five days now, and it's just been one headache after another after another with this machine.  I allready installed all the codecs and windows fonts manually this morning - I had to reformat and reinstall Ubuntu this afternoon (long, dull, painful story there) and thought I'd just let Automatix do the work for me this time.   

Cripes.  I think his computer is cursed.  It must be.  There is no other explanation for EVERY step of the way being this difficult on this machine!

I'm going to go cry now.  Or get in a brawl. I'm not sure which.  Mabye both.

-zami

---

### Post by sdowney717 on 2007-03-05
do this, maintain a complete partition backup of ubuntu, you can even use norton ghost for this.
I make sure I have working backup copy so when it breaks, I just restore the whole darned thing. It only takes a few minutes.

The way I do it is I keep a winxp partition on the drive. I boot into windows and backup my partitions. I also do this with fedora and xp.

---

