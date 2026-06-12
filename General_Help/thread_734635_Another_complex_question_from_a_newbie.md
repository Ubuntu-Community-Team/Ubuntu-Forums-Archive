---
title: "Another complex question from a newbie"
date: 2008-03-24
forum: General Help
---

### Post by power_speed on 2008-03-24
I had a previously installed mandriva.  I decided to try Ubuntu.  However,  Ubuntu will not let me have access to the information stored on the partitions created by mandriva.  It says i do not have permissions necessary.  Is there a complete way to disable permissions.  As I am the only one who ever uses this machine I don't need that much security?  If not is there at least a way I can get my information copied over.  This problem is starting to get to me.  Please help!!
Thankyou,
RE

---

### Post by aysiu on 2008-03-24
Try Alt-F2 ```
gksudo nautilus
``` If someone tells you to *chown* or *chmod* the Mandriva partitions, don't do it.

---

### Post by AdamWill on 2008-03-25
It's important to know that on Linux your username is just an abstraction. Think of it as a URL, like [www.google.com](www.google.com) . That's not *really* Google's location, it's just a way to find it. The real location is an IP address - a number.

In the same way, your username on a Linux system is just a reference to the real identity, which is numerical. Your files aren't *really* owned by 'powerspeed' or 'bob' or 'adamw' or whatever your username is, they're owned by User 501, or User 1001, or something. So even if you create a user on one distro and then create a user on another distro and give it the same user name, that doesn't mean you'll have access to the files, because the user ID (UID) could still be different. This is likely what you're running into here (IIRC, Mandriva numbers its user accounts starting at 500, but Ubuntu numbers them starting at 1000).

What aysiu suggests is basically to copy the files as root - running 'gksudo nautilus' runs Nautilus as root. Then you'll have absolute access to copy anything from anywhere to anywhere. What I'd recommend is to use Nautilus to copy what you want from Mandriva to your Ubuntu partition, and *then* use 'chown' *on the copied files*, not the originals, to change them to being owned by your Ubuntu user.

---

