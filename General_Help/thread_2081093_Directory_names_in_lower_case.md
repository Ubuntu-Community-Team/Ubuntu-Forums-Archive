---
title: "Directory names in lower case"
date: 2012-11-05
forum: General Help
---

### Post by Alan.Brown on 2012-11-05
When I try to create a directory with a name in upper case - eg **HP** - it always reverts to lower case - **hp**.   This happens in Thunar, Dolphin, Krusader and in the Command Line.

So **ACER** becomes **acer** but **ACER-Linux** remains as I typed it.

This seems to be quite recent since some directories I have created months or years ago are OK.

Why is this happening and can I correct it?   Is it a setting somewhere?

It is the small things that annoy us!!  :confused:

TIA

Alan

---

### Post by 2F4U on 2012-11-06
Just tried a simple mkdir TEST on my (pretty much stock) Xubuntu 12.10 install in a terminal, but it created the folder exactly as specified in uppercase. Tried the same with Thunar and again it created the folder as specified in uppercase.

---

### Post by Alan.Brown on 2012-11-06
Thanks for your reply.  This is how it always used to for me too.   I have obviously set a setting incorrectly somewhere - But I cannot find what I have done.

I will keep trying

Thanks

---

### Post by jerome1232 on 2012-11-06
My only thought, and this is a shot in the dark, but is this only happening on a certain filesystem, a Microsoft one perhaps?

---

### Post by Alan.Brown on 2012-11-06
YES!!  Thats correct.   I have a wireless router that has a network drive connected to it that is shared across my network.   This drive in formatted to **ntfs** because the router requires this and because one computer on the network runs Windows.

All other drives on the system are formatted to **ext4** and I have no trouble with them.   

That explains the problem - thank you.

---

