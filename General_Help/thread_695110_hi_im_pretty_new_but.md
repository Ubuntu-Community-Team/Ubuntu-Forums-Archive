---
title: "hi im pretty new but"
date: 2008-02-12
forum: General Help
---

### Post by tomarmstrong on 2008-02-12
hi im pretty new to ubuntu, im using 7.10 and i tried downloading nvu wysiwyg editor and it ```
your system has broken dependencies. This application can not continue until this is fixed, To fix it run 'sudo synaptic' or 'sudo apt-get install -f' in terminal window
```
so i do that and i enter 'sudo synaptic' or 'sudo apt-get install -f' that part into it and press enter and it comes up with enter password but when i try to type my password it dose not come-up. Im sorry if i do not make myself clear but i have tried looking round.

its ok now i found out my problem

---

### Post by SgtDude on 2008-02-12
Just to be sure, are you entering

**'sudo synaptic' or 'sudo apt-get install -f'**

all on a single line, or are you entering

**sudo synaptic**

*or*

**sudo apt-get install -f**

Into the command line?  You only need one or the other (and make sure to not type in the quotes).

Hope this fixes your problem.

---

### Post by PeterJS on 2008-02-12
> **tomarmstrong said:**
> hi im pretty new to ubuntu, im using 7.10 and i tried downloading nvu wysiwyg editor and it ```
your system has broken dependencies. This application can not continue until this is fixed, To fix it run 'sudo synaptic' or 'sudo apt-get install -f' in terminal window
```
so i do that and i enter 'sudo synaptic' or 'sudo apt-get install -f' that part into it and press enter and it comes up with enter password but when i try to type my password it dose not come-up. Im sorry if i do not make myself clear but i have tried looking round.

its ok now i found out my problem

it is accepting keyboard input, it's just not giving you any visual feed back. This is a historical security measure from the old days of unix, there's a debate around here every now and then as to how effective it is a a security measure.

---

### Post by Herman on 2008-02-12
Did you get it fixed?

:) We don't use NVU anymore in Ubuntu, we use KompoZer now instead. KompoZer is NVU with a new name, and it's more up to date. KompoZer is easy to install in Ubuntu using 'Applications'-->'Add/Remove', or with Synaptic Package Manager, or with an apt-get command.
```
sudo apt-get install kompozer
```:) To install software in Ubuntu, it's best to avoid downloading  it from sites on the internet. Not only because it's ten times as much work, but also because it might not be safe and it might break your system.
One of the great features of Ubuntu is our [SecureApt]("https://help.ubuntu.com/community/SecureApt") system where software for Ubuntu is guaranteed to be readily installable in Ubuntu and clean (secure).

:) Here's an article on repositories so everyone will understand what those are: [Repositories]("https://help.ubuntu.com/community/Repositories/Ubuntu")

:) Here's a great tutorial everyone should read [Complete Guide to Installation in Ubuntu]("http://ubuntuforums.org/showthread.php?t=500020") by starcraft.man.

I'm typing this not only for you but for other new members here as well, we have lots of other people new to Ubuntu every day, so those links might help any other new people who may also happen to read this post.

Regards, Herman  :)

---

### Post by tomarmstrong on 2008-02-12
thanks guys but yeah i found out that you do not see any characters you enter. imo they should just be covered up with stars.

---

### Post by PeterJS on 2008-02-12
> **tomarmstrong said:**
> thanks guys but yeah i found out that you do not see any characters you enter. imo they should just be covered up with stars.

And thus the debate rolls on.

---

