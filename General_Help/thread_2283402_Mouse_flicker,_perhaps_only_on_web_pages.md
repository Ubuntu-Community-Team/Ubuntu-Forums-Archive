---
title: "Mouse flicker, perhaps only on web pages"
date: 2015-06-21
forum: General Help
---

### Post by Cleaver on 2015-06-21
Hi,

My mouse cursor is flickering(moving left to right rapidly, or up and down) when I move it, but only when I move it. It was fine last night, so this is very abrupt. I'm using 15.04 and have already tried unplugging it and plugging it into another USB port. I've also rebooted at least twice.

The flicker sometimes seems a bit less extreme on things that aren't web pages, but I'm not sure about that yet.

Anyone solved this problem? I looked at other threads but only saw one involving dual monitors. Thanks.

---

### Post by Bucky Ball on 2015-06-21
Have you tried another mouse? As unlikely as it might seem, it is possible for goblins to come during the night and mess with the inner workings of electronic devices. :)

In all seriousness, at least it would rule out one possibility. Goblins! Or dead hardware. It's a fact that electronic things can die with little warning.

---

### Post by Cleaver on 2015-06-22
> **Bucky Ball said:**
> Have you tried another mouse? As unlikely as it might seem, it is possible for goblins to come during the night and mess with the inner workings of electronic devices. :)

In all seriousness, at least it would rule out one possibility. Goblins! Or dead hardware. It's a fact that electronic things can die with little warning.

The thing is, I'm a multibooter(must be more than 5 OSes on here now) and I don't have this problem with any other on here. They work perfectly normally, including Mint and the dreaded Windows. It was very abrupt and I can't think of what change I made to the system that would mess with it, but then I still consider myself very green with Linux.

---

### Post by Bucky Ball on 2015-06-22
Hmm. That is interesting. Didn't do an update and this happened?

Just a point, and off-topic, sorry: have you tried running all those OSs as virtual machines in Virtualbox? That way you can play and break as much as you like then just reload the snapshot of the virtual machine and you are back to square one. 

Maybe you have a specific reason to install five OSs to the hard drive. :-k :)

---

### Post by Cleaver on 2015-06-22
Well, I've run "apt-get update" but other than that I can't think of what updates I've done.

I mostly just want them to run faster on "bare metal," which I keep reading they do as opposed to a VM. I tried using VirtualBox once too, but couldn't get it working despite understanding the instructions. Given I'm still learning and sometimes still break OSes, I need backup ones so I can still do crucial stuff without needing an immediate reinstall--plus I only use one OS(Manjaro) for my job, which requires me to look at malicious sites, and though I don't think I've ever gotten malware I want to protect the other partitions.

Besides that, I really don't mind rebooting anyway, and my partitions for OSes are pretty small.

---

### Post by Bucky Ball on 2015-06-22
Ok, try a full update/upgrade of the installed system and see if it spits anything out.

```

sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

Post any and all errors. If you see there is a new kernel to be installed, reboot when the update/upgrade is finished and use the new kernel. The instructions above will NOT upgrade your installed release to a newer one, as you probably know. :)

---

### Post by Cleaver on 2015-06-22
Nothing strange came up. No kernel mention came up. Rebooted anyway just in case, and for the first minute the cursor was normal, even on this page.

I just realized the cursor often is two cursors when flickering, with one that doesn't flicker being the real one and the flickering one being a "decoy" of sorts. They're generally side by side, maybe 2 inches apart.

Edit: Meant to say that the cursor went haywire again after that first minute.

---

### Post by Bucky Ball on 2015-06-22
Hmm. Have you done any customisations on the OS? Installed any desktop environments? Perhaps a quick run down of anything you may have changed which has given you two mice. 

Have you installed Xubuntu-desktop or anything like that?

This issue gets odder. :-k

---

### Post by Cleaver on 2015-06-22
Yes! Sorry about that--I thought I'd mentioned it. I've installed several of those for the purpose of checking them out on Ubuntu--maybe up to 5, even.

Is there a way to have those installed without it affecting the mouse? I know merely having Lubuntu/Xubuntu in the past on here didn't interfere.

---

### Post by Bucky Ball on 2015-06-23
*Thread moved to **General Help**.*

Ok, installing *buntu-desktop anything is like installing a full install on top of another one. If you install xubuntu-desktop in Ubuntu, for instance, then you, in effect, have Ubuntu and all its default apps/dependencies, etc. AND Xubuntu and its default apps/dependencies, etc. Messy. If you have installed five *buntu-desktops, you have a real mess in there. We are talking on the SAME partition, right? Not on separate partitions or as virtual machines?

If you want to try the desktop environment of another flavour, install just the DE. For xubuntu, that is xfce4 and for Lubunutu that is lxde. There are lots of DEs to play around with.

Think of it like this: All the official flavours use the same base Ubuntu kernel. When you install a Ubuntu flavour, it is the base kernel 'dressed up' with a bunch of default apps and software specific to the flavour you've installed. The mini.iso is a good example. You install and, if you don't choose a profile, it installs the Ubuntu base kernel and that's it. Now you can go to the wardrobe and choose the clothes, so to speak! Add whatever individual bits you want from any distro. BUT, and this is a big but, if you install the mini.iso THEN install, say, Xubuntu-desktop, you have Xubuntu for all intents and purposes. No need to install the mini.iso. You could have just installed Xubuntu and saved some time. 

This a VERY common misunderstanding of the mini.iso and I see threads here often where people have done just that, installed the mini.iso then installed *buntu-desktop. No point in doing a mini.iso to start in that case.

If you want to try a full install of another OS, best as a virtual machine guest or on another partition. 

Your current 'twin-cursor' issue, as you have up to five different flavours installed on the one partition, will be like finding a needle in the proverbial haystack, but we're pretty good at digging here. 

First, I think you might need to uninstall some of those *buntu-desktops and run:

```
sudo apt-get autoremove
```

... after each. The fixing of this, if possible, has a chance of breaking your system so I would backup any personal data on that partition you don't want to lose prior to proceeding.

(Have you looked in 'Mouse and touchpad' to see if it is reporting only one mouse in the devices there? If it is reporting two, switch one off. Two of your psuedo installs, or more, may be loading drivers for the mouse and happily using it as per normal ... somehow, a stab in ... the ... dark ... ) ;)

(PS: You could try, at your own risk, uninstalling the *buntu-desktops you have installed one by one, rebooting after each and seeing if the issue goes away. You may discover which install is causing the issue this way. You may also end up with a very broken install.)

---

### Post by Cleaver on 2015-06-24
OK. I think removing those worked. It was fine when I only had 2 additional desktops installed on there, though. I noticed the super key menu(blanking on the name for some reason) pops up faster now.

I'd thought they merely installed a new DE for you to switch between if you wanted and those extra apps. Those apps themselves don't actually bother me. So, in addition to installing those apps, are you saying it also makes the distro heavier and therefore slower and maybe less stable/reliable?

It *did* do nothing when I tried opening some programs within Unity after doing this(like Startup applications) but upon rebooting this seems to have been fixed. I'm guessing that'll remain consistent for now.

---

