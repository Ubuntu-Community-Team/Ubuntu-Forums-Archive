---
title: "How do you reset your packages back to the original repos?"
date: 2019-12-07
forum: General Help
---

### Post by gregoryshock on 2019-12-07
Please bare with me.  My short story is going to talk about Linux Mint first.  I found the answer to that question but it created another question in my mind.  I also run Xubuntu 18.04 on all my other computers.  My final question is about Xubuntu, and I assume whatever answer I might get, will probably work with all the Ubuntu flavors.

Tue Jun 12 21:16:05 2018 I was doing some DVD stuff in Linux Mint 18.3.  I was advised to install the latest FFmpeg.  The PPA was connected too was ppa:jonathonf/ffmpeg-3.  And that was how I left things until now.  The [PPA](https://launchpad.net/~jonathonf/+archive/ubuntu/ffmpeg-3) went away.  I had only two options.  1) Try to downgrade FFmpeg or 2) Try to upgrade it.  I first tried option 2, and it uninstalled Winff, my favorite graphical front end for quickly converting things.  So next I tried downgrading it.  That is when things got really bad.  There was other software depending on the newer version of FFmpeg, and things got lost, and now they are kinda reinstalled.  I recently learned that Winff is [retired](https://www.biggmatt.com/p/winff.html).  A guy on the Linux Mint Forums [helped](https://forums.linuxmint.com/viewtopic.php?f=47&t=306773#p1724721) me.  But it got me wondering.  **If something like this happens on a Distro like Xubuntu what do you do?  How do you reset or downgrade your packages back to the original repos?**

---

### Post by mörgæs on 2019-12-07
> **gregoryshock said:**
> I was advised to install the latest FFmpeg.

Then I would install the latest Mint or Buntu release. Adding a new PPA to an old release doesn't make sense to me. 

For the same reason I never downgrade or reset to an original repo. I tried to use PPA's some times back in the good old days but in the end it often turned out to be a waste of time.

---

### Post by CatKiller on 2019-12-07
> **gregoryshock said:**
> If something like this happens on a Distro like Xubuntu what do you do?  How do you reset or downgrade your packages back to the original repos?

There's a tool that does exactly that, called ppa-purge. It removes the packages from the PPA, back to the versions from the repositories, and then removes the entries from your sources.list.

---

### Post by gregoryshock on 2019-12-07
> **mörgæs said:**
> Then I would install the latest Mint or Buntu release. Adding a new PPA to an old release doesn't make sense to me. 

For the same reason I never downgrade or reset to an original repo. I tried to use PPA's some times back in the good old days but in the end it often turned out to be a waste of time.

I only use PPAs when it's necessary.  Because I know they can cause problems.  I never ran into problem where the PPA actually went away, and was stuck like this.  I am going to change the OS on that computer.  I just haven't decided on which one I'm going to change it too.  I experimented with Xubuntu 18.04 on an external ssd in the icy dock.  It worked really good.  But I have a bug in an application that I would need to start another post about.

> **CatKiller said:**
> There's a tool that does exactly that, called  ppa-purge. It removes the packages from the PPA, back to the versions  from the repositories, and then removes the entries from your  sources.list.

Do you mean this command right here?
```
sudo apt-get install ppa-purge && sudo ppa-purge ppa:jonathonf/ffmpeg-4
```
Found on this website/instruction:  [http://ubuntuhandbook.org/index.php/2018/10/install-ffmpeg-4-0-2-ubuntu-18-0416-04/](http://ubuntuhandbook.org/index.php/2018/10/install-ffmpeg-4-0-2-ubuntu-18-0416-04/)

I tried it but it was going to remove a lot more then I wanted to remove.  Scared me so I didn't go through with it.

---

### Post by mörgæs on 2019-12-07
> **gregoryshock said:**
> But I have a bug in an application...

Yes, 18.04 is a museum for old bugs. Better to try to see if it's fixed in 19.10.

---

### Post by gregoryshock on 2019-12-07
> **mörgæs said:**
> Yes, 18.04 is a museum for old bugs. Better to try to see if it's fixed in 19.10.

What I don't like about Xubuntu 19.10 is that if you have an Nvidia card, it automatically installs the drivers.  That made it harder for me to do the testing I wanted.  I also had problems with compton, which I needed to solve screen tearing on intel graphics.

---

### Post by CatKiller on 2019-12-07
> **gregoryshock said:**
> I tried it but it was going to remove a lot more then I wanted to remove.  Scared me so I didn't go through with it.

Packages depend on packages, which depend on packages, and they all have to be the correct version. That's why PPAs exist, which contain all of those dependencies for packages newer than the ones in the repositories, and why ppa-purge exists, to unscramble that egg. 

All of the packages that would be removed or downgraded are those that were installed when you added the PPA in the first place. That's potentially a lot of packages, depending on the specifics of the PPA.

---

