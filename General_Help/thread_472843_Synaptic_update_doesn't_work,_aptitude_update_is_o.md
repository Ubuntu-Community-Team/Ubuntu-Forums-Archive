---
title: "Synaptic update doesn't work, aptitude update is okay"
date: 2007-06-13
forum: General Help
---

### Post by Tomlin on 2007-06-13
All of a sudden, synaptic has stopped working (sort of). It fires up okay and tells me what updates are available, but clicking on the "install updates" DOESN'T do anything.

I can successfully "sudo aptitude update".

Synaptic works fine for installing other software, just NOT updates.

I'm sure there's an easy fix. Do I remove synaptic and re-install it? What do the gurus say?

Thanks.

---

### Post by bapoumba on 2007-06-14
Do you "mark the packages for upgrade" and then "apply changes" ?

---

### Post by Tomlin on 2007-06-14
I use gnome. When there are updates to specific packages, a small icon appears in the top menu bar (upper right, near the clock). When I click on the icon it opens a window displaying what packages are available to update. All are checked by default. I click on the "install updates" button and it **USED** to download, then update those packages.

Now, when I click the button it opens a window saying something like "building dependency tree" (always did that) but it never installs the packages.

If I open a terminal and type:

sudo aptitude update

it updates the checked packages, and removes the icon in the menu bar.

I guess I could continue doing that, but I'd like to know what happened.

Thanks

---

### Post by bapoumba on 2007-06-15
Several things:

1- you are actually talking about update-manager (the one that pops up with a small orange icon).
2- in order to apply updates in a terminal, you have to run
```
sudo aptitude update
sudo aptitude upgrade
```
3- Do you have any error message if you run 
```
update-manager
```

---

### Post by Tomlin on 2007-06-15
Thanks for the reply.

Yes, update-manager is what I'm talking about.

Running:

*sudo update-manager* gives me the following **warning**:

/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)

but the program **does** run.

My system is up to date so I can't tell you if clicking the "Install updates" button will work, since it's grayed out.

---

### Post by bapoumba on 2007-06-15
Could you try to run **update-manager** without the sudo ?

---

### Post by Tomlin on 2007-06-15
Without the *sudo* I get:

/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)

and this pop-up window:

[IMG]http://phase1.com/images/error.png[/IMG]

---

### Post by bapoumba on 2007-06-15
Strange, I do not use update-manager (just aptitude), but it does run without sudo (did not think of it, but as its a GUI, you should use gksudo anyway).
What flavor or Ubuntu are you running ? There is a bug on update-manager, but its only when upgrading the system to a newer version, as far as I can tell:
[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/67066]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/67066")

---

### Post by Tomlin on 2007-06-16
I'm using dapper.

I just updated "language-pack-gnome-en" this morning. I had the same problem as before, re-booted and tried again, and it worked. I have no idea why.

Thanks again for your help.

Tomlin

---

