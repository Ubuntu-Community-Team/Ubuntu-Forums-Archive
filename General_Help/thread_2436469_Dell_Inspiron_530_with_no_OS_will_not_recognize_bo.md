---
title: "Dell Inspiron 530 with no OS will not recognize boot DVD"
date: 2020-02-06
forum: General Help
---

### Post by dellcomputer on 2020-02-06
I have seen this exact issue posted elsewhere involving the same computer and I have not been able to find a workable solution.

burned the ubuntu 18.04.3 iso to a dvd, verified it works when booted on other computers.

I am trying to boot it on a dell inspiron 530 with out a current operating system.  All I get is the message "[COLOR=#242729][FONT=Arial] "No Boot Device Available" press enter to retry 

I've changed bios configurations over and over again changing boot orders, etc.  searched dell pages, searched this forum, and see a lot of 530 owners with the same problem, but nothing that resolved it.  is there any hope here?  or does anyone want to buy some soon to be available computer parts from me?

**edit**
The dvd drive on the dell recognized other OS disks like windows 98, which it attempts to load but can’t find drivers (hardware compatibility issue), I haven’t tried later versions of windows because I’m not sure if I still have any on cdrom.

The computer itself was last known to have a windows vista operating system.

The computer that burned the iso image was running windows 10 home. Version 1909
DVD used was -R
[/FONT][/COLOR]

---

### Post by kevdog on 2020-02-06
Do you know the DVD drive is working?  Can you not boot from USB?

---

### Post by dellcomputer on 2020-02-07
Yes I meant to add the dvd drive is working.  I’m able to load a windows 98se disc from the drive in the dell.  (Of course it won’t actually install). The drive reads it no problem.

---

### Post by dellcomputer on 2020-02-07
Haven’t tried Putting the iso into a usb yet.

---

### Post by oldfred on 2020-02-07
How much RAM?
Since older system, may be better to use lighter weight flavor.
Light weight flavors
Lubuntu, xubuntu, Ubuntu MATE, Budgie
[https://wiki.ubuntu.com/UbuntuFlavors](https://wiki.ubuntu.com/UbuntuFlavors)

Not sure if still required or not.
[http://en.wikipedia.org/wiki/Intel_GMA](http://en.wikipedia.org/wiki/Intel_GMA)
 Older Intel video card: i915.modeset=1 or i915.modeset=0 newer:  i915.i915_enable_rc6=1

If Dell has an update to BIOS, you should install that.

Some have post this:
 Dell security software on Windows 7 ties in with the BIOS cannot write to drive

---

### Post by CelticWarrior on 2020-02-07
> **dellcomputer said:**
> Yes I meant to add the dvd drive is working.  I’m able to load a windows 98se disc from the drive in the dell.  (Of course it won’t actually install). The drive reads it no problem.

The Windows 98SE is a CD. So... The drive is working with CDs is all you can infer. There are different lasers for CDs and DVDs, one can fail while the other is still working. Or the drive may not be a DVD reader.

Try a USB instead.

---

### Post by GhX6GZMB on 2020-02-07
When burning the DVD, did you select the option "burn and close" or just "burn"?

---

### Post by dellcomputer on 2020-02-07
> **CelticWarrior said:**
> The Windows 98SE is a CD. So... The drive is working with CDs is all you can infer. There are different lasers for CDs and DVDs, one can fail while the other is still working. Or the drive may not be a DVD reader.

Try a USB instead.

I think you were very right.  Installed a different OS, tried cd-roms  they worked..dvd's...wouldn't read them


Have not been able to try the USB yet.  Dont know now which way ill go, may use a light version recommended above or just run it from the usb all together.

Thank you all for the input!!!

---

### Post by oldrocker99 on 2020-02-07
I believe that the best way to burn an image to a USB is Etcher, which doesn't require preformatting or anything. It is, IIRC, in the Ubuntu repos.

---

