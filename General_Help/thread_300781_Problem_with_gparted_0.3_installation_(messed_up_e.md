---
title: "Problem with gparted 0.3 installation (messed up everything)"
date: 2006-11-16
forum: General Help
---

### Post by Nameless_one on 2006-11-16
Hi I'm a new ubuntu user with a stupid problem. Sorry for the long post, but it's the shortest way to describe the problem. 

I have been trying to install the latest version of gparted for a couple of days now, as gparted 0.1 that comes with Dapper (which I am running) doesn't support merging and other useful features. 

I should note I am running Dapper with support for greek, everywhere, in the terminal and the GUI. 

I tried to install gparted 0.3 that I downloaded from the official site, and make informed me I need libpart v 1.7.1. After a lot of work I found that dapper comes with libpart 1.6 or so and that there are no available packages for the latest version in the repositories. I found a deb package for libpart 1.7.1 in launchpad.net (which was for feisty - from what I understand that means it is in development? not supported? ) and tried to install it, but a dependency wasn't met. Libc6. 

I found I had libc6 but after looking around some more, it turned out I needed a more recent version, which again wasn't a vailable for dapper. I found *that* in a deb package in launchpad again, and after I resolved a couple of dependencies (a good two hours) I installed libc6 2.5... 

After restarting, Synaptic told me there are broken packages (the replaced libc6 packages - **** me if I know why they were replaced, and not upgraded), and greek doesn't work in the terminal any more. What's more important, though is that synaptic doesn't let me do anything until I resolve the issue with the broken libc6 packages, and it won't let me uninstall them unless I also uninstall just about every basic package ubuntu needs (even ubuntu-base). 

I figured I'd uninstall the new libc6 2.5 that I installed, but guess what! The same as the libc6 packages. I have to uninstall the basic ubuntu packages. 

And on top of all that, the installed of gparted *still* can't find libparted 1.7.1 on my system (which was installed like a charm after I got libc6 2.5 working). 

Anyone able to help? This sure looks like an ugly deadlock. I am mainly interested in restoring greek support, and optionally gparted 0.3

---

### Post by Nameless_one on 2006-11-16
Bump.

---

### Post by darrenm on 2006-11-16
Is upgrading to Feisty not an option?

---

### Post by Nameless_one on 2006-11-16
Not really. I am trying to keep things as stable as possible, being a linux newbie, and having to deal with issues concerning an experimental, being-developped-at-the-moment release isn't my cup of tea right now.

---

### Post by Nameless_one on 2006-11-16
Another bump. I'm kind of desperate.

---

### Post by Nameless_one on 2006-11-16
One more bump. :(

---

### Post by Nameless_one on 2006-11-16
OK, I managed to restore the broken packages via bash, but the original problem still remains. How can I install libparted without messing everything up? 

Can I add the edgy repository to my sources.list and install the next libc6 from there? Will Dapper take it or crash?

---

### Post by dpm on 2006-11-16
Someone correct me if I'm wrong, but I believe libparted 1.7.1 comes with Edgy.

So you could just upgrade from Dapper to Edgy, which is a stable release.

On the other hand, why go through all this trouble if you can just download the gparted 0.3 livecd ISO at [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) ?

---

### Post by Nameless_one on 2006-11-16
I don't really know how to use it. I tried to mount it in ubuntu, but it didn't work. Do I have to physically burn it onto a CD and boot with it? 

Thanks for the reply.

---

### Post by jimbob on 2006-11-16
Yes you must download and burn the iso - but it is an excellent tool to have in your arsenal.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by dpm on 2006-11-16
> **Nameless_one said:**
> I don't really know how to use it. I tried to mount it in ubuntu, but it didn't work. Do I have to physically burn it onto a CD and boot with it? 

Thanks for the reply.

As jimbob said, you have to download it and burn the ISO.

If you are using Ubuntu, you can just navigate to the location where you downloaded the ISO with nautilus, right-click on the ISO file and select the entry "Write to Disc..." from the context menu.

I hope this helps.

---

