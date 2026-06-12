---
title: "How do I get this change to stick?"
date: 2007-11-05
forum: General Help
---

### Post by Abishye on 2007-11-05
Greetings to all.  Easy question for you gurus here.

I'm running a command "v4l2-ctl -d /dev/video0 --set-input=2" to change the input of a tuner card to composite.  The command works perfect.  But every time I reboot I have to enter it again.  Is there a way to make this change permanent?  I'm running Ubuntu 7.10 64bit desktop.

Thanks much.

---

### Post by fazavon on 2007-11-05
You might be able to add it to the "session"

System > Preferences > Sessions

You can add custom commands that will run at startup, much like editing the msconfig in Winblows...(did i just say that? :))

Thanks

//j

Let me know if that works

---

### Post by notna01 on 2007-11-05
> **Abishye said:**
> Greetings to all.  Easy question for you gurus here.

I'm running a command "v4l2-ctl -d /dev/video0 --set-input=2" to change the input of a tuner card to composite.  The command works perfect.  But every time I reboot I have to enter it again.  Is there a way to make this change permanent?  I'm running Ubuntu 7.10 64bit desktop.

Thanks much.

make a launcher in the panel? Then you would just need to click it to turn on your tv card

---

### Post by Abishye on 2007-11-05
Hi there fazavon.  Thanks for the help, that did the trick.  I still have alot to learn.

Thanks again.

 =D>

---

### Post by fazavon on 2007-11-05
no problem, ask anytime, I will help as much as I can.

I have been using Ubuntu well all the back to 5.04, and I still learn something new everyday. :)

---

### Post by geirha on 2007-11-05
If you want it to be run at boot time, you can add it to /etc/rc.local ... then you probably don't need to think about it anymore.

---

