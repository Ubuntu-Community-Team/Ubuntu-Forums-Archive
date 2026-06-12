---
title: "System booting issue after abruptly shutting down whil someone was trying ssh on mine"
date: 2021-02-16
forum: General Help
---

### Post by shyam1287 on 2021-02-16
My ubuntu system doesnt boot after I abruptly shut down my system with the power button.

Steps I tried:
Boot repair, grub re-installation  (dint work)
Trying nomodeset option to view boot sequence logs.  (nothing much)
Why my sub-sequent boots are not displaying the login screen.

Where generally are the login splash screen and the booting related GUI images will be stored in the filesystem?
Which file controls and initiates the GRUB and where the control goes after GRUB config finishes execution?

Version:
Ubuntu 20.04, focal fossa

Currently the rescue, safe mode boots. But the normal GUI mode doesnt really move and is freezed in that loading process.

---

### Post by TheFu on 2021-02-16
> **shyam1287 said:**
> My ubuntu system doesnt boot after I abruptly shut down my system with the power button

Hint: don't do that again.

I would start with a fresh install, restore my data, settings, and anything else I can't lose from backups.  It's the only way to be sure. 

Don't pull the power on modern computers. It can be bad.

---

### Post by shyam1287 on 2021-02-16
Funny, Plugging the power doesnt affect anything at all generally, only things it might affect might be the physical hard disk  and as you are abruptly stopping the disk rotations and reads will get affected, if at all you use hdd. Only if someother booting related file is modified wrongly, only then system's booting might get affected. Anybody can do a fresh install. Thats not the actual way to go. There is some issue somewhere in the booting process, that needs to be resolved. There are chances for any adversaries to perfectly time their mal modifications to coincide with such mishaps, to make the user wrongly interpret it and associate it with such user's actions.

---

### Post by TheFu on 2021-02-16
A fresh install is 15 minutes.
Restoring from backups, another 15 minutes - perhaps 30.
In 45 minutes, this issue, which we will likely never know the actual cause, will be solved.

There was an ssh bug a few weeks ago that was patched. I don't recall the details. A few of my systems allow ssh from specific internet subnets, only allowing key-based connections, but I've not seen any system halts.  

After you get a fresh install (we can't trust this system anymore), be certain to patch and secure all outside connections properly.

IMHO.

There was an ISO released by Canonical that had to be re-released. That wouldn't impact any existing system. At the end of the new install - it was a 20.04 installer problem - they didn't actually install any kernel.  There's an announcement about that. 
[https://lists.ubuntu.com/archives/ubuntu-announce/2021-February/000265.html](https://lists.ubuntu.com/archives/ubuntu-announce/2021-February/000265.html)
If you pulled any Ubuntu 20.04 ISO recently, say in the last 2 weeks, probably should get a new one. It applies to all flavors of ubuntu.

---

### Post by grahammechanical on 2021-02-16
> Where generally are the login splash screen and the booting related GUI images will be stored in the filesystem?
Which file controls and initiates the GRUB and where the control goes after GRUB config finishes execution?

The login splash screen is called GDM or GDM3. Gnome Display manager. A search in the file manager will show references to GDM in many folders some of which will require administrator (root) privileges to open the folders. 

I do not know what you mean by "booting related GUI images."  The motherboard BIOS/UEFI system will try to load a boot loader (Grub) from the hard drive that has boot priority and it will look in the bios boot partition (or EFI boot partition). Grub in turn looks for its configuration file (grub.cfg) and then loads the Linux kernel that is referenced in grub.cfg. If there is more than one operating system Grub will present a menu for us to select the OS.

 At some point after Linux loads to a command line it starts running various commands and scripts that eventually (hopefully?) bring us to a login screen that is sitting on Linux. At this point Gnome Display manager is making use of a loaded video driver. The login screen loads the desktop environment which loads the user interface. There will be various configuration files that determine the look of the user interface.

If I try to give a more detailed explanation than this I will pass out from lack of oxygen. :) These matters are at too high an altitude for me to breathe.

Regards

---

### Post by DuckHook on 2021-02-16
> **TheFu said:**
> A fresh install is 15 minutes.
Restoring from backups, another 15 minutes - perhaps 30.
In 45 minutes, this issue, which we will likely never know the actual cause, will be solved.
> **shyam1287 said:**
> Anybody can do a fresh install. Thats not the actual way to go.
:confused:

You have been given good advice. So why do you insist on doing it the hard way?

Your idea of how a modern OS works is woefully inadequate. Pulling the power does not confine your problem to just failed writes. The disk heads halt above physically writable media. If they skid to such a halt, there's no telling what sectors they will take out, even boot. DEs are complex beasts. We have no idea what you were doing prior to pulling the plug because you didn't bother to tell us. If it involved a change to the DE, configs, user settings, ownerships or mods of anything on /home, then an abrupt shutdown could indeed leave files in such a disrupted state that it would break subsequent login.

[LIST]
[*]Why did you have to so brutally pull the plug?
[*]How do you know that someone was trying to SSH you?
[*]Why are you jumping to such suspicions?
[/LIST]

---

### Post by QIII on 2021-02-16
No matter your storage media, a sudden power-off can and will leave writes uncommitted/incomplete.  And you should definitely pay attention to the info about the heads if you are using mechanical drives.  They get left dangling.  In a normal shutdown they are parked to avoid damage.  That very definitely CAN cause system corruption.  That is just ONE of the things a sudden power-off can do.  There is a reason people with critical systems use battery backups so that they can shut their machines down gracefully.

At the risk of causing an echo:  you can go your own way, do a lot of work, possible go through a significant emotional event and possibly, just possibly come out the other side no worse for the wear.  Or, you can heed the advice of folks who have been around this for many years.  Your choice.

Indeterminate system corruption --> reinstall.  Unless you know every corner of the Linux kernel and each and every application you run, it is unlikely you will catch every possible problem and be able to fix it.

---

### Post by QIII on 2021-02-16
> **shyam1287 said:**
> Anybody can do a fresh install. Thats not the actual way to go.

Actually, sometimes it is.

---

### Post by shyam1287 on 2021-02-17
Is there any full length video or any kind of tutorial that explains all the situations and scenarios that cover step by step what all executions happen and which files are used and accessed until the point where the login screen or the internal desktop GUI appears? Specific to ubuntu is better, if not general linux.

---

### Post by QIII on 2021-02-17
As you seem bound and determined to disregard the suggestions of some very knowledgeable people, I offer [this]("https://opensource.com/article/17/2/linux-boot-and-startup").  Not a video, but it's a great way for you to see what you are trying to get yourself into.  Save yourself some time and frustration and do as suggested.

Best wishes.

---

