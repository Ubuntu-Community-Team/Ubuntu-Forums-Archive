---
title: "Ctrl+Alt+F1"
date: 2015-02-13
forum: General Help
---

### Post by Johnny3 on 2015-02-13
Ctrl+Alt+F1 (tried other F keys too) at log on doesn't seem to work any more. I got it to work once or so but when I did after I would put my name and pass word I would sudo service lightdm stop and then everything I typed in would also go in a long box that looked kind of like where you put you pass word for a normal log in so it wouldn't work. Something about use a untrusted ppa to install NVIDIA drivers just bothers me. Hope 14.04.2 has them supported.
Thanks Johnny

---

### Post by ian-weisser on 2015-02-14
If this is reproducible, you should file a bug report.
Developers won't know about the problem if you don't tell them.
They don't read these forum posts.

EDIT: When you stop lightdm, the service automatically restarts and switches the display to tty7. The login screen should reappear, since that's what lightdm does when it starts/restarts.
If the login screen appears strange, then your new video drivers may be the cause.
If the system freezes up and accepts no input, then your new video drivers may have crashed the system.
If the system still accepts input, but won't switch to a console (CTRL+ALT+<F1-F6>), that would be a bug.

---

### Post by Johnny3 on 2015-02-15
I was just want to known if anyone else was having the problem too. I just put in a new geforce gtx 970 and 14.04.2 is just about to come out then mite file a report.
Thanks Johnny333 68 ++

---

### Post by grahammechanical on 2015-02-15
I am not really clear about what you want to do. Why are you stopping Lightdm? It is a display manager. LightDM = Light Display Manager. It is what is used to present the login screen. If we stop LightDM we also need to start another display manager, such as GDM = Gnome Display manager. It is my guess that you are seeing a text (non-GUI) utility that appears when we run stop lightdm. It gives us the opportuity to start another DM and make it the default.

I am not convinced that you are seeing a bug. Have you used a PPA to install an Nvidia driver?

Regards

EDIT: Perhaps you are trying to install a Nvidia driver from a PPA. In which case we would indeed need to stop LightDM, install the Nvidia Driver and then start LightDM.

---

