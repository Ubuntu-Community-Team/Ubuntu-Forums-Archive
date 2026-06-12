---
title: "autoremove deletes keyboard driver, cannot write login password"
date: 2020-06-14
forum: General Help
---

### Post by ffrr on 2020-06-14
Many installs recommend autoremove to clean out deadwood. Since, years ago, I got a machine completely cleaned out, including the OS by autoremove, I never touched it again. Until the other day, figuring it surely was decommissioned and replaced older versions. It was quite a lot and the names that zipped by, such as 'gnome...' looked rather suspicious. Well--here I go again! This time Ubuntu is still there all right, but firing up I get as far as to the login and cannot enter the password, because the keyboard is dead. So my question is: Isn't there a recovery mode to get into with appropriate fingering? Or could I get back in with a boot CD or USB stick? And what would be the best way to make those?

Frederic

---

### Post by VMC on 2020-06-14
Since this has happened twice, maybe your not autoremove clean out often enough.
I have never come across this scenario. I never let it build up.
It would be hard to back tract since apparently you had many old files.
Have you tried logging in with the live session, chroot and add keyboard?

---

### Post by grahammechanical on 2020-06-14
Ubuntu does have a recovery mode. You may be able to access it if you see a Grub boot menu. Which we will not see if Ubuntu is the only OS. So, here is the way to call it up.

[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

If you wish to download from the internet you should first of all select Network at the recovery menu. That will set up a network connection. At the menu if we select Root we get a root shell prompt where we can issue commands. Typing "exit" will bring us back to the recovery menu. Selecting Resume will load to a desktop but without activating any video drivers. So, expect a rather large size desktop. May be the keyboard will work with the Grub menu and the Recovery menu as the activity is happening before the OS is loaded.

You do not say what version of Ubuntu you are using. The login screen is presented by a Display Manager and not by the desktop environment. You may need to re-install Gnome and Gnome 3 shell. 

Regards.

---

### Post by ffrr on 2020-06-15
Thank you both. I followed the recovery mode procedure finishing with 'Resume' as recommended. A normal login followed and I still had no keyboard. Same thing over again up to the recovery menu. An item 'Repair broken packages' looks much to the point. Should I try that? Or rather do an 'upgrade' from a root terminal?

Frederic

---

### Post by CelticWarrior on 2020-06-15
It depends.

If it's an EoL release jjust do your backups if needed from the live session and install fresh a supported release.

---

### Post by ActionParsnip on 2020-06-15
Which release of Ubuntu are you using, please?

---

### Post by ffrr on 2020-06-15
18.04 LTS on a Dell Latitude E6530.

---

### Post by speartip on 2020-06-15
Autoremove is usually safe to use. That being said, if you delete a program that is closely tied to the stock Gnome install for example, you may well find that Autoremove then wants to remove the rest of the Gnome desktop or at least part of it. I had this happen in a debian install. That's why I use synaptic to install remove programs. Then you can see immediately what's left in autoremove, & make a better informed decision. My advise is don't delete/uninstall anything that comes with the vanilla install, unless you're certain you know what you're doing.

---

### Post by ffrr on 2020-06-15
Speartip, advice well taken. Thanks. For the immediate, I am kind of spinning in a circle, working Grahammetrical's recipe (post #3). I tried 'Repair broken Packages'. This option failed with 'Failed to fetch http:(name)' errors. Next try was 'Drop to root shell prompt' and 'apt-get update'. Same error. I don't seem to have an internet connection. How would I connect from the root shell prompt. I suppose I have to configure the connection first.

---

### Post by speartip on 2020-06-15
So assuming your using ubuntu gnome 18.04, if we can resolve the broken package issue, then a simple:
```
sudo apt-get install ubuntu-gnome-desktop
```
should resolve the problem, bearing in mind you said a lot of gnome stuff got deleted in post 1.
Do you know what the broken package is? and do you have any 3rd party repos enabled?

---

### Post by ffrr on 2020-06-15
The road block currently is the absence of an internet connection. 'update' lists the urls of repos it would fetch but doesn't fetch. Each listing starts with 'Failed to fetch'. So, I am blatantly missing an internet connection and should establish one before I can get on. The hardware, the wiring are in place. The server is waiting. I am the superuser in a terminal. I can type commands (and that is all I can do).

---

### Post by ffrr on 2020-06-15
To sum up the situation: The only access I have is a terminal. I am the superuser. I would like to update, upgrade, install, operations that require a live internet connection. I don't seem to have one. 'update', 'upgrade' and 'install' all display running lists of urls. Each listing starts with the failure notice: 'Failed to fetch [http://(name](http://(name) of site). So, at this point the question is: what does the superuser in his terminal write at the prompt needing to establish internet access? The hardware connection is intact, the server is ready to take requests. The road block seems to be a missing device driver.

---

### Post by ffrr on 2020-06-18
The good advice I have received so far has allowed me, if not to solve the problem, at least to shift my focus to the boot process before the recovery mode menu appears. The recovery mode turned out as a dead end. Package repair requires internet access, which I didn't have and couldn't restore from a root shell prompt. Conclusion: I should attempt to boot from a USB stick so that I get a root terminal on a functional machine, internet connection included. The question then is how to prepare such a USB stick. I did snoop around on this forum. Ironically, the keywords 'boot,USB' call up an abundance of tales of failing USB boots, not successful USB boots rescuing failing HD boots.  

Frederic

---

