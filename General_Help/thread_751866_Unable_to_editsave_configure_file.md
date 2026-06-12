---
title: "Unable to edit/save configure file"
date: 2008-04-11
forum: General Help
---

### Post by Old Marcus on 2008-04-11
I recently had internet problems and solved them by following this:
[http://www.cyberciti.biz/faq/how-can-i-setup-the-mtu-for-my-network-interface/](http://www.cyberciti.biz/faq/how-can-i-setup-the-mtu-for-my-network-interface/)
I changed my mtu settings. Now, it says to make this permanent you need to edit the configure file in /etc/network/.

I can open it, but there isn't hardly anything of what it says there is in there, just the first two lines. I add "mtu 1492" and go to save. I don't have the permission to. I made sure I had admin capabilities, and also tried to open it via su in the terminal. but to no avail.

It seems that no matter what I don't have any permission to edit this file, any help?

---

### Post by FuturePilot on 2008-04-11
You need to have root privileges to edit the file. You can do this by launching the editor with sudo or if it's a graphical editor use gksudo.
So to edit that file try
```
gksudo gedit /etc/network/interfaces
```

---

### Post by Old Marcus on 2008-04-11
Ok, but it seems strange that it didn't work under 'su', which I believe is the root account.

Thanks, that worked. :)

---

### Post by Old Marcus on 2008-04-11
Hmm, I did what that tutorial said and it hasn't kept the change permanent. Am I missing something here? I followed the Debian instructions since that the closest to ubuntu. Is there another way to do this? I just don't want to have to keep resetting it every time I restart my computer.

---

