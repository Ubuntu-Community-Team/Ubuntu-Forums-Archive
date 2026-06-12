---
title: "Segmentation fault (core dumped)"
date: 2007-05-03
forum: General Help
---

### Post by PartisanEntity on 2007-05-03
I got this error yesterday for the first time while trying to launch Kompozer.

Today I installed Seamonkey, and upon trying to launch it I got that same error.

I have this bad feeling that it could be something in the system and not in these applications?

What can I check to make sure? Where do I need to look? What do I need to do?

OS info: This is a Feisty installation which was upgraded from Edgy. Hardware is an Asus laptop.

---

### Post by aiwarrior on 2007-05-07
i have the exact same problem. It started with the change from ubuntu to kubuntu.
The weirdest thing is its all right when i reboot/re-log but a few minutes later when i try to re-run the same apps i get all segmentation faults.

---

### Post by PartisanEntity on 2007-05-07
Strangely once my problem showed up, not even a reboot or a renewed log-in helped. I removed Kompozer and installed the old Nvu which is working fine. I hope this won't happen again.

Hopefully some experienced members can help us to find out why this happened in the first place.

---

### Post by aiwarrior on 2007-05-07
Well i dont even got that kompozer installed, but i got more info on the issue.

1st It's not an application issue, its from the kde environment, still trying to really know whats making this error fire.

2nd It doesnt happen in the gnome environment so again it's not an application issue. I think its possibly a bug

---

### Post by PartisanEntity on 2007-05-07
I don't use the kde environment. I am having this error in Gnome.

---

### Post by aiwarrior on 2007-05-07
oh well then im lost again, we should wait for some poster more skilled than us. I have already seen some posts similar to our but none seems to get resolved.

---

### Post by public_void on 2007-05-07
A segmentation fault is caused by the program trying to access an area of memory it shouldn't. However, because two programs have done and on different environments, it suggests that a shared library maybe be at fault.

Try
```
tail /var/log/messages
```to see if there is anything relating to this.

---

### Post by PartisanEntity on 2007-05-08
Hi, thanks for the input.

I tried tail /var/log/messages but the output was all about my wireless card and none of it seemed to be an error message.

Where else could one look? Is Launchpad a good place to mention this and see if others are experiencing the same behavior with certain applications?

---

### Post by aiwarrior on 2007-05-08
Mine too, but it was my nforce audio drivers. I still searched and greped the outpud but no mention that i was aware of. My problem went away when e deleted all gnome and kde packages, and made a minimal ubuntu. Then i switched to Xfce and all is running fine.

---

### Post by cleggton on 2007-05-11
Chaps,

I have a similar problem, This seems to happen in a whole host of apps - Firefox, thunderbird, hardware manger?.  I use Gnome as my WM but also have the KDE libs installed so i can use Amarok and Kaffeine.  

This has happened since I have upgraded to feisty, but also I have moved from the NVidia to NVidia_new binary drivers, could this be at fault?

Im', not sure that I confirm it as a Gnome/KDE problem.

Reboots do not help at all.

There seems to be quite a lot of seg faults kicking around at the moment i think we could do with understanding what our common features are.

---

### Post by cleggton on 2007-05-11
Actually I have just installed the VMware-server kernel modules also.

---

