---
title: "DOES NOT WORK: sudo dpkg-reconfigure xserver-xorg"
date: 2008-05-05
forum: General Help
---

### Post by elustran on 2008-05-05
Whenever I use dpkg-reconfigure, the settings wizard never prompts me for video card or display information, leaving my xorg.conf file void of settings information, just stuff like "configured video device" and "configured screen".

I tried to do this in order to fix my problems with xrandr not allowing me to change my screen resolution.

maybe I shouldn't have tried upgrading.

---

### Post by Rocket2DMn on 2008-05-05
That is because Hardy is using a new version of X that relies more on autodetection than xorg.conf - it's driving a lot of people insane.  What card do you have?
```
lspci | grep VGA
```
I'm not exactly sure how to troubleshoot resolution settings any more, but I have heard of "xfix" or "grandr", or you can try manually adding the Modes to the Device section in xorg.conf.

---

### Post by elustran on 2008-05-05
I have a radeon 9800pro.  I've tried adding display settings to my xorg.conf file, but that hasn't done anything.

My problem is still xrandr.

Another problem I'm having is that linux won't shut down.  I'm not sure if there are other problems too, but CIFS VFS is throwing me a 'server not responding' error and hanging.  I keep on having to restart manually, and I can only hope that isn't causing more problems.

---

### Post by Rocket2DMn on 2008-05-05
Some other people have been having problems with 9800s, you should search the forums and see what comes up.  You will want to use restricted drivers, too, I suggest using EnvyNG if the built in restricted drivers from System->Administration->Harwdare Drivers doesn't do the trick
[http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A)

As for your CIFS VFS problem, do you have an entry in /etc/fstab for a network partition that is not mounting?

---

### Post by elustran on 2008-05-05
I tried envyng, but it didn't seem to do the trick.  I ran their driver installer and selected ATI, but I'm not sure it actually changed anything.  I wasn't getting any errors as far as I know.  I'm going to have to go through the faq more carefully to see if I missed anything.

As far as the shutdown problem, I took out a line that was mounting a shared cd-rom drive via cifs because it seemed the most likely to be confusing cifs vfs, but I'm still getting thrown the following error:

CIFS VFS: server not responding
CIFS VFS: no response for cmd 114 mid 51

I still haven't checked around for the particular error yet - I probably will this afternoon.  I think if the next couple of fixes I try do nothing, I'm just going to do a clean install.

---

