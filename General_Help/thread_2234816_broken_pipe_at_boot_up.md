---
title: "broken pipe at boot up"
date: 2014-07-17
forum: General Help
---

### Post by cecilieaux on 2014-07-17
The error message "could not write bytes: broken pipe" pops up right before the Ubuntu logo with the dots. 

I get it that it's an I/O error caused by a command or data pipe that is broken. The system appears to work as it did, that I can tell, but obviously some daemon that I never knew existed is not getting to do its thing and I'm wondering if one day the computer will just freeze up. So ...

What pipe (or how do I find out what pipe)?

Can I fix this?

As best I can recall the last thing I did before this happened is update the hardware enhancement stack (in response to an update manager message).

Thanks in advance!

---

### Post by fcdecker-gmail on 2014-07-17
I've also just updated my hardware stack, and am receiving the same message. In my case the system also booted normally, and seems to perform a bit better (it's an elderly HP with an AMD Turion processor) but after about 30 minutes of operation it locked up and again displayed the "broken pipe" message. A reboot cleared things up, for now, but it's going to be a long day if I have to do keep doing that. 

The error message came after the terminal login prompt came and went, but before Ubuntu's login splashscreen loaded. I'd guess it might be x-related? I'm not especially knowledgeable, despite running Ubuntu for 7 years now, but I've seen a lot of issues come and go with X and my Nvidia graphics card.

---

### Post by Randy M on 2014-07-17
I'm getting the same message during boot. It started after the latest updates this morning. Does anyone have any suggestions on troubleshooting?

---

### Post by CCC999 on 2014-07-17
Add me to the list...same broken pipe message....plus some server issues where it is looking for servers I have removed recently......

---

### Post by fcdecker-gmail on 2014-07-21
I'm curious whether the rest of you have Nvidia chipsets. My machine has crashed three times since the update, giving the same "broken pipe" message and then an error from the Nouveau driver. Before I updated my hardware stack I'd been running the proprietary Nvidia driver v 304.88, which wasn't exactly lightning-fast but was very stable. The stack update deleted that, and when I tried to reinstall it yesterday the install errored out with a message that I "had been holding broken packages." I thought the "had been" phrasing was odd. When I ran Synaptic to check for and repair broken packages, it found none, but a second attempt to reinstall the Nvidia driver also failed.

---

### Post by cecilieaux on 2014-07-21
No Nvidia here.

---

### Post by WB0HYQ on 2014-08-10
I do have an NVIDIA card here and I'm getting the 'broken pipe' message now at bootup.  I can still get a full-screen tty to run, but when I hit Ctrl-Alt-F7 to get a desktop, I get the broken pipe message and nothing else.  Ctrl-Alt-F2 gets me back to the tty.

So I know that Ubuntu is running, but no desktop is displayed.  Where do I go from here?

Bill

---

### Post by NM5TF on 2014-08-10
you might try this.....seems to have fixed it for several people...YMMV

```
sudo apt-get update
sudo apt-get purge nvidia-*
sudo apt-get install nvida-current-updates
sudo rm .Xauthority
```

good luck...let us know if it fixed it...

tommy

---

### Post by FriedMicro on 2014-08-11
It should ask you for your password; after which ```
sudo apt-get install nvidia*
``` will install the proprietary drivers which "might" help. Personally I'm running on Intel and NVIDIA graphics on Ubuntu 14.04 with an Intel SSD cache so hardware wise my rig was a pain to get running, but it works well now.

---

### Post by WB0HYQ on 2014-08-11
@nm5tf & friedmicro:

Tried both of those.  I started a new thread of my own and mentioned both attempts.  Sorry I didn't mention that.

My computer worked well for around three weeks and then just did this to me.  I don't recall any updates installed before it happened.  What is strange is that I can remote into the machine from my Win7 machines and get a desktop just fine.  I just can't get the desktop to run on the attached monitor.  Strange.

Bill

---

### Post by NM5TF on 2014-08-11
if your desktop is not running you might try this...

```
sudo service lightdm restart
```

tommy

---

