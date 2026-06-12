---
title: "I can't shoutdown my ubuntu automatically by qshutdown app."
date: 2013-01-29
forum: General Help
---

### Post by sinaphysics on 2013-01-29
Hello,

Recently, qshutdown doesn't work for me. When I schedule for a specific time to shutdown, it fail. In setting part, it was on "automatic method", I am using now ubuntu 12.10 Gnome desktop, so I changed it to "Gnome session". But there is same problem too. what do u suggest ?

---

### Post by hakaishi on 2013-02-24
Hi sinaphysics,

please try the option "ConsoleKit". If it still doesn't work, please tell me and add the output of qshutdown. You can get the output if you enter "qshutdown -v" in the terminal. The output will appear as soon as qshutdown tries to shutdown the system.
It is possible that one of the "Gnome" methods interrupts qshutdown trying all the methods in the option for "automatic". Btw: What version of qshutdown are you using?

All of this is because Gnome is messing around with their dbus-Interfaces... It should be working fine when using Unity. :-/

I just now registered here because I saw your question while searching for comments on qshutdown (actually, I'm the developer of qshutdown). ;)

---

### Post by zero2xiii on 2013-02-24
One word: Permissions.

Try running through sudo.. **warming this might be dangerous and all that warning stuff here.. I wont post HOW**

You get a similar issue when you try in terminal:
```
shutdown now
shutdown +1
shutdown 20:00
```

It gives you the error that you must be root to shutdown the system. So try running the tool from sudo.. 

Dev.. You referred to the dbus? Intresting method of programing such a tool.. :)

Good luck

---

### Post by hakaishi on 2013-02-24
qshutdown should work without problems without using any root privileges! This is why it exists... Well, you can also give qshutdown (according to the instructions) root privileges and set the shutdown method to "sudo shutdown -P" or do what ever you want using "user defined" (while this could be risky when it has root privileges...).

BUT: This was not the question of sinaphysics. Please refrain from unnecessary information (almost) every Linux user knows about. It'd be more helpful if we could get the Gnome developers to properly handle the dbus interfaces... Here a bug report from me on launchpad: [https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/931565](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/931565)
By the way: The method used in the dbus interface (mentioned in the bug report) was completely removed some time ago. :(
[]("https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/931565")

---

### Post by hakaishi on 2013-02-24
I forgot to mention that the normal shutdown using the (gnome) desktop environment also uses dbus. How else would any user be able to shutdown the system?

---

