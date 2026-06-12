---
title: "Error in syanaptic"
date: 2008-04-18
forum: General Help
---

### Post by Rikketik on 2008-04-18
When I open synaptic I get this error message.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

What do I need to do?

Help me please.

---

### Post by TeoBigusGeekus on 2008-04-18
Well, just open a terminal and type
```
sudo dpkg --configure -a
```

---

### Post by forestpixie on 2008-04-18
You need to run the command as given - nearly - you'll need to use sudo to give it root rights, open aterminal

```
sudo dpkg --configure -a
```

If you've not done so yet - sudo needs the password, but when you enter it doesn't appear - carry on it is there and enter.

---

### Post by whouseswindowsanyway on 2008-04-18
these don't always work -- i had this prob once and i had to goto /etc/apt/archives and delete all the files in their (need root) ... and then also run :
sudo apt-clean

---

### Post by Rikketik on 2008-04-18
I needed to be root to do the command, I'm running it now in Terminal As root,

Thanks

---

### Post by george9233 on 2008-04-18
I once got that problem as well. It's probably caused by forcing the dpkg to quit while it's still downloading or installing something. In my case I just entered that command and waited for the download and installation to finish and everything went right.

---

### Post by Rikketik on 2008-04-18
Everything worked perfectly, thanks for help. I'm quite new in Ubuntu so I haven't any idea what to do.

---

