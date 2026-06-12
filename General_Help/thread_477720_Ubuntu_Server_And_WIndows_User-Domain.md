---
title: "Ubuntu Server And WIndows User-Domain"
date: 2007-06-18
forum: General Help
---

### Post by tolley1466 on 2007-06-18
hi,

i was wondering if i can use Ubuntu Server and use it for a user domain for windows computers?

Cheers,

---

### Post by nymphaeles on 2007-06-18
Try Samba 3.x.  It can act as a domain controller in a windows network.

---

### Post by tolley1466 on 2007-06-18
wow! their site is very hard to navigate, got a link to the download?

---

### Post by nymphaeles on 2007-06-18
From your Ubuntu machine, go to System, Administration, Synaptic Package Management.  Samba is in the list, you just need to check a box.

---

### Post by tolley1466 on 2007-06-18
> **nymphaeles said:**
> From your Ubuntu machine, go to System, Administration, Synaptic Package Management.  Samba is in the list, you just need to check a box.
so i need to install ubuntu server?

sorry im a newbie to linux

---

### Post by dustigroove on 2007-06-18
[FONT=Arial][SIZE=2][COLOR=Black]Samba is in the software repositories. Go to the **Applications** menu, then [/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Black]**Accessories** submenu, then [/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Black]select **Terminal**.

Enter the following within the terminal window:
```
sudo apt-get install samba
```Alternately, follow nymphaeles' previously mentioned steps to install via the Synaptic package manager. Also, being new to Linux I would suggest that you search through the forums and Google for advice on what you are looking to accomplish, and post any questions you have along the way.


Cheers

[/COLOR][/SIZE][/FONT]

---

### Post by tolley1466 on 2007-06-19
yea but to get onto that menu do i need to install ubuntu server?!

---

### Post by Sunforge on 2007-06-19
As far as I know Ubuntu server is a subset of the normal Ubuntu desktop install, the major difference bewteen server and desktop being the graphical interface and the desktop applications.

If you want to install Samba on a normal desktop there's nothing stopping you if all you want to do is experiment with it.

If you intend to run this in a production environment it's better to run the server variant as there's less clutter from applications etc.

---

