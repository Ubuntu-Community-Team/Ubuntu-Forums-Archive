---
title: "No firestarter"
date: 2013-11-01
forum: General Help
---

### Post by mcsheffrey on 2013-11-01
I just upgraded to 13.10 from version 10, now my firestarter is gone, can't find it in software center. What's the equivalent in 13. I did find it in /etc and was able to start it, the process is running, but how do I monitor it. Appreciate any help with this. Tks

---

### Post by deadflowr on 2013-11-01
About time, as firestarter hadn't had a maintainer for a while.
It's hard to tell what the closest would be, but [gufw]("https://help.ubuntu.com/community/Gufw") is okay.
I run the installed but not enabled [ufw]("https://help.ubuntu.com/community/UFW") myself, and others go further and play with [iptables]("https://help.ubuntu.com/community/IptablesHowTo?action=show&redirect=Iptables").

[More]("https://help.ubuntu.com/community/Firewall"), maybe.

---

### Post by Mopar1973Man on 2013-11-01
I also would suggest gufw as well. 
[https://help.ubuntu.com/community/Gufw](https://help.ubuntu.com/community/Gufw)

---

### Post by claracc on 2013-11-02
Firestarter is old software which hasn't  received any attention (updates) since long time ago.

I use ufw firewall and its gui gufw, they both rock.

---

### Post by mcsheffrey on 2013-11-02
Thanks for the feedback, installed gufw, looks pretty good, now I have one more question, how can you set it up to start automatically on bootup, because it's too easy to forget to start it after a re-start.  Tks Roy

---

### Post by Frogs Hair on 2013-11-02
UFW  is enabled at boot. If you use the the gui select on and your good to go.

---

### Post by sammiev on 2013-11-02
> **mcsheffrey said:**
> Thanks for the feedback, installed gufw, looks pretty good, now I have one more question, how can you set it up to start automatically on bootup, because it's too easy to forget to start it after a re-start.  Tks Roy

Once turned on it's always on.

---

### Post by mcsheffrey on 2013-11-02
Ok, but after my last boot I did  "ps-ef|grep gufw" and it didn't show up until I double clicked on the icon. Maybe  I didn't wait long enough. Tks again

---

### Post by claracc on 2013-11-03
To see if the firewall is running you have to run in a xterm:

```
ps -ef | grep ufw
```

ufw is the firewall, gufw is only the gui to set ufw.

---

