---
title: "Stuck in Boot Process: A Lesson Learned"
date: 2007-03-12
forum: General Help
---

### Post by dasunst3r on 2007-03-12
For those of you who are getting stuck halfway through the boot process, you might want to read this.  It took me several reinstallations to figure the problem out.  As you know, Edgy can be a little bit behind other distros with respect to networking.  

When you are stuck, what the OS is doing is waiting for an IP address to all the interfaces listed in /etc/interfaces.  Some might not even exist (!).  Here's how you rectify the problem:

[list=1]
[*]Press Ctrl+Alt+F1, then Ctrl+Alt+F8.  You should see some text about fsck being done.
[*]Press Ctrl+Alt+Delete **(not kidding)** to force Ubuntu to proceed with booting
[*]Install *network-manager-gnome* and its dependencies
[*]Modify /etc/network/interfaces to look like this:
```
auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp
```
In essence, comment out everything but the loopback interface (the first entry).
[*]Restart
[/list]

I hope this saves other folks from having to reformat.  It was lesson learned through the School of Hard Knocks.

---

