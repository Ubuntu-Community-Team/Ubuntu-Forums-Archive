---
title: "Upgrading obsolete programs"
date: 2014-03-02
forum: General Help
---

### Post by sideburns on 2014-03-02
My sister is running Xubuntu 13.10, and just received a message that there are at least 15 to 20 obsolete packages that should be upgraded.  I know that this can be done with apt-get, but she's not that good with a CLI, and it would be nice to know how Ubuntu does this in a GUI.  (I know how to do it in Fedora, but that's no help here.)

---

### Post by Buntu Bunny on 2014-03-02
Her best bet would probably be Synaptic Package Manager, available for download from the Software Center. OTOH, the commands in terminal are pretty simple. Perhaps she'd gain a bit of confidence if she learned how(?)

---

### Post by ian-weisser on 2014-03-02
> **sideburns said:**
> My sister is running Xubuntu 13.10, and just received a message that there are at least 15 to 20 obsolete packages that should be upgraded.

Along with that message, one of her application indicators in the top bar should turn red.
Click on the red indicator, and open Software Updater.

---

### Post by sideburns on 2014-03-02
It's not a lack of confidence in this case, so much as the number of programs to upgrade.  I'm an old-time command line hack, but for something like this, I'd prefer a GUI myself, just to get it done all in one shot.  I'll let her know about Synaptic, and we'll go from there.  Thanx!

---

### Post by sideburns on 2014-03-02
OK, that gives her two ways to do it.  Again, thanx!

---

### Post by Jason_Gibson on 2014-03-02
> **sideburns said:**
> It's not a lack of confidence in this case, so much as the number of programs to upgrade.  I'm an old-time command line hack, but for something like this, I'd prefer a GUI myself, just to get it done all in one shot.  I'll let her know about Synaptic, and we'll go from there.  Thanx!

I would assume a long time command line user would know that all that is needed is this.

```
sudo apt-get update && sudo apt-get -y upgrade
```

Matters not how many programs to upgrade.

---

### Post by sideburns on 2014-03-02
I don't want to be snarky, but you might consider reading my .sig first.  I've never used a Debian-based distro; both my desktop and laptop use Fedora, so I don't know (without checking man pages) what the syntax is for apt-get.  And, if there's a way to do it via GUI, my sister, who's not at all comfortable in a terminal, will find it much easier.  BTW, I just got a look at her error message, and she's using version 14.04, not 13.10 as I first reported, but I doubt that will make a difference here.

There are two error messages; one simply reports which packages need upgrading, and the other, which I hadn't known about, is about an internal error.  She's tried reporting it, several times, but hasn't heard back yet.

---

### Post by monkeybrain20122 on 2014-03-03
synaptic is already installed in xubuntu.      

P.S. If your sister is not so comfortable with geeky stuffs why on earth is she using a pre-release (14.04) which is meant for bug hunters?:confused:
(yeah I would think that 14.04 would have a lot of error messages)

---

### Post by sideburns on 2014-03-03
Why is she using 14.04?  Well, until I read a screen shot of the error message and noticed it, she didn't know that she was.  I do know that she'd told her system updater (or whatever it's called) to notify her of upgrades, because she was several back and wanted to get current.  Possibly she accepted an upgrade into a pre-release version without realizing it.

I just walked to the other end of the condo and asked; she doesn't know either.  As I wrote earlier, we both thought that she was on 13.10.

---

### Post by monkeybrain20122 on 2014-03-03
> **sideburns said:**
>   I do know that she'd told her system updater (or whatever it's called) to notify her of upgrades, because she was several back and wanted to get current.  Possibly she accepted an upgrade into a pre-release version without realizing it.
.

The updater is not supposed to prompt her to upgrade to a pre-release version so either there is a bug or she has done something (I am not receiving a prompt to upgrade to 14.04 but I am on Ubuntu, though I think xubuntu uses the same update mechanism)

On the safe side I suggest that she should turn "notify me for new ubuntu version" in the update-manager to 'never' to avoid breaking the system whenever a new Ubuntu comes out. 1) "upgrade" is very unreliable (a clean install is much faster and safer)and 2) you don't want to upgrade to a new os the very day it is released, there will be bugs.

---

### Post by sideburns on 2014-03-03
Thank you.  I doubt, however, that she's going to run into trouble by upgrading on the very first day as she has the updater set to check once a week.

---

### Post by monkeybrain20122 on 2014-03-03
> **sideburns said:**
> Thank you.  I doubt, however, that she's going to run into trouble by upgrading on the very first day as she has the updater set to check once a week.

That is not what I meant. There are two kinds of 'updates',.normal packages update and system (OS) updates(aka "upgrade"). She configures notification for package update to be once a week, but as soon as a new version of Ubuntu is released it will prompt her to "upgrade" the system and chances are it will break it. It is the second one that I ask you to disable. It is all in the option menu of the update manager. Can't show you a screenshot now as I am on Fedora.

---

