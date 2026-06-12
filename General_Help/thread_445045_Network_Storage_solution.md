---
title: "Network Storage solution??"
date: 2007-05-15
forum: General Help
---

### Post by simonsocial on 2007-05-15
Didn't really know where to put this thread but here goes anyway...

What i'm after is a Home Network Storage solution that a Windows, Mac and Linux based systems can access. Maybe even run Ubuntu from the NAS (if thats possible). I after around 500GB of capacity.

Has anyone get any ideas??

---

### Post by prozacgod on 2007-05-15
If you are just looking at a quick fix, I'd say get a NSLU2, Also, check out the dd-wrt.org project and the list of hardware they support.   There are several that have enought specs to run a full distro, but they are ARM based, I don't think ubuntu has an ARM port as of yet..

Watch to make sure the device you choose can support 500gb drives, or if you get a device with USB2.0 ports it should work as the controller is on the portable drive itself.  If you put dd-wrt or say openwrt on the device you can even raid across portable USB drives ;)   Get a terabyte of space :D

-Prozacgod

---

### Post by DonQuichotte on 2007-05-15
I have a Synology DS-101j (NSLU) and it's awesome. Newer models support hds of the capacity you're after.

I've got the hack done on it and can access it by ssh and telnet . In the network it is visible as a samba server to my Windows and Linux comuters, and I can run a bittorrent client and many other applications on it.

After installing the hack I've had several problems though, but all of them were easily solvable.

---

### Post by MontanaMax on 2007-05-15
I'll add a +1 to the NSLU2 by Linxsys - it's been rock solid and easy to administer. Plugged right in, and the Ubuntu / Kubuntu / Mac and M$ (it's work issued) machines all hooked right up to it. 

I also have a two year old Buffalo Linkstation that often serves as a door stop, and will soon be opened gently with a crowbar as repayment for many wasted frustrating hours it shared with me just trying to do basic backup and samba connections. (I had a horrible time with this one - definately not recommened at any price.)

---

### Post by YourSurrogateGod on 2008-04-09
Hmm... what if you want to go really big? Say, 2 terabytes? I'd love to consolidate all of that in something that's redundant, central and cheap. Any suggestions?

---

### Post by Shredder11 on 2008-07-10
I have a Synology DS101j with a 300GB drive but I am unsure of the maximum size drive it can take.  I too would love to use a couple of 1TB drives if possible.  Even 1.5TB would be great.

Anyone out there currently using the DS101j with really large drives?  Also is there any limit to what size drives can be plugged into the USB ports?

---

### Post by flintflake on 2008-07-11
Another nod for the NSLU2.   I picked mine up from Amazon for less than $50 a few months back.  Works well with Ubuntu and Windows.

---

