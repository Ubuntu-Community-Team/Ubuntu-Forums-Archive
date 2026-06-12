---
title: "Using Ubuntu OS on Mobile Android"
date: 2017-09-03
forum: General Help
---

### Post by angel mike on 2017-09-03
The website [www.instructables.com](www.instructables.com) gives a method for installing  a Ubuntu OS on an android mobile phone. Is this really possible ?

---

### Post by TheFu on 2017-09-04
I didn't follow the link. You didn't link to instructions anyway, so nobody can possibly say if THAT SPECIFIC method might work or not.  The sight is reputable, though I don't usually go there for anything computer related.

Yes.  I've installed Ubuntu onto my Android tablet (phones are too small), but there are many, many, caveats.

The way I did it was to make a chroot in android - this is a normal Unix feature that any OS running any variant of Unix supports (so basically anything except MS-Windows).  Then I loaded an image with Ubuntu using the same ARM CPU that my tablet used.  Then I setup VNC inside the chroot, since the only way to access it is via a remote desktop.  Then I found a VNC client for Android, ran it, connected to the VNC server running inside the chroot.

This is all very inefficient. Slow. Problems with using a mouse-based GUI without a mouse.  Problems with keyboard translations.  Most phones/tablets are limited in RAM and CPU.  This means everything is slow.  After all, 2 OSes are running on the same phone.  After about a week, I flushed the Ubuntu install. For me, it wasn't worth it.
These days, I use a chromebook - ran with "crouton" for a few months before wiping it and loading a full Ubuntu-based install. That is 1000x better.  Crouton also uses the chroot method, but a $150 chromebook is much more capable and chromeOS is much more like an Ubuntu install.  Only a few things don't work, things that require kernel modules.  I suspect that most people wouldn't care, but for me, access to NFS is mandatory for any OS. NFS isn't supported with chromeOS.

You should try the phone method.  Phones are faster and have more RAM these days.  The tiny screen will still be a huge problem.  See how bad/good it is for yourself.  I vaguely recall that getting the image was a dodgy download.  I cannot recall if a root'd phone was needed or not.  My tablet was rooted.

If you allow remote VNC to the phone, you can use a desktop or laptop to remote into it and setup things. That isn't very secure, so don't leave it setup that way when outside your home LAN.  Very dangerous.

---

### Post by angel mike on 2017-09-04
Thanks Thefu for very useful reply - will follow your suggestions. Mike

---

### Post by TheFu on 2017-09-04
I just thought of something else - if you don't need a GUI, but want access to almost all the normal Unix CLI tools, then this chroot method **is** very useful.  Without the GUI, many of the negatives of a 5in screen would be gone too.
On Android, I use a "terminal" called IDE Terminal. It provides a minimal Linux environment - ssh and a few other commands. It doesn't have rsync and about 250 other commands I'd love.  So I could use a chroot ubuntu-server system on my Android devices, provided I had a usable keyboard.  With my tablet, I have a USB keyboard (the case includes it), so typing is pretty easy.  Also picked up a travel Bluetooth keyboard way back when I was traveling with a Nokia N800 (debian variant) in 2007.  Did central and south America with that setup, nothing else.  My current Android phone is probably 10x faster than that N800.  OTOH, I have a $50 8in Android tablet that is probably 10x fast than the phone now too.  Perhaps ... but my current tablet isn't connected to google and nobody has root'd it, so I'd need to do a little more research.

A few links that I haven't read yet, but part of my CLI-only on Android goal:
* [http://www.linux-magazine.com/Online/Features/Convert-an-Android-Device-to-Linux](http://www.linux-magazine.com/Online/Features/Convert-an-Android-Device-to-Linux)
* [http://www.kevinboone.net/kbox.html](http://www.kevinboone.net/kbox.html)
* [https://termux.com/common-packages.html](https://termux.com/common-packages.html) - might be all that I need.  It even includes **ssh-copy-id**!

---

### Post by angel mike on 2017-09-04
Thanks again Thefu - appreciate the response . Mike

---

