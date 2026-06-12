---
title: "Really Need Help"
date: 2007-08-26
forum: General Help
---

### Post by Fonon on 2007-08-26
Whenever I try to use Synaptic, Upgrade Manager, etc, I get this error message : 'E:The package virtualbox needs to be reinstalled, but I can't find an archive for it.'

Also, the add/remove programs never lets me select a check box any more, I assume because of that.  Please help!

---

### Post by tzulberti on 2007-08-26
Try, from comsole: "sudo apt-get remove virtualbox" (this shoud unistall virtualbox, so don't use this if you are realy using it)

---

### Post by Fonon on 2007-08-26
> **tzulberti said:**
> Try, from comsole: "sudo apt-get remove virtualbox" (this shoud unistall virtualbox, so don't use this if you are realy using it)

I get this error message: E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.


That's direct from the terminal after I pout that command in.  Thanks for trying to help me, though.

---

### Post by nqsonk9 on 2007-08-26
I hope this will work :
sudo dpkg --configure -a

---

### Post by r4ik on 2007-08-26
Try,

sudo dpkg --remove --force-remove-reinstreq virtualbox

Good luck !

---

