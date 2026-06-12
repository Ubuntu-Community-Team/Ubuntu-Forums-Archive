---
title: "Remote booting with the live CD?"
date: 2005-04-10
forum: General Help
---

### Post by quilted on 2005-04-10
Hi all,

I'm running Ubuntu at home on my development machine and I'm very happy with it. However I'm travelling a lot and I can't afford a decent laptop at the moment(and I have a big luggage as it is), so I rely on using other peoples computers when working. I've tried using VNC to connect to my dev box but I find it too slow to be really usable on anything other than a LAN. I've recently tried using the Ubuntu live CD and while it's working well on most machines it's a bit tiresome to configure it every time and working with files over FTP isn't exactly ideal.

So my question is: Is it possible to boot up with a live CD and use the settings, files and applications on my home box over the network, but executing everything on the machine I'm sitting at? Basically using it as a thin client.
I've been a BeOS user until recently so I have no experience with nfs and that kind of stuff. But I would imagine that it would be somehow possible to mount the partitions of my home box using nfs when booting the live CD, and only use the CD for loading the kernel and drivers. Is that possible to do? And how hard would it be to modify the live cd to do this? (I don't want to enter boot paramters every time I boot)
Perhaps there is another live CD distro that will do this already, but since I use Ubuntu at home I figured using the Ubuntu live would be the best choice.

I hope my question was clear enough.
Thanks for your time.

---

### Post by localzuk on 2005-04-10
I think it would probably be easiest to create a custom live cd:

[http://www.ubuntulinux.org/wiki/LiveCDCustomizationHowTo](http://www.ubuntulinux.org/wiki/LiveCDCustomizationHowTo)

And use a USB key (they can be picked up for a few pounds).

That way, you can have your custom settings and files without needing any sort of network connection.

---

### Post by quilted on 2005-04-10
Thanks for the reply. I guess I wasn't clear enough though.
My main wish is to be able to use an environment that is identical or as close as possible to my home system. VNC would have been ideal if it was fast enough.
If I was to use an USB key to work with my files I'd have to sync it with my harddrive all the time and it's not something I wish for. Besides I'd need a rather large one to be able to store everything I need.

Isn't it simply possible to instead of mounting an USB key, mount an NFS partition instead? Besides, the USB-key trick only works as a home directory right?

[QUOTE=localzuk]
And use a USB key (they can be picked up for a few pounds).

That way, you can have your custom settings and files without needing any sort of network connection.[/QUOTE]

---

