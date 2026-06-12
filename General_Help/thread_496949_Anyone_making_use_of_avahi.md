---
title: "Anyone making use of avahi"
date: 2007-07-09
forum: General Help
---

### Post by RHTopics on 2007-07-09
Is anyone making use of the avahi-daemon or avahi-autoipd?

I have avahi-daemon set to not automatically start when booting the computer. 

I am considering uninstalling avahi-daemon and avahi-autoipd, but I thought first check out if they are worth keeping around.

---

### Post by kidders on 2007-07-10
Personally, I find avahi tremendously useful. Granted applications of mDNS are a little under-developed in Linux (at least when compared to Apple).

Tbh, your question is a little like asking whether blender, for instance, is worth installing. Some users won't be able to function without it ... others might not even know what it is. If you don't like/want avahi, there's no reason to keep it.

---

### Post by RHTopics on 2007-07-12
kidders,

Thanks for the reply.

I am glad that someone finds it useful.  I take it then you have a mixed Apple/OSX and Linux environment.  So are you using avahi to access printers and share files on your network?

> Tbh, your question is a little like asking whether blender, for instance, is worth installing. Some users won't be able to function without it ... others might not even know what it is. If you don't like/want avahi, there's no reason to keep it.

The avahi packages "avahi-daemon" and "avahi-autoipd" are installed by default not by choice which is the case with blender.  At least that is the what happens when you install Ubuntu 7.04 using the live CD.  So it is more a matter of removing unnecessary all ready installed software rather than trying out an application and then deciding you do not want to keep it.

---

### Post by kidders on 2007-07-13
> **RHTopics said:**
> The avahi packages "avahi-daemon" and "avahi-autoipd" are installed by default not by choiceThat's exactly right. The point I was making was that just because I find avahi convenient doesn't mean anyone else will hehe.

Like you said, OSX users will certainly always find avahi handy, but on a pure Linux network, it has its uses. Lately there has been some experimentation with doing all sorts of things with mDNS, eg some services that are normally provided by DHCP. Nautilus also has some mDNS support. Even on a Windows/Linux network, mDNS can be used, for example, to have Linux boxes show up in iTunes, although I don't know enough about Windows to say what else you could do with it.

I suppose the most important question is whether *you* have any Macs on your network. If you do, I'd be happy to go into more detail about how to get some useful functionality out of gizmos like avahi.

---

### Post by RHTopics on 2007-07-13
I have an old iMac G3 on my network, but it is running Ubuntu (Dapper 6.06).  Thanks for the offer of assistance.

Correct me if I am wrong, but it seems that with each release of Ubuntu, the deployment of avahi related software is increased.  But the deployment is somewhat behind the scenes with little information being provided to the end user.  It is as though the infrastructure is being installed with the actual applications to follow later after they are completed.

Case in point.  With Ubuntu 6.10, the avahi-daemon package is installed by default, yet it is turned off.  Ubuntu 7.04, has both the avahi-daemon and avahi-autoipd packages installed.  And they are active.  Yet there appears to be no applications installed to make use of them. Doing a Google search I found this article on PrinterDrake in the Ubuntu Wiki ([https://wiki.ubuntu.com/PrinterDrake](https://wiki.ubuntu.com/PrinterDrake)).  The goal of PrinterDrake is to replace gnome-cups-manager.  PrinterDrake utilizes avahi to discover network printers.

Here is the current blueprint for PrinterDrake [https://blueprints.launchpad.net/ubuntu/+spec/printerdrake](https://blueprints.launchpad.net/ubuntu/+spec/printerdrake) . As you can see, it is still under development.

---

### Post by kidders on 2007-07-13
There's nothing stopping you installing your own mDNS apps, I suppose. Don't let the fact that they don't come pre-configured out of the box deter you. After all, there's only so much that a post-install OS can/should contain.

You do seem right though ... it looks as though the Ubuntu devs may be trying to gradually increase the profile of mDNS in their operating systems. Perhaps it's a not-so-subtle hint to the community to start developing more apps that support a technology that's still in its infancy, and might need some encouragement.

---

### Post by RHTopics on 2007-07-13
I agree with your assessment that avahi is a "technology that's still in its infancy".

After doing some more searching, I found information on Apple's implementation of mDNS (bonjour) and how it relates to avahi.  I now have a better understanding on avahi's potential in Linux.

It will be interesting to watch this technology progress in Linux.

---

### Post by kidders on 2007-07-13
> **RHTopics said:**
> I agree with your assessment that avahi is a "technology that's still in its infancy".I was referring to mDNS in general, really. It's possible that it'll become much more widely used than it is now, in the future.

If you don't like avahi though, there are several other similar mDNS daemons around, that you could try.

---

