---
title: "Virtualbox troubles"
date: 2007-07-06
forum: General Help
---

### Post by godd4242 on 2007-07-06
Hello everyone.

E:The package virtualbox needs to be reinstalled, but I can't find an archive for it.'

That is the new error I get when I try to run sudo update, or open synaptic, or sudo apt-get install anything.


Anyone know what the trouble is?

PS: I have never actually used virtualbox, I'd be happy to get rid of it, but I can't even do that.

Sudo apititude rm virtualbox tells me it can't find virtualbox and gives me E:The package virtualbox needs to be reinstalled, but I can't find an archive for it.' again


Any advice or anything would be greatly appreciated.

---

### Post by eggdeng on 2007-07-06
Try ```
which virtualbox
``` or ```
sudo updatedb
``` and then ```
locate virtualbox 
``` to see if / where it is installed on your system.

---

### Post by godd4242 on 2007-07-08
> **eggdeng said:**
> Try ```
which virtualbox
``` or ```
sudo updatedb
``` and then ```
locate virtualbox 
``` to see if / where it is installed on your system.

I get no return from either command

---

### Post by godd4242 on 2007-07-12
Well, this is a formal request for this thread to be closed.

I'll try to post with a different title in the beginners forum, and see if anyone knows how I can just get rid of virtualbox without synaptic or the terminal telling me I can't get rid of virtualbox because I don't have virtualbox.


Later chaps

---

### Post by SendDerek on 2007-07-12
VirtualBox is the only app I know of in Linux that actually uses the capitol V and B in the name.  So, you have to type "VirtualBox" instead of "virtualbox" or else synaptic will have no idea what you're talking about.

You could also try this:
> 
sudo dpkg --purge -r VirtualBox

and if that doesn't work try this: sudo dpkg --purge --force-remove-reinstreq -r VirtualBox


---

