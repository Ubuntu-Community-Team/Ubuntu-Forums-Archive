---
title: "Making an Image of XP"
date: 2008-01-16
forum: General Help
---

### Post by Xswitch on 2008-01-16
I have a PC running Windows XP.  I would like to create a "ghost" image of the PC using linux.  Can someone step me through the process?  Thanks.

---

### Post by mathisdermaler on 2008-01-16
The basic process:
1) boot off of a live CD
2) copy the entire hard drive somewhere else by reading from /dev/sda or whatever drive you want to make an image of.  You could either copy it to another hard drive in the same computer or you could copy it over the network.  

Whether this is a good idea is questionable, as you may not be able to use this image on any other hardware (or else windows will need to be reactivated) and I am not sure what will happen if you try to use the image on a hard drive that is not exactly the same size as the drive that you made the image from.

What are you trying to do with it?

---

### Post by dcstar on 2008-01-17
> **Xswitch said:**
> I have a PC running Windows XP.  I would like to create a "ghost" image of the PC using linux.  Can someone step me through the process?  Thanks.

Install the **partimage** package, and use it (in a terminal):
```
partimage
```

---

