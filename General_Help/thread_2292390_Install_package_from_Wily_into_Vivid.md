---
title: "Install package from Wily into Vivid"
date: 2015-08-27
forum: General Help
---

### Post by Dechcaudron on 2015-08-27
Hey there guys,

so a while ago octave released its 4th version, featuring (among others) decent GUI support. The thing is, while at the time I compiled the source to install it on my pc, some colleague also wishes to have that version installed (plus also having the ease to upgrade when new versions are added to the repo). The thing is, I've been exploring the repositories and while we run Vivid or lower, octave 4.0 is only available at Wily. Is there any way I can install that package from Vivid or lower? I if there is, I just cannot figure out which apt command to use.

Thanks beforehand,
Dechcaudron

---

### Post by grahammechanical on 2015-08-27
Ubuntu versions have their own repositories. So, Ubuntu wily werewolf (15.10) has Octave 4 in the Ubuntu Software Centre. There is not an apt-get command that you can use to install an application in vivid from the wily repositories. What you can do is upgrade to 15.10. Ubuntu 15.04 reaches end of life at the end of January 2016.

If you cannot wait that long, and you do not want to upgrade to 15.10 before it is released in October, then I suggest that you dual boot with 15.04 and 15.10. There are daily images available. I am using 15.10 right now. I use it daily and have done so since development started back in May. It is stable. But I always have an older version of Ubuntu installed just in case 15.10 gets broken. And I keep all my data on a separate partition. Then I do not lose any data and I can always access it from any installation of Ubuntu that I have.

If we are going to use these Ubuntu releases that only have 9 months support then I think it is sensible to dual boot with each new release before upgrading the previous version to the new one. In that way we can find out if the new version does everything that we want it to do.

[http://cdimage.ubuntu.com/ubuntu/daily-live/20150826/](http://cdimage.ubuntu.com/ubuntu/daily-live/20150826/)

Regards

---

### Post by monkeybrain20122 on 2015-08-27
Simple solution, just install with ppa. [https://launchpad.net/~octave/+archive/ubuntu/stable](https://launchpad.net/~octave/+archive/ubuntu/stable) 

```
sudo add-apt-repository ppa:octave/stable
sudo apt-get update
sudo apt-get upgrade
```

The first line adds the octave ppa to your sources, the second updates the database to reflect the fact that new software source has been added to the pool, the third upgrades octave along with other things for which upgrades are available (supposedly you have already had 3.8 installed)

No need to fool around with 15.10's repo or do a premature OS upgrade or other complicated things like dualboot with prerelease (??? Seriously??)

ppas is an easy way to get up to date software without waiting for Ubuntu "official releases" and having to go through the hassles and risks to upgrade the OS in order to just get new features for a few applications. It is one reason (a pretty big one) I use Ubuntu instead of Debian.

In any case Octave is quite easy to compile from source tarball. Have been doing that for a while (for experimental features not in official builds)

Edited: you also need liboctave-dev if your want to install octave toolboxes via pkg install -forge.

---

### Post by Dechcaudron on 2015-08-28
Wow guys thank you both. After reading documentation about ppa-s, I've decided to use @monkeybrain20122's solution, since it seems less of an overkill ;). But anyways thank you both. This is has been my first time seeking help in the Ubuntu forums, and all I can say is I'm delighted.

Thanks again!

---

