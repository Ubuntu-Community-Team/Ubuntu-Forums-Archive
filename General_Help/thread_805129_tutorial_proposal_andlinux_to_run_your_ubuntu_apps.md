---
title: "tutorial proposal: andlinux to run your ubuntu apps"
date: 2008-05-23
forum: General Help
---

### Post by Virtual DarKness on 2008-05-23
Today I've managed to install [andlinux]("http://andlinux.org") and configure it so that I achieved (all) these results:  

- run applications as a normal user
- mount my ubuntu root and home partitions
- dist upgraded ubuntu in andlinux to 8.04
- run applications (like thunderbird) using settings and data of my real ubuntu installation (so I can run thunderbird and firefox with the same data and configuration in both linux and windows)
- run applications that I've installed in my ubuntu install but not in the andlinux install from window with my settings / data like konqueror, gftp (so I don't have to install them again in andlinux's ubuntu) .. this last thing using schroot

The only problems are:
- sound does not longer works in andlinux (problems with permissions of pulseaudio with the normal user I guess)
- I was not able to run revelation both in andlinux and in andlinux from my ubuntu install using schroot (guess has something to do with the fact that it is written in python but I could be wrong)

so.. does someone would like to have a tutorial on how to do this? I'm asking cause I plan to write some notes for myself but writing a tutorial would require me lot more time. also would be nice if someone would like to help me writing it and of course if there are better methods (like using directly colinux) let me know. I've started with andlinux cause it already has lot of pre-configured things like the X server and so on.

btw.. I've used cofs instead of samba to share a folder with the windows install.

bye,
Giovanni.

p.s.
I know that being a "proposal" this post may not fit at 100% the topic of this section but anyway this post contains some tips and shows what can be done :)

---

### Post by K.Mandla on 2008-05-29
Moved to General Help.

---

