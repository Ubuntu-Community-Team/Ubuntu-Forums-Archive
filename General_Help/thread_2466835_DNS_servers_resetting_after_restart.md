---
title: "DNS servers resetting after restart"
date: 2021-09-07
forum: General Help
---

### Post by empleat on 2021-09-07
I Am on last Ubunutu/Desktop.  Using this command on admin account:  ```
sudo nano /etc/resolv.conf
``` I change DNS servers, then open resolv.conf again to double check. And DNS servers are saved! Then after restart, all saved settings from resolv.conf are deleted!!!  Any ideas why? Thanks!

---

### Post by rsteinmetz70112 on 2021-09-07
Why it works like this I don't have a clue, but recent versions of Ubuntu are designed to rewrite the /etc/resolv.conf file at every reboot.
Depending on how your system is set up there are different methods for accomplishing this.

Here is a discussion of various techniques to accomplish that.

[https://askubuntu.com/questions/130452/how-do-i-add-a-dns-server-via-resolv-conf](https://askubuntu.com/questions/130452/how-do-i-add-a-dns-server-via-resolv-conf)

The easiest seems to use the GUI tool to add the DNS servers.

Goog luck.

---

### Post by &amp;KyT$0P# on 2021-09-07
I assume you have a good reason to be directly editing [FONT=Courier New]/etc/resolv.conf[/FONT] instead of the normal way to change DNS settings on a current Ubuntu desktop.

Please post output from running this command in Terminal -
```
realpath /etc/resolv.conf
```

What does [FONT=Courier New]/etc/resolv.conf[/FONT] reset to?  Next time you perform a reboot and it resets, please post the contents of the reset [FONT=Courier New]/etc/resolv.conf[/FONT] file.

What are you using for networking?  e.g. NetworkManager, wicd, netplan, [FONT=Courier New]/etc/network/interfaces[/FONT], ...?

---

