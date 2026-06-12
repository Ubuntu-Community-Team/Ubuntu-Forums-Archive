---
title: "How to get rid of GNOME?"
date: 2007-06-15
forum: General Help
---

### Post by loathsome on 2007-06-15
Hi there,

I recently installed kubuntu-desktop on my workbench. How do I remove everything that comes with "Ubuntu"; (ubuntu-desktop) including apps etc, and only keep Kubuntu-stuff?

Thanks!

---

### Post by earobinson on 2007-06-15
[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

---

### Post by loathsome on 2007-06-15
Thanks. I'll try that.

Though, I was hoping for a more cleaner solution.

---

### Post by earobinson on 2007-06-17
its just one line in the terminal. It would be nice if you could just uninstall one program that would do it all.

Let us know how it goes!

---

### Post by loathsome on 2007-06-17
Hi,

It went flawlessly, thanks a lot. I've collected the name off all the packages that comes with ubuntu-desktop, kubuntu-desktop and xubuntu-desktop if anybody else wants this:

[http://ubuntu.loathsome.us/doc/ubuntu-desktop](http://ubuntu.loathsome.us/doc/ubuntu-desktop)
[http://ubuntu.loathsome.us/doc/kubuntu-desktop](http://ubuntu.loathsome.us/doc/kubuntu-desktop)
[http://ubuntu.loathsome.us/doc/xubuntu-desktop](http://ubuntu.loathsome.us/doc/xubuntu-desktop)

Thanks,
loathsome

---

### Post by earobinson on 2007-06-19
sweet!

---

### Post by Qu4k3R on 2007-06-19
Could you use synaptics to remove ubuntu-desktop (completely, with it's dependencies :D ) ?

---

### Post by W. Irving on 2007-06-19
> **Qu4k3R said:**
> Could you use synaptics to remove ubuntu-desktop (completely, with it's dependencies :D ) ?

I'd say no, as ubuntu-desktop is needed to run synaptic.

If a snake (or eel, for that matter) tries to eat itself, will it eventually disappear into thin air?

---

### Post by earobinson on 2007-06-20
It would be really hard you would have to search for and uninstall all of those things.

---

### Post by stchman on 2007-06-20
> **loathsome said:**
> Hi there,

I recently installed kubuntu-desktop on my workbench. How do I remove everything that comes with "Ubuntu"; (ubuntu-desktop) including apps etc, and only keep Kubuntu-stuff?

Thanks!

I recommend downloading Kubuntu and freshly installing.  It is actually quicker to do.

---

### Post by DarkN00b on 2007-06-20
You can run the following command with no effect on your system:

```
sudo aptitude remove ubuntu-desktop
```

The only thing is that you need to reinstall it if you do a dist-upgrade. The ubuntu desktop is not necessary for your system to function. It is just a meta package that is there to install other packages.

---

