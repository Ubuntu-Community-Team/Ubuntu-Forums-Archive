---
title: "ubuntu laptop mode"
date: 2008-01-15
forum: General Help
---

### Post by Elena678 on 2008-01-15
Hello Ubuntu people :)

I have a laptop, and i was looking a bit around in Synaptic, And I found ubuntu-laptop-mode. I readed that it reduce power consumption by allowing the hard drive to spin down for longer periods of
time. (is this save ?? )

when I would like to install the package, it is telling it would delete ubuntu-desktop.

so, can somebody tell me what happens to my laptop when i install it, and if it is a good idea to install it? in fact i am happy with my system, but battery live is always nice :)

greetings 

Elena

---

### Post by frigaut on 2008-02-27
Exactly the same situation here. I'm also happy with my current setup, but as you say, more battery life can't hurt. but there is simply not enough information attached to the package and I don't dare to install it and remove (or let synaptic remove) all that other core stuff.
Hope you'll have an answer.

---

### Post by jorgecarrillo150990 on 2008-02-27
Same here, but as for deleting the ubuntu-desktop, I dont think is a good idea...

---

### Post by pointone on 2008-02-28
ubuntu-desktop is only a [metapackage]("https://help.ubuntu.com/community/MetaPackages"). It doesn't contain any actual files; it only depends on other packages to be installed. When you make a change that removes or changes any single package found within the metapackage, you no longer "offically" have that metapackage anymore... although all the other packages it depends on remain untouched.

In short, you should be fine just going right on ahead with the change.

As far as the usefulness of ubuntu-laptop-mode, I think there's already some laptop-specific power saving stuff already installed by default, but I could be wrong. Give it a shot and let us know!

---

