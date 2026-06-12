---
title: "upgrading from 12.04LTS to Raring or newer?"
date: 2013-12-28
forum: General Help
---

### Post by kurja on 2013-12-28
This has been asked and discussed before I'm sure but I couldn't find an answer... So, now I have the 12.04 Precise installed, and I want to try gimp's [16 bit editing dev version]("https://launchpad.net/~otto-kesselgulasch/+archive/gimp-edge") but as far as I can tell it's only for raring, saucy and trusty. Checking for updates in 12.04 I have the option of upgrading to 12.10 quantal which isn't recent enough, if I do that can I then upgrading further to a newer version? And would that be expected to "just work"?

---

### Post by deadflowr on 2013-12-28
It's definitely possible.
Though I think upgrading two releases at once might be a little stressing, both on the machine and user.
I know 13.10 has a new upgrade option on the livecd letting users upgrade their system via the cd rather than the net.
Don't know if it would upgrade a 12.04 to 13.10 though.
Personally, if I wanted to move beyond one release, I'd do a quick and easy fresh install.
Back up my files and start cleanly.
But that's just me(and quite possibly a million other users).

---

### Post by kurja on 2013-12-28
Yea I'd prefer a clean install too, except for losing two year's worth of tweaks and installs and whatnots ;) But on a more serious note, I most likely would clean upgrade to the next LTS when it comes out anyway, right now I'm even thinking of upgrading just so I could try the >8bit gimp.

---

### Post by deadflowr on 2013-12-28
There are so many little changes between precise and saucy that you may find some of the tweaks you've set unusable now.
Or needed to be reset, differently than they were on precise.

---

### Post by kurja on 2013-12-28
yeah. Is it possible to install a newer version of ubuntu parallel with precise? So I could choose which one I want to fire up at boot, like some people have windows and linux side by side.

---

### Post by deadflowr on 2013-12-28
Side by Side is suppose to work on the install disk.
I've used it in the past, but have no idea how well it still works.
When you get to the where/how to install Ubuntu on the install disk, it should list a side by side option.
When you choose this, you can toggle/slide the partition bar that appears at top to allocate how much space each will get.
again, though, haven't used this for a couple of years, so how well it works now is something I don't know.

---

### Post by grahammechanical on 2013-12-28
I have mulitple installs of Ubuntu and its flavours and I can multi-boot into any of them. All we need is a 20-25GB partition and then we use the Something Else option. And also to know how to partition. 

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

With the something else option at the Installation Type screen we select the partition we want to install Ubuntu in and click Change. In the dialog box that appears we select Use As to be Ext4. We tick the format box. We select a mount point of / and then click OK. Now we are back at the Installation type screen where we click Install Now.

Oh, please remember that 1304 and 13.10 each only have 9 months support. But you will get through to the release of 14.04.

Regards.

---

