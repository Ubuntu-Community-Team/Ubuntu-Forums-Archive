---
title: "My Ubuntu is dead after update =("
date: 2006-10-16
forum: General Help
---

### Post by rubso on 2006-10-16
hey guys, my ubuntu is dead after updating some kernel images many things have turned to be broken especially the X Windows and when i editied my X.config file to use "nv" driver, i was shocked that my wifi "ath0" won't work neither !!
so i started X manually and tried to install the older packages, but synaptic won't work until i get an internet connection.
:( so, what should i do?

---

### Post by rubso on 2006-10-16
i rebooted to the older linux image and it works now, but i don't know what to do with the newer kernel?
Note: the new kernel is 2.6.15-27
i'm using 2.6.15-26 now .
any clue?!

---

### Post by dannyboy79 on 2006-10-16
is it possible that this could solve your update issue with x not starting?
[http://www.ubuntuforums.org/showthread.php?t=241254&highlight=x+broke+after+update](http://www.ubuntuforums.org/showthread.php?t=241254&highlight=x+broke+after+update)

---

### Post by rubso on 2006-10-16
my Xorg version is 
Version: 1:1.0.2-0ubuntu10.4
so i don't need to update it.. right?

---

### Post by crane on 2006-10-16
I had the problem as well with the newest update to the kernel. Repeated attempts to fix failed so I just uninstalled the new kernel. HAd to work on mythbox as well. I'm scared of updates now.

---

### Post by dannyboy79 on 2006-10-16
i don't know why you are asking this? of course you don't need to update xorg. that's not what the link suggests. it is saying that after a certain update, xorg.conf gets messed up and you need to perform certain things to get x to start again.

---

### Post by crane on 2006-10-16
Well, I guess you could ask yourself if you really need the new kernel. If it does not help or hinder you to do without just uninstalling or at least set grub to boot to the working kernel by default.

---

