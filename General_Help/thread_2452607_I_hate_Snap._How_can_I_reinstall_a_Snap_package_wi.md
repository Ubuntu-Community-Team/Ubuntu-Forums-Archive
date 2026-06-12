---
title: "I hate Snap. How can I reinstall a Snap package with Apt?"
date: 2020-10-25
forum: General Help
---

### Post by mnealbarrett on 2020-10-25
I have been having problems with some snap packages. For example, I had various problems with MakeMKV until I uninstalled the snap package and compiled it.  I would like uninstall ffmpeg and all of its related packages, and install the apt versions. How can I do that?

---

### Post by mc4man on 2020-10-25
Simple
```
sudo snap remove ffmpeg
```
```
sudo apt install ffmpeg
```

---

### Post by HermanAB on 2020-10-26
I won't go so far as to say that I hate Snap, but it does seem to solve a problem that nobody has and causes quite a few more, so it is probably best avoided by most everybody.  Maybe it works for the Snap developers.

---

### Post by ajgreeny on 2020-10-26
I have to admit that I removed all the snap infrastructure from my Xubuntu 20.04 a while ago with, so far at least, no downsides.

Deciding how to install chromium was the trickiest problem to solve but at the moment I use the version from the dev PPA, link to follow when I get off this Android tablet.

---

### Post by TheFu on 2020-10-26
I was forced to add the snap infrastructure back because **lxd** is only provided as a snap package since v2.x. I'm addicted to lxd containers, which surprisingly aren't as finicky as docker containers and are more open ... but have to be managed by LXD in a constrained container?  LXD is like a mini-virtual machine, but with the speed and 1/10th overhead of a Linux Container.  Plus, Linux containers can run on any Linux system, so we don't have to enable VT-x/AMD-v support to use it.  The encapsulation of a VM, without the hardware demands.

But besides that, I avoid snaps and have a weekly job that purges the 2nd and 3rd copies of unwanted snaps that get installed without my permission. What's really frustrating is that snap packages seem to fail at the primary reason they exist - for 1 install that "just works" everywhere.

I hope Canonical gives up on snaps quicker than it took them to give up on Unity as a DE. Best we put this behind us ASAP.

---

### Post by VMC on 2020-10-26
^^^
This! (the last sentence)

---

### Post by mc4man on 2020-10-26
> 
I hope Canonical gives up on snaps quicker than it took them to give up on Unity as a DE. Best we put this behind us ASAP
There is 0% chance of that ever happening

---

### Post by mikewhatever on 2020-10-27
Wow, a bunch of snap haters here. Is there a linux community without haters anywhere? 
It was Unity before snaps, and the orange color before Unity, and the brown color before that.
This hate nonsense must go, ASAP.

---

### Post by ajgreeny on 2020-10-27
> **mikewhatever said:**
> Wow, a bunch of snap haters here. Is there a linux community without haters anywhere? 
It was Unity before snaps, and the orange color before Unity, and the brown color before that.
This hate nonsense must go, ASAP.
That's  what happens when there is choice available!

There will always be users who "hate" something or other about the OS they use; just be thankful that there is a choice and you can remove snaps if you want to.

---

