---
title: "sudo: /etc/sudoers is mode 0640, should be 0440"
date: 2007-04-28
forum: General Help
---

### Post by phatty420 on 2007-04-28
Im pretty new to linux but experienced pc user,  i was trying to edit my "sudoers" file to automatically start "firestarter" at login.  this is the code i used in the terminal: ```
gksudo gedit sudoers 
```and this is the terminal says "sudo: /etc/sudoers is mode 0640, should be 0440" and now anything i "sudo" says that!!! im hoping theres a way to change it back without rebooting! is there some safe mode i could use(hopefully w/o reboot)?   thank you in advance for anyone that helps!:confused:

---

### Post by spone on 2007-04-28
try:

```

su -
chmod 0440 /etc/sudoers
exit

```

:)

---

### Post by perje on 2007-12-24
Hey,

 I had the same problem, then I've found the answer on Conrad's world:

[http://64.233.183.104/search?q=cache:qYH_-YPGU9QJ:conrad.instantspot.com/blog/index.cfm/2007/7/3/How-to-fix-your-etcsudoers-permissions+sudoer+is+in+mode+0640&hl=en&ct=clnk&cd=4&client=opera](http://64.233.183.104/search?q=cache:qYH_-YPGU9QJ:conrad.instantspot.com/blog/index.cfm/2007/7/3/How-to-fix-your-etcsudoers-permissions+sudoer+is+in+mode+0640&hl=en&ct=clnk&cd=4&client=opera)

"The Fix: 

After some more pain and searching for how to fix it, I find that I can just go into **recovery mode** from the GRUB menu and then **chmod 0440 /etc/sudoers and reboot**. So once again I avoid a reinstall of Ubuntu"

It worked for me...

Godd luck

---

