---
title: "[SOLVED] SageTV won't let me boot! (GNOME+KDE install)"
date: 2008-06-16
forum: General Help
---

### Post by RevolutionMaster on 2008-06-16
Ok, I installed SageTV from their site, thinking that I could use my Windows key. Well I cant, and when I try to boot, it asks for the activation key, and it WON'T continue booting until I enter my Linux SageTV server key! I can't abort it either! :(. Is there a way to A: skip the step, B: just exit the key asker, or C: edit it out of the boot process from Windows (With EXT3 support)?

---

### Post by prshah on 2008-06-16
> **RevolutionMaster said:**
> Ok, I installed SageTV from their site, thinking that I could use my Windows key. Well I cant, and when I try to boot, it asks for the activation key, and it WON'T continue booting until I enter my Linux SageTV server key! I can't abort it either! :(. Is there a way to A: skip the step, B: just exit the key asker, or C: edit it out of the boot process from Windows (With EXT3 support)?

Most easiest: The key asker seems to be a shell script; Ctrl+C will stop most scripts dead in their tracks.

Easiest: from windows, rename the "/opt/sagetv/server/startsage" and the "/opt/sagetv/server/keygen.sh" files.

From linux, 

a) Try switching to a virtual terminal with Ctrl+Alt+F1
--OR--
b) press Ctrl+Alt+SysRq+E to terminate all running programs and dump you to a prompt.

Now rename the above two files, or remove execute permissions on them. These files are autostarted, and you will have to find out how to stop this behavior (hint: maybe /etc/rc.local?)

CAVEAT: I don't have SageTV and will not be held responsible if your system blows up or otherwise goes wonky with these suggestions.

---

### Post by ats51 on 2008-06-18
i'm also having this problem, after installing sagetv it prompted me for an activation key. without one and unable to abort the installation i force crashed the application. now when i start up ubuntu stalls on the splash screen before requesting me again for the activation key. does anyone know a way around this because as it is i am unable to use my computer as it does not start up!!

---

### Post by ats51 on 2008-06-18
in response to my own problem i was able to solve it by starting in recovery mode (by pressing esc on the grub screen) then entering root terminal. i was then able to uninstall the problem program, for me this was sagetv server:

```
apt-get remove sagetv-server
```

this did the trick

---

### Post by lferree on 2008-07-05
that didn't work for me, here's what i did

recovery mode

login user that installed

```
cd opt

sudo rm -r sagetv
```

hope this keeps someone from having a heart-attack O.o

---

### Post by sickenmcsluggets on 2009-03-01
> **lferree said:**
> that didn't work for me, here's what i did

recovery mode

login user that installed

```
cd opt

sudo rm -r sagetv
```

hope this keeps someone from having a heart-attack O.o
Thanks a BUNCH! I did that, and was able to boot up without the entering the key. I then went to Synaptic Package Manager to completely uninstall, but it asked me to:

 ```
dpkg --configure -a

```
Which I did , and then was able to completely uninstall sagetv-server. 

I didn't look closely enough at the SageTv website, because, I was misunderstanding the free trial download. Apparently the free trial was only for Mac and Windows. So I got stuck with this key request ...FRUSTRATING, but fixed.

---

