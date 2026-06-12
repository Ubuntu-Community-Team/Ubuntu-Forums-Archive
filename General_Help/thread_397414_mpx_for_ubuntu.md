---
title: "mpx for ubuntu"
date: 2007-03-30
forum: General Help
---

### Post by Mr..Yeti on 2007-03-30
You may have heard of the Multi-Pointer Xserver, a modification to the xserver to allow more than one mouse and keyboard. [http://wearables.unisa.edu.au/mpx/]("http://wearables.unisa.edu.au/mpx/")

It sounds very cool, imagine a dual-monitor setup, with two people using one monitor each, while they each have a separate mouse and keyboard. Or for ambidextrous multi-taskers you could do twice as much!

Has anyone tried this on edgy or feisty. There is already a live-CD using dapper.
Cloning the Xserver is probably beyond my reach, although if it is easier than it sounds it might be ok.

So... just tell me anything about it really.

---

### Post by motin on 2008-01-31
I agree - this is awesome!

I'd use it to be able to use the wiimote and a mouse independently, or even two wiimotes using the wiimote whiteboard technique for cheap linux multitouch functionality.

Care to write a specification on providing MPX as an alternative? It would be great to be able to have both X variants available on the same machine and be able to switch between then using Fast user switching for instance. 

First however, maybe a dedicated MPXubuntu needs to become a reality.

This is the future! ;)

---

### Post by nfox on 2008-02-10
Yes, it's as cool as xservers can get. I'm installing it now and will gladly share details of cloning x. 

There is no specific documentation on it for our distro. It should be added somewhere so anyone with success, share here.

---

### Post by motin on 2008-02-10
> **nfox said:**
> Yes, it's as cool as xservers can get. I'm installing it now and will gladly share details of cloning x. 

There is no specific documentation on it for our distro. It should be added somewhere so anyone with success, share here.

Great! I'll stay tuned for now then and don't forget to post any problems you encounter and I'll try to help you. 

Cheers!

---

### Post by nfox on 2008-02-10
Yea, I don't want to sound overly optimistic. This is a pain in the bash. 
First and foremost, I need my Nvidia driver working correctly. I've got the cruddy 'nv' going and the switch to 'nvidia' causes it to either blank-screen or stick at 640x480 res.

First things first. If you happen to have some advice, Envy failed me, Nvidia's latest driver failed me and a slew of other resources.

Just in case, it's:
nvidia geforce 5500
gutsy x86


After this is fixed, I'll post my steps

---

### Post by motin on 2008-02-10
> **Mr..Yeti said:**
> You may have heard of the Multi-Pointer Xserver, a modification to the xserver to allow more than one mouse and keyboard. [http://wearables.unisa.edu.au/mpx/]("http://wearables.unisa.edu.au/mpx/")

It sounds very cool, imagine a dual-monitor setup, with two people using one monitor each, while they each have a separate mouse and keyboard. Or for ambidextrous multi-taskers you could do twice as much!

I just realized that you didn't mention the "simultaneously" word - which is MPX's big thing. For what you are describing (multiterminal / multiseat) there are other solutions around as well. Read more here:
[http://en.wikibooks.org/wiki/Multiterminal_with_Xephyr](http://en.wikibooks.org/wiki/Multiterminal_with_Xephyr)
[http://netpatia.blogspot.com/2006/09/multiseat-computer-with-ubuntu.html](http://netpatia.blogspot.com/2006/09/multiseat-computer-with-ubuntu.html)
[http://research.edm.uhasselt.be/~jori/page/index.php?n=Misc.DualSeatX](http://research.edm.uhasselt.be/~jori/page/index.php?n=Misc.DualSeatX)
[http://oldwiki.linux-vserver.org/MoreUbuntu](http://oldwiki.linux-vserver.org/MoreUbuntu)

MPX provides the added bonus that the mice and keyboards can interact on the same desktop simultaneously without requiring modification of window managers or applications in general.

---

### Post by nmz787 on 2008-04-21
I wrote this HOWTO for MPX on Ubuntu Gutst 7.10

[http://jisag.rit.edu/MPX/mpxhowto.html](http://jisag.rit.edu/MPX/mpxhowto.html)

hope some people make some use of this other than myself!

---

### Post by ibbuntu on 2008-05-04
> I wrote this HOWTO for MPX on Ubuntu Gutst 7.10

[http://jisag.rit.edu/MPX/mpxhowto.html](http://jisag.rit.edu/MPX/mpxhowto.html)

hope some people make some use of this other than myself! 

I'd like to, but that link appears to be broken....

---

### Post by brnetonboy on 2008-06-10
I would love to get this running on Ubuntu as well. I have Hardy Heron... alas the link above is broken! Does anyone know where it is?

I didn't know this thread existed, but there is another plea for Ubuntu MPX support here: [http://ubuntuforums.org/showthread.php?p=5153570#post5153570](http://ubuntuforums.org/showthread.php?p=5153570#post5153570)

---

### Post by motin on 2008-06-11
> **brnetonboy said:**
> I would love to get this running on Ubuntu as well. I have Hardy Heron... alas the link above is broken! Does anyone know where it is?

I didn't know this thread existed, but there is another plea for Ubuntu MPX support here: [http://ubuntuforums.org/showthread.php?p=5153570#post5153570](http://ubuntuforums.org/showthread.php?p=5153570#post5153570)

Thanks, let's unite in one thread and get things cooking. The best news, as stated in the above thread is probably: [Hooray, MPX is merged to master!]("http://ubuntuforums.org/showthread.php?t=809663&highlight=mpx")

Now it should be but to build standard X from git to get this cooking! Anyone that has the ability to try this anytime near? I will have a go at it in a few weeks but currently I'm too swamped to risk screwing up my X server...

---

### Post by Unislash on 2008-06-20
Heya,

I am a fairly new one to ubuntu and can't really offer anything in terms of development help, but i thought that i'd just say that i would love this software on my ubuntu system as well :D

Hopefully we can get someone to get it working!

Cheers,
Unislash

---

