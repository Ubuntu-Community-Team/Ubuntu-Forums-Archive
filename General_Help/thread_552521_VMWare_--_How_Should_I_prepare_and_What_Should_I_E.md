---
title: "VMWare -- How Should I prepare and What Should I Expect?"
date: 2007-09-16
forum: General Help
---

### Post by Battie on 2007-09-16
Hello everyone.

I've been dual-booting since I built this machine, but I realize how impractical it is when there are VM options available.  I want to run Windows from a virtual machine.  However, since I have a good, broken-in setup right now I want to make sure I know what's going on before I start.

The Questions:

Should I dedicate a partition to the new Windows installation? Perhaps blow away the "real" installation and use that partition?

If I understand correctly, the VM won't be able read anything but the virtual drive.  But can I fetch things I create on that drive from the Ubuntu side?

If all goes well, I'd want to merge my Windows/Ubuntu personal data partitions (I think).  Do I need to destroy and recreate both partitions as one, or can I just destroy one and expand the other (backups either way, of course!)?

Anything else I haven't thought of?

Thanks for your help!

---

### Post by HermanAB on 2007-09-16
As can be expected, it all depends on what virtual tool you use.

To install VMware, first update your system, then use Synaptic to install VMware server/player.  Once you installed the guest OS, install VMware-Tools on the guest - this speeds things up enormously to pretty much almost native speed.

A virtual machine is for all intents and purposes a separate machine, but Vmware and Virtualbox both allow you to set up shared folders with the host and you can click-drag-drop things around.

Note that you cannot mix virtual tools on one physical machine - they will clash.  You have to install only one and if you wish to switch to another system, then you may have to re-install the host.

I actually bought VMware Workstation - well worth it.  Dual booting is so 20th Century!

Cheers,

H.

---

### Post by AndyCooll on 2007-09-16
And to continue what HermanAB has been saying ...

You don't need a separate partition to run virtual machines. They create "images" which can be stored in your home directory (or anywhere else you choose).

It is also possible to "share" your files and folders. You'll need Samba for this. I have an XP VMware image which I haven't used for ages. I have a file server and I was able to map all the folders on it so that they were viewable via my XP image.

:cool:

---

### Post by Battie on 2007-09-16
Thank you for your responses.

The Samba thing sounds nice and simple.  Should I think of the guest image as being sort of similar to a Ghost image, then?

Finally, since VM-ing is supposed to be superior (or something) to dual-booting, can I expect to get some Serious Work done in this environment?  Say I want to run Corel Painter (no good in Wine) to do some large paintings.  Is that viable on a decent machine?  I suppose only experimentation would really tell, but it's nice to hear previous experience.

Thanks again!

---

### Post by fjgaude on 2007-09-16
Well, in VMware Server I use Xara Xtreme Pro and Jasc Paint Shop Pro and they run just about as fast as in a native Windows machine. I use WinXP Pro as my guest, giving it 512 MB of RAM. The Guest Tools make it all work fast. Here's some of the work I do:

[http://yantrayoga.typepad.com/noname/](http://yantrayoga.typepad.com/noname/)

Try it, you have nothing to lose and all to gain.

Good luck,

frank

---

### Post by GoodPanos on 2007-09-19
> Note that you cannot mix virtual tools on one physical machine - they will clash. You have to install only one and if you wish to switch to another system, then you may have to re-install the host.
Can you have both VMWare Server and Player installed?

---

### Post by fjgaude on 2007-09-19
> **GoodPanos said:**
> Can you have both VMWare Server and Player installed?

No, no... if you install player you will have to get rid of everything associated with it before server will install.

frank
[http://yantrayoga.typepad.com/noname/](http://yantrayoga.typepad.com/noname/)

---

### Post by GoodPanos on 2008-04-23
Can you have VMWare Player and VirtualBox on the same box (Gutsy Gibbon)?

I know VirtualBox is suppose to be able to open VMWare images but it won't open one of the images I have.  So I wanted to install VMWare Player but I'm worried it might conflict with VirtualBox.

Please advise.

---

### Post by AndyCooll on 2008-04-24
Yes, you can have them both on the same pc. They are two completely separate software apps and act independently of each other. 

I would also recommend you install VMware Server rather than VMware Player. It's a far more flexible version. Player just "plays" an image, server both plays and alllows you to create your own. It too is free (as in beer, that is) like Player.

:cool:

---

