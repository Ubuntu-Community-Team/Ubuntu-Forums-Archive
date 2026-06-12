---
title: "gnome-obex-send cannot scan in edgy"
date: 2006-12-14
forum: General Help
---

### Post by djembe330 on 2006-12-14
I am having some bluetooth problems in edgy that were not problems in dapper.

When I use the nautilus-sendto program and choose obex, there are no options under "send to".  When I type gnome-obex-send <file-name> into a terminal the scan dialog pops up but nothing is found after pressing refresh and waiting for 5 minutes.

Command line options seem to work though:

"hcitools inq" and "hcitools scan" both work.  Then if I use the address of the device with:
```
gnome-obex-send -d <address> <file-name>
```
the file will send just fine.  This is ok for now, but in dapper I could just use gnome-obex-send to find the device and send, without any command line interaction.  This wouldn't be an issue if the nautilus-sendto worked, but I am guessing that the problems are related.  Anyone have this bluetooth stuff working *smoothly* in edgy?

---

### Post by zerohalo on 2006-12-22
I'm experiencing the same problem since upgrading to Edgy. Anyone have any solutions, or is this a bug?

---

### Post by elektronaut on 2007-01-06
[It's a bug.](https://launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/70718)

---

