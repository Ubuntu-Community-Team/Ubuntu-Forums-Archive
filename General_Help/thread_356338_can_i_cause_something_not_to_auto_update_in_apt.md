---
title: "can i cause something not to auto update in apt?"
date: 2007-02-08
forum: General Help
---

### Post by nephish on 2007-02-08
hello there, is there a way i can have a package not upgrade ? i have some special kernel modules set up and i would like to keep my current kernel 

just wondering if there is a way to keep apt from updating my kernel

thanks

---

### Post by etank on 2007-02-08
Take a look at this page [http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html). Its called pinning and it is described at the bottom.

---

### Post by nephish on 2007-02-08
great, thanks for this.

---

### Post by dagnabit dang doohickey on 2007-02-08
I find the easiest way to handle this is with Synaptic. In Synaptic's "Package" menu, you will find the "Lock Version" setting.

---

### Post by itchanddino on 2007-02-08
Is there anyway to see/sort packages that you may have accidentally locked and "unlock" them within synaptic?

---

### Post by dagnabit dang doohickey on 2007-02-08
In Synaptic's "Settings" menu, you'll find the "Filters" submenu. In the "Filters" window, create a new filter (button in bottom left area), name it (top left), and make "pinned" the only checked box.

Now you have a custom filter that will show all your locked(pinned) packages.

---

### Post by itchanddino on 2007-02-08
Is it easy to unpin them?

---

### Post by NT4usB on 2007-02-08
> **itchanddino said:**
> Is it easy to unpin them?
exactly the same steps as 'pinning' them

---

