---
title: "My first go with Ubuntu 16.04, possible glitch as I shut down PC"
date: 2016-11-08
forum: General Help
---

### Post by gwahyyr on 2016-11-08
Dear fellows, 

 This is my first post to Ubuntu forums, as I'm a new user to this wondrous operating system. My compliments go to all who have been developing and using it, as it is like a breath of fresh air after so many years of frustration concerning windows. I have installed Ubuntu 16.04 a couple of days ago, and noticed a possible problem that occurs while shutting down the PC, which is an HP 250 G3 Notebook, to be precise. During the shutdown, we can see those dots blinking below the word Ubuntu, and in my case it appears that the machine may be jumping through important steps in the shutdown process, because it suddenly and abruptly shuts down with a noise that is reminiscent of a lightbulb exploding (not that loud:):), or a television short circuiting. The PC functions properly nonetheless, so obviously there is no short circuiting, but the noise itself concerns me, as I've not heard it ever before. 

 At this point I have to say a few words/details about the installation itself, as they may provide some clue to more experienced users. I installed it using the usb-iso variation to replace win7 completely, however I started the installation from the ubuntu desktop itself. (I'm referring to the possibility of trying out Ubuntu prior to installation) While trying out from pendrive, Ubuntu offers the installation, by clicking on the installation icon to be found on the desktop. The rest of the process was the regular step by step fashion if my memory serves right. Thank you in advance for support and information, glad to be here!

---

### Post by Bucky Ball on 2016-11-08
*Thread moved to **General Help**.*

... as you are already installed and things are working fine ... except the knocking which is not related to installing or upgrading your OS so better chance of support here.

This:
> During the shutdown, we can see those dots blinking below the word Ubuntu ... it suddenly and abruptly shuts down

... is exactly what I experience on my machine, but without the bang. The machine makes a noise as the hard drives wind down, then a kinda 'click' noise along the way, but that's about it. Strange. Hopefully someone will have some clues. :-k

Apart from that, glad you're enjoying the OS. :)

* Afterthought: If this is a new install and if you haven't already, open a terminal and run these two commands, one after the other hitting enter after each. You'll be asked for your password, it will be invisible when you type, that is normal. 

```
sudo apt update
sudo apt full-upgrade
```

Reboot.

---

### Post by kurt18947 on 2016-11-08
I am running 16.04 on a Lenovo Thinkpad 410 and your experience sounds much like mine. Shutdown is quite abrupt and there is a 'tick' sound (relay activating?). It doesn't really sound like anything to get too alarmed about.

---

### Post by gwahyyr on 2016-11-09
Bucky Ball, thanks for your input. Some sort of Ubuntu magick is going on, as after I wrote my complaint yesterday, the computer did not produce the same cracking sound as described above during the shutdown process, however the abruptness remained. I'm gonna do the recommended commands, as I have not performed them after the install. Should these upgrade commands be performed on a regular basis, or only once?

 Thanks Kurt, glad to hear I'm not the only one. Perhaps you're right and it's nothing to worry about.

---

### Post by Bucky Ball on 2016-11-09
> **gwahyyr said:**
> Should these upgrade commands be performed on a regular basis, or only once?

In theory, the Software Updater should do this for you (I think that is in Ubuntu), but I don't use it (I have a bit of a custom setup with Xubuntu-core so missing a lot of the 'standard' stuff). I update/upgrade with the commands I gave you on a regular basis instead. You can also update with Synaptics but never used that method (you can install Synaptic Package Manager from the repos and it is, to my mind, a better package manager than the default Software Centre and widely used) .

So, how often you update is up to you, but you should keep your machine up to date so should be done regularly (once a week at least).

Also, you can have the system update automatically. If you open Software and Updates> Updates tab and have a look at the settings there you can set the update frequency and other things.

Lastly, the 'sudo apt full-upgrade' command I gave should *always* be run *after* the 'sudo apt update' command, never on its own. The 'full-upgrade' command will NOT upgrade your OS release to the latest release. It updates all installed software, nothing more. ;)

---

### Post by kpatz on 2016-11-09
The click you hear is probably the hard drive heads parking and locking.  I think Windows sends a command to the drive to do this before it powers down, so you don't hear the click when shutting down Windows.  It's harmless.

---

### Post by gwahyyr on 2016-11-11
> **kpatz said:**
> The click you hear is probably the hard drive heads parking and locking.  I think Windows sends a command to the drive to do this before it powers down, so you don't hear the click when shutting down Windows.  It's harmless.

 Thanks for reassuring me on this.

---

