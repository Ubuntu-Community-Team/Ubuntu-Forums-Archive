---
title: "using ./configure"
date: 2007-08-01
forum: General Help
---

### Post by OoooMatron on 2007-08-01
Is there anyway to make configure report a list of dependencies rather than just falling over every time it doesn't find one?

I find myself spending hours running ./configure and installing dependencies. Would be much quicker if it told me what was missing all in one go so i can install them all in one go.

---

### Post by Shib on 2007-08-01
Not really. You can either read the INSTALL file, if that's included... or hunt down some documentation online. They usually list somewhere what the dependancies are, but not always.

This, by the way, is the main reason such wonderful programs like apt and yum exist, to solve the dependancies for you, and to create a standard way of releasing a package.

---

### Post by OoooMatron on 2007-08-01
yeah and using packages is all well and fine until you use something not in the repo's;)

---

### Post by Shib on 2007-08-01
such as?

there's a ton of obscure repos for weird things...

unless you're talking about some uber beta application.

hey actually... if you're getting build issues... try doing a "apt-get build-dep gaim"... that'll pull down most of the compliation tools required to build most apps.

---

### Post by OoooMatron on 2007-08-01
I'm not getting build issues I just asked if there was a way to list the dependencies from the configure option that was all.

For example, when I use PCLINUXOS and I want to build the latest version of Gnome I find it a complete nightmare and have failed to find 3rd party repo's that have it. 

It would just save a lot of wasted time if i knew what my system was going to fail on except go through then entire ./configure process over and over and over and over.

Sometimes it's just easier to download the source and compile it myself. Why should I want to rely on 3rd party builds for applications not in the official repo's all the time? It's not like I can even verify if they have put code in there that might be hamful or intrusive to my system. I don't want to have to wait days or weeks for someone else to be bothered to compile updates that aren't in the ubuntu repo's either.

Your initial reply was enough - to go through the documentation and just look for the dependencies it *might* cite in the manual.

Cheers anyway.

---

