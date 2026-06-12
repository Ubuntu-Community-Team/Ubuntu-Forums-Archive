---
title: "Update error: Failed to fetch ports.ubuntu.com message"
date: 2014-10-02
forum: General Help
---

### Post by wog on 2014-10-02
Im updating an ancient Inspiron 6000 from 8.04 to 10.04.

I got this during update:
==start==
W:Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/lucid/main/binary-i386/Packages.gz](http://ports.ubuntu.com/ubuntu-ports/dists/lucid/main/binary-i386/Packages.gz)  404 Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.
==end==

If I close the window, the upgrade quits. Any idea what I can do?

---

### Post by matt_symes on 2014-10-02
Hi

Disable that repository in your sources file.

From the terminal

```
sudo sed -i 's/ports.ubuntu.com/^#/g' /etc/apt/sources.list
```

Then try the update again.

Kind regards

---

### Post by wog on 2014-10-02
Still the same error during update. 

I tried checking for updates, and I get this instead, over and over:
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.91.14 80]

---

### Post by QIII on 2014-10-02
8.04 is well past it's EOL.  The desktop version of 10.04 is also past its EOL. 

The repos for both have been moved.  Thus, the 404 messages.

 Although it can be done by the intrepid and expert, upgrading through EOL versions is a sure-fire recipe for disaster. You would find yourself without support yet again.  Rather than trying to go through the heartburn of an upgrade from one unsupported version to another, it would be best to do a fresh installation of a currently supported version.  At this time, that means 12.04 or 14.04.  

If your hardware is not up to the task of Unity in 3D, then I suggest Xubuntu or Lubuntu.

---

### Post by matt_symes on 2014-10-02
Hi

> **wog said:**
> Still the same error during update. 

I tried checking for updates, and I get this instead, over and over:
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.91.14 80]

That is a different error message as it's referencing a different repository. 

Hardy as been EOL for a while and that's why it can't find the hardy repository in the main ubuntu repository.

How are you trying to upgrade the system to 10.04 ? From the terminal ?

**EDIT: **I have to concur with QIII's post. There are ways to upgrade to 10.04, however are you sure you want to do that on such old hardware ?

Alot changed between 8.04 and 10.04 and the changes are monumental from 8.04 to an even newer LTS release.

Upgrading maybe the type of thing i would try "just for the hell of it", however if you have intentions of actually using the laptop then you may be disappointed.

Try running some LiveUSBs and see how the laptop copes.

Kind regards

---

### Post by wog on 2014-10-02
I have X (gnome) up, so Ive been using whatever updater comes with that. I can use the terminal, since the commands are well-known. This version also comes with Synaptic, so I suppose I could also use that. Honestly, I use whatever system a helper suggests, because theyre familiar with something and Im not.

If 10.04 is EOL, then why would Hardy suggest it instead of 12.04 or 14.04? 
Honestly, I installed 8.04 because I had it handy, and thought an older version might cope better with an older architecture. I then expected I could update to the latest and greatest version from there. I guess that wasnt an accurate notion?

What are Xubuntu and Lubuntu based on, if not Unity?

---

### Post by QIII on 2014-10-02
Xfce and LXDE respectively.

You can [upgrade through an EOL path]("https://help.ubuntu.com/community/EOLUpgrades"), but it is fraught with danger.  I don't recommend it.

What are the specs of your machine?

Edit:  I just looked up the specs, and suggest that you might also try Bodhi Linux.  It's extremely light and should run just fine with half a Gig of RAM.  But make sure you download the 32 bit version.  The Enlightenment Window Manager might take a bit of getting used to.

Edit:  Just tuned down my VM.  Pretty snappy still, but running a video on YouTube soaked up the memory and sent some to swap.

---

### Post by matt_symes on 2014-10-02
Hi

> **wog said:**
> I have X (gnome) up, so Ive been using whatever updater comes with that. I can use the terminal, since the commands are well-known. This version also comes with Synaptic, so I suppose I could also use that. Honestly, I use whatever system a helper suggests, because theyre familiar with something and Im not.

...Honestly, I installed 8.04 because I had it handy, and thought an older  version might cope better with an older architecture. I then expected I  could update to the latest and greatest version from there. I guess that  wasnt an accurate notion?


If you've just installed Hardy then there's no problem. You can wipe it and install something more appropriate.

Ubuntu distros have a lifespan and Ubuntu is more designed for newer hardware. There are other flavours of Ubuntu that use other desktop environments that use less resources and are more suitable for older hardware.

Amounst these are Xubuntu and Lubuntu.

> If 10.04 is EOL, then why would Hardy suggest it instead of 12.04 or 14.04? 

For your reference...

[http://fridge.ubuntu.com/2013/05/10/ubuntu-10-04-lucid-lynx-desktop-end-of-life-reached-on-may-9-2013/](http://fridge.ubuntu.com/2013/05/10/ubuntu-10-04-lucid-lynx-desktop-end-of-life-reached-on-may-9-2013/)

10.04 Desktop is EOL. Maybe it's offering to update common desktop and server packages ? Maybe one can only upgrade from LTS to the next LTS and not skip an intermediate LTS. TBH I'm not sure really.

> What are Xubuntu and Lubuntu based on, if not Unity?

AS i said, Unity, Xubuntu and Lubuntu use different Desktop environments (DE) but they all use Ubuntu under the hood, like cars with the same engine but different bodies.

Xubuntu is a flavour of Ubuntu that uses the XFCE DE and  Lubuntu uses the LXDE DE. Ubuntu is a flavour of Ubuntu that uses the Unity DE.

[www.duckduckgo.com]("http://www.duckduckgo.com") them and take a look at some of the screenshots for each.

Kind regards

---

### Post by QIII on 2014-10-02
Got rid of those berry dupes for you matt_symes.  One of those nights with the servers again.

---

### Post by matt_symes on 2014-10-02
> **QIII said:**
> Got rid of those berry dupes for you matt-symes.  One of those nights with the servers again.

Cheers QIII. I though it was my laptop having a brain fart :)

---

