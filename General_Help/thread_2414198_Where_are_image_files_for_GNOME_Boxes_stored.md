---
title: "Where are image files for GNOME Boxes stored?"
date: 2019-03-07
forum: General Help
---

### Post by goodstuff9 on 2019-03-07
Ubuntu 18.04
Gnome Boxes 3.30.3

I have installed Linux Mint as a guest virtual machine in Gnome Boxes.  It works great.  

I can't figure out where the image file for that guest virtual machine is stored.  

I've looked at many other questions on this topic, they all turned out to be wrong in my case.  

/home/user/.local/share/gnome-boxes/images does not have it.  

/home/user/.config/libvirt does not have it.  

/home/user/.config/libvirt/qemu does not have it.  

/home/user/.config/gnome-boxes does not have it.  

/var/lib/libvirt/images does not have it.  


I don't know where else to look for it.  

Also, I don't know the "format" the name of the image file takes, so I don't know how to search for it using a tool like Catfish.  

And yet, since I can successfully run Linux Mint within Gnome Boxes, I know there must be an image file somewhere.  

How do I find where this file is located?

---

### Post by PaulW2U on 2019-03-07
I use GNOME Boxes and my images are at /home/$USER/.local/share/gnome-boxes/images but you said you looked there.

Try searching for large files in a terminal using
```
find ~ -size +1G -ls
```
to search /home or
```
find / -size +1G -ls
```
for a complete search.

---

### Post by goodstuff9 on 2019-03-08
> **PaulW2U said:**
> I use GNOME Boxes and my images are at /home/$USER/.local/share/gnome-boxes/images but you said you looked there.

Try searching for large files in a terminal using
```
find ~ -size +1G -ls
```
to search /home or
```
find / -size +1G -ls
```
for a complete search.


Yep, that worked!!!!  Thanks!!  

It was located in /home/user/.var/app/org.gnome.Boxes/data/gnome-boxes/images .  

I assume it was put into this odd location because I installed gnome boxes via Flathub.

---

