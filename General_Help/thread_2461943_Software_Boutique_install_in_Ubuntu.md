---
title: "Software Boutique install in Ubuntu"
date: 2021-05-10
forum: General Help
---

### Post by dddman on 2021-05-10
I have installed the mate software boutique (store) as a snap package from here:
[https://snapcraft.io/install/software-boutique/ubuntu#install](https://snapcraft.io/install/software-boutique/ubuntu#install)
It said install completed, but I'm not getting a launcher in applications.

I tried launching from the terminal and was instructed to:

sudo snap install ubuntu-mate-welcome --classic'

And I did, but still no launcher.  Trying to launch from terminal again tells me to run the above install command, which comes back already installed.

I like to get this working

---

### Post by dddman on 2021-05-10
I'm doing it right

[URL="https://phoenixnap.com/kb/snap-packages#ftoc-heading-3"]https://phoenixnap.com/kb/snap-packages#ftoc-heading-3

Neither package will open in terminal
[/URL]

---

### Post by deadflowr on 2021-05-10
Software Boutique only shows in Mate.
If you have the welcome snap then try
```
ubuntu-mate-welcome --boutique
```
See if that launches it, if so, try locking/adding the launcher to the favorites bar; if even possible.

---

### Post by dddman on 2021-05-10
Thank you

That solved it.  I received the message ubuntu-mate-welcome is not supported on Ubuntu.

---

### Post by dddman on 2021-05-10
I already installed aptitude package manager, its not what I'm after.

Looks like I'm down to one last option.  Synaptic package manager

---

