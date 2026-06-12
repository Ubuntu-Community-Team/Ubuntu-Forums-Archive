---
title: "APT now installs SNAPS ?"
date: 2021-04-27
forum: General Help
---

### Post by Shibblet on 2021-04-27
This all started in a different thread for different reasons:
[https://ubuntuforums.org/showthread.php?t=2461000]("https://ubuntuforums.org/showthread.php?t=2461000")

This ultimately led me to a completely different question...

Maybe I don't understand APT that well, but it always thought it was it's own package manager.
The other day I attempted to add a PPA for a Development branch of Chromium (as noted in the previous thread).

When I went to install it, even using APT, and after putting in the PPA... it launched SNAP to install Chromium!!!
So, I went to remove snap, and all of it's subsidiaries... and when I went to install Chromium again, it downloaded Snap on it's own and then installed the Chromium SNAP!!!

This is noted in this article at the bottom under "Gotcha."
[https://www.kevin-custer.com/blog/disabling-snaps-in-ubuntu-20-04/]("https://www.kevin-custer.com/blog/disabling-snaps-in-ubuntu-20-04/")

So... to the Questions...

[LIST]
[*]Why would APT force a SNAP install?
[*]Aren't they different package managers?
[*]Is this just the direction Ubuntu is going?
[*]Everything has to be Snaps whether you like them or not?
[/LIST]

---

### Post by Shibblet on 2021-04-27
Apparently this has caused some division...

From the below listed article:
> "Ubuntu is planning to replace the Chromium [Google's open-source browser and foundation for Chrome] repository package with an empty package, which installs the Chromium Snap. In other words, as you install APT [Debian's program for installing and managing DEB files] updates, Snap becomes a requirement for you to continue to use Chromium and installs itself behind your back. This breaks one of the major worries many people had when Snap was announced and a promise from its developers that it would never replace APT.

A self-installing Snap Store which overwrites part of our APT package base is a complete NO-NO. It's something we have to stop and it could mean the end of Chromium updates and access to the Snap store in Linux Mint."

[https://www.zdnet.com/article/linux-mint-dumps-ubuntu-snap/]("https://www.zdnet.com/article/linux-mint-dumps-ubuntu-snap/")

---

### Post by Frogs Hair on 2021-04-27
This is how chromium is listed in synaptic which I thought was a GUI for apt. It does show that it is a snap in the description and does install the snap.

---

### Post by Shibblet on 2021-04-27
> **Frogs Hair said:**
> This is how chromium is listed in synaptic which I thought was a GUI for apt. It does show that it is a snap in the description and does install the snap.

Yup.  I watched it happen in the terminal, and then went to Muon to look it up...
The problem is even if you uninstall SNAP, the Chromium-Browser will re-install SNAP in order to install itself!!!

---

### Post by CelticWarrior on 2021-04-27
If you're using the development branch PPA then it shouldn't.

---

### Post by Frogs Hair on 2021-04-27
The only way to get chromium is via snap or flatpack AFIK. There was a ppa at one time just to keep chromium up to date, but it's dead.

[https://launchpad.net/~chromium-daily/+archive/ubuntu/stable](https://launchpad.net/~chromium-daily/+archive/ubuntu/stable)

---

### Post by CelticWarrior on 2021-04-27
I emant this one: [https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev](https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev)

---

### Post by Shibblet on 2021-04-27
> **CelticWarrior said:**
> If you're using the development branch PPA then it shouldn't.
I agree, it **shouldn't.**

> **CelticWarrior said:**
> I emant this one: [https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev](https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev)
Yep.  Try installing that PPA, and then go to install Chromium-Browser.  You will get the SNAP no matter what.

It's almost like watching "West Side Story..." You know, where one gang attempts to establish dominance with SNAPS.

---

### Post by CelticWarrior on 2021-04-27
> [COLOR=#000000]Yep. Try installing that PPA, and then go to install Chromium-Browser. You will get the SNAP no matter what.[/COLOR]


No, been there, done that and no, it didn't. But I uninstalled the previous (snap) Chromium.

---

### Post by CatKiller on 2021-04-27
It's not new.

They're dogfooding Chromium as a snap for [these reasons](https://snapcraft.io/blog/chromium-in-ubuntu-deb-to-snap-transition). In prior releases they had random things as snaps, like Gnome's calculator. 

The deb in the repositories has to pull in the snap for the dogfooding test to actually take place.

If the PPA you're using has a newer version of Chromium then you'll get a traditional package from the PPA; if the version in the Ubuntu repositories is newer, you'll get that, which pulls in the snap. That's just how the package manager works.

Lots of people enjoy getting in a huff.

---

### Post by zebra2 on 2021-04-27
i'm switching my hirsute to impish at the end of this week and plan to go all snaps just to satisfy my own curiosity. I'm interested in the viability of all of this. May let you know what I find. I have multiple systems here but will bet that Impish is the best one for the test.

---

### Post by CatKiller on 2021-04-27
> **zebra2 said:**
> i'm switching my hirsute to impish at the end of this week and plan to go all snaps just to satisfy my own curiosity. I'm interested in the viability of all of this. May let you know what I find. I have multiple systems here but will bet that Impish is the best one for the test.

If you want all snaps, all of the time, then you want [Ubuntu Core](https://ubuntu.com/core).

---

### Post by zebra2 on 2021-04-28
> **CatKiller said:**
> If you want all snaps, all of the time, then you want [Ubuntu Core]("https://ubuntu.com/core").

Actually, I was referring to snaps not debs where the choice existed. I have proprietary software running that doesn't supply a snap, plus I only use current development Ubuntu versions. It keeps my reinstall fingers nimble. But thanks for the tip. i will check it out. I just want a true snap experience. Canonical has done me good so far, if there is issues I want to know for myself what they are.

---

### Post by deadflowr on 2021-04-28
Without the outputs for how you added the ppa we are left wondering what you did wrong.
As properly adding the saiarcot895/chromium-dev ppa will install the ppa version.
This also assumes that apt wasn't already broken for some reason.

Sidenote: setting the priority is not needed as Ubuntu isn't PopOS.

Edit:
Probably useful to know what 
```
sudo apt update
apt policy chromium-browser
``` 
look like.

---

### Post by rbmorse on 2021-04-28
>  [COLOR=#000000]plan to go all snaps just to satisfy my own curiosity [/COLOR]

I did that in a 21.04 VM.  It's fine. So Far.

---

### Post by ajgreeny on 2021-04-28
I have been using the [https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev](https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev) ppa for a long time now, since I installed 20.04 as I found snaps at that time too limiting in access to the filesystem in the way I had been used to.  It is still installing chromium successfully, currently on **chromium-browser-91.0.4449.6-0ubuntu1~ppa1~20.04.1.**

Perhaps things have now changed in that respect but I haven't tried as I completely removed snapd and everything else snap related from my 20.04 install.

I do have VMs (in KVM/QEMU) of 21.04 and now 21.10 (currently identical) and have not removed snaps from those so it will be interesting to see how things work now, and hopefully in the future.

---

### Post by Shibblet on 2021-04-28
> **CelticWarrior said:**
> No, been there, done that and no, it didn't. But I uninstalled the previous (snap) Chromium.
I tried multiple times, and watched in horror as Chromium re-installed snap on it's own, and then installed itself.  No matter what I did, the PPA would not override the Snap.

> **deadflowr said:**
> Without the outputs for how you added the ppa we are left wondering what you did wrong.
Right?  Me too.

> **deadflowr said:**
> As properly adding the saiarcot895/chromium-dev ppa will install the ppa version.
This also assumes that apt wasn't already broken for some reason.
That's how I thought PPA's worked.  You add the PPA, and it overrides the previous package when you go to download it.  I did this multiple times with other programs that are already in the software repos, but I wanted a more current or different version.

> **deadflowr said:**
> Sidenote: setting the priority is not needed as Ubuntu isn't PopOS.

Edit:
Probably useful to know what 
```
sudo apt update
apt policy chromium-browser
``` 
look like.
I'll have to check the "apt policy chromium-browser" for the exact output...

My real frustration here is that when I use APT to install a package, it then launches SNAP on it's own.  Not sure if that is just for the "chromium-browser" or if APT looks to see what is in the software repository first, determines if the package is a SNAP, and then launches SNAP to install it.

My personal opinion, is that APT ***should be*** used to install standard packages, and SNAP should be used to install SNAPS.  Otherwise... why have APT if it's going to need SNAP?

---

### Post by Shibblet on 2021-04-28
> **CatKiller said:**
> If the PPA you're using has a newer version of Chromium then you'll get a traditional package from the PPA; if the version in the Ubuntu repositories is newer, you'll get that, which pulls in the snap. That's just how the package manager works.
So, the "chromium-browser" SNAP package is a newer version than the one in the Development PPA that I am using?  

That makes a lot of sense actually...  So, then, how do I ignore the newer version and instead download the one from the PPA?

> **CatKiller said:**
> Lots of people enjoy getting in a huff.
LOL!  Yep... have you seen my posts?

But seriously...  Forcing SNAPS onto Ubuntu users at this point in SNAP's life cycle isn't good.  They may be a great idea for future reference, but they don't seem to run as efficiently.  There are some SNAP programs out there that won't even allow me to make changes in the preferences the way the orignial package does.

So, until SNAPS work as efficiently as a standard package, and have complete functionality... I'm not going to use them.  I understand why Linux Mint has chosen to stay away for the time being.

---

### Post by grahammechanical on 2021-04-28
Would it start an argument to say that apt is not the package manager but apt-get is?  To quote this web site

> apt is a command-line utility for installing, updating,  removing, and otherwise managing deb packages on Ubuntu, Debian, and  related Linux distributions. It combines the most frequently used  commands from the apt-get and apt-cache tools with different default values of some options.

[https://linuxize.com/post/how-to-use-apt-command/](https://linuxize.com/post/how-to-use-apt-command/)

From the apt man page

> apt provides a high-level commandline interface for the package management system. It is intended as an end user interface and enables some options better suited for interactive usage by default compared to more specialized APT tools like apt-get(8) and apt-cache(8). 

It is not beyond possibility to write an apt script that redirects to a different repository.

> SCRIPT USAGE AND DIFFERENCES FROM OTHER APT TOOLS
       The apt(8) commandline is designed as an end-user tool and it may change behavior between versions. While it tries not to break backward compatibility this is not guaranteed either if a change seems beneficial for interactive use.
       All features of apt(8) are available in dedicated APT tools like apt-get(8) and apt-cache(8) as well.  apt(8) just changes the default value of some options (see apt.conf(5) and specifically the Binary scope). So you should prefer using these commands (potentially with some additional options enabled) in your scripts as they keep backward compatibility as much as possible. 

Try installing with apt-get. Read about apt config file

[https://linux.die.net/man/5/apt.conf](https://linux.die.net/man/5/apt.conf)

Regards

---

### Post by grahammechanical on 2021-04-28
Does Linux have an issue with Chromium? Read about the problem and the reason why Canonical decided that Chromium snaps are necessary. Canonical may even drop Chromium completely. Other Linux distributors also are reacting.

[https://www.zdnet.com/article/linux-distributors-frustrated-by-googles-new-chromium-web-browser-restrictions/](https://www.zdnet.com/article/linux-distributors-frustrated-by-googles-new-chromium-web-browser-restrictions/)

Regards

---

### Post by Frogs Hair on 2021-04-28
> I tried multiple times, and watched in horror as Chromium re-installed  snap on it's own, and then installed itself.  No matter what I did, the  PPA would not override the Snap.

  @ Shi[COLOR=#000000]bblet[/COLOR][COLOR=#000000], try deleting chromium from the snap folder and then try installing the ppa. I will test the ppa and let you know what happens. I too get a snap after adding the ppa. I tried using chromium-browser as suggested below and the snap was installed. Chromium-dev also failed as unknown.[/COLOR][URL="https://ubuntuforums.org/member.php?u=778025"][COLOR=#000000]

_Edit: _My failure was due to having snapd installed. [/COLOR][B][COLOR=#000000]


[/COLOR][/B][/URL]

---

### Post by ajgreeny on 2021-04-28
> **Shibblet said:**
> So, the "chromium-browser" SNAP package is a newer version than the one in the Development PPA that I am using?  

That makes a lot of sense actually...  So, then, how do I ignore the newer version and instead download the one from the PPA?


LOL!  Yep... have you seen my posts?

But seriously...  Forcing SNAPS onto Ubuntu users at this point in SNAP's life cycle isn't good.  They may be a great idea for future reference, but they don't seem to run as efficiently.  There are some SNAP programs out there that won't even allow me to make changes in the preferences the way the orignial package does.

So, until SNAPS work as efficiently as a standard package, and have complete functionality... I'm not going to use them.  I understand why Linux Mint has chosen to stay away for the time being.
The current dev ppa version of chromium is 91.0.4449.6 and the most updated chromium snap in my 20.04 is 90.

If you do not want the snap version to keep reinstalling, though I'm not sure how it is managing to do that, remove all the snaps listed on your system and when that is done remove snapd.  If you still have snapd installed when you install chromium it will pull in the snap version; for the .deb version from the ppa you need to install ***chromium-browser*** and not ***chromium***
Once that's done you will never get another snap unless you reinstall snapd.

---

### Post by Shibblet on 2021-04-28
> **ajgreeny said:**
> The current dev ppa version of chromium is 91.0.4449.6 and the most updated chromium snap in my 20.04 is 90.

If you do not want the snap version to keep reinstalling, though I'm not sure how it is managing to do that, remove all the snaps listed on your system and when that is done remove snapd.  If you still have snapd installed when you install chromium it will pull in the snap version; for the .deb version from the ppa you need to install ***chromium-browser*** and not ***chromium***
Once that's done you will never get another snap unless you reinstall snapd.

Amazingly enough, I completely uninstalled all of the snaps that come with Ubuntu, as well as SNAP and SNAPD, as shown in this article:
[https://www.kevin-custer.com/blog/disabling-snaps-in-ubuntu-20-04/]("https://www.kevin-custer.com/blog/disabling-snaps-in-ubuntu-20-04/")

Check out the "Gotchas" part  toward the end of the article.

Regardless...  I'm not a Linux hater because of this... but I may bail out of Kubuntu, and go with Linux Mint, because they don't do the SNAPS.  I just don't really want to, because I've been with Kubuntu since 8.04 Hardy Heron, and it's been a truly great OS...  Also... I've almost completed one alphabetic circuit!  Hirsute Hippo  I hardly knew ye.

---

### Post by CatKiller on 2021-04-28
> **Shibblet said:**
> Regardless...  I'm not a Linux hater because of this... but I may bail out of Kubuntu, and go with Linux Mint, because they don't do the SNAPS.  I just don't really want to, because I've been with Kubuntu since 8.04 Hardy Heron, and it's been a truly great OS... 
I'd suggest Pop as a better Ubuntu-alternative than Mint, since they don't have the lead dev throwing their toys out of the pram.

Or you can stick with Ubuntu and, if you really can't seem to help yourself from installing snaps that you don't want, use the same tweak that Mint does. It's just a text file that pins snapd to have a priority that means it can't be installed.

```
Package: snapd
Pin: release a=*
Pin-Priority: -10
```

---

### Post by Shibblet on 2021-04-28
> **CatKiller said:**
> I'd suggest Pop as a better Ubuntu-alternative than Mint, since they don't have the lead dev throwing their toys out of the pram.
I like Pop_OS!  I may give it a whirl.  I just don't want to get into distro-hopping again.

> **CatKiller said:**
> Or you can stick with Ubuntu and, if you really can't seem to help yourself from installing snaps that you don't want, use the same tweak that Mint does. It's just a text file that pins snapd to have a priority that means it can't be installed.

```
Package: snapd
Pin: release a=*
Pin-Priority: -10
```
Now... that's a great idea!  Thank you for that!

I really do like Kubuntu, and I don't WANT to change.  I have some faith in Canonical, and I am sure that one day SNAPS will be a great thing.  Right now though, standard packages just seem to work better for me.  And I hear a lot of people are having the same problems.

I do think that APT and SNAP installers ***"should"*** be separated.  That means APT downloads standard packages, and SNAP **only ONLY [SIZE=3]ONLY[/SIZE]**, downloads SNAP packages.

---

