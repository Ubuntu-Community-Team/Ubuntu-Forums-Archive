---
title: "Accidentally lost my sudo privileges. [Resolved]"
date: 2007-02-24
forum: General Help
---

### Post by JohnSilver on 2007-02-24
As the subject says, I accidentally lost my sudo privileges... I think. I installed virtualbox and after briefly reading some of the user manual I noticed that to run virtual box I need to be part of the group vboxusers, so I executed the following statement

[INDENT]sudo usermod -G vboxusers john.[/INDENT]

After rebooting a little later I noticed that I had no audio. Not nowing why, I ran

[INDENT]sudo modprobe snd-via82xx,[/INDENT]

and got the following output

[INDENT]Sorry, user john is not allowed to execute '/sbin/modprobe snd-via82xx' as root on ubuntu-desktop.[/INDENT]

Does anybody have any ideas on how can I get my sudo privileges back?

---

### Post by aysiu on 2007-02-24
> **JohnSilver said:**
> 
Does anybody have any ideas on how can I get my sudo privileges back? Try this:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by JohnSilver on 2007-02-24
Thanks for the link, everything is back to normal now.

---

### Post by aysiu on 2007-02-24
Great.

In the future, instead of using *usermod*, try using *adduser*: ```
sudo adduser john vboxusers
```

---

### Post by _asc_ on 2007-03-04
Hello!

I have the same problem. Thank's to the link aysiu posted, I have the sudo privileges back, but my sound still does not work. When I click on the volume control I get the following error message:

> 
No volume control GStreamer plugins and/or devices found.


Can anybody help?

---

### Post by aysiu on 2007-03-04
> **_asc_ said:**
> Hello!

I have the same problem. Thank's to the link aysiu posted, I have the sudo privileges back, but my sound still does not work. When I click on the volume control I get the following error message:



Can anybody help?
So your problem gets the attention it deserves, I've moved it to [its own thread](http://ubuntuforums.org/showthread.php?t=376173).

---

