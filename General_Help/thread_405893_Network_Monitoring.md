---
title: "Network Monitoring"
date: 2007-04-10
forum: General Help
---

### Post by Kizilbas on 2007-04-10
There is a default Network Monitoring application that came with Xubuntu Linux 6.0.6 Dapper.

Where would I obtain and install a more specific and advanced/better Network Monitoring program?

I need to see all the connections. Does Linux have commands similar to the function(s) of the command netstat in Windows?

---

### Post by rufius on 2007-04-10
> **Kizilbas said:**
> I need to see all the connections. Does Linux have commands similar to the function(s) of the command netstat in Windows?

In fact netstat was created on a *nix system, BSD 4.2 that is. Windows ported it to their platform. Netstat exists but if you'd like a nicer way to monitor your connections, then you'll want to install "iftop". Its a command line tool and is very nice. You'll have to use it as root, but thats not really an issue, the basic command to open is as follows:

```
sudo apt-get install iftop
```

then to run it:
```
sudo iftop -i <interface> -P
```

The -P switch will show ports as well.

---

### Post by Kizilbas on 2007-04-10
Yes rufius thanks for this, its a good tool :)

---

### Post by Kizilbas on 2007-04-10
Oh and now can I put a shortcut of the Terminal on my desktop?

---

### Post by rufius on 2007-04-10
Well I see you're using Xubuntu. For that I have no idea, but you'll want to make sure it runs iftop in a terminal. For Gnome you would right click your desktop and click 'create launcher'.

---

### Post by Kizilbas on 2007-04-10
aah yes its the same in Xubuntu aswell. Right-Click on desktop & create launcher, then selecting the terminal from the list.

Thanks for all your time rufius,
time is precious :)

---

### Post by Bartolomeo on 2008-01-16
**Kizilbas** **rufius**
thank for your posts. They are very useful for me

---

