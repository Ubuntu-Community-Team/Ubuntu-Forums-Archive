---
title: "Samba share; wrong names are shown."
date: 2008-06-05
forum: General Help
---

### Post by _sAm_ on 2008-06-05
Hi

I have a strange problem with samba shares with latest Ubuntu. One of the shares has lot of folders(all with music), and some of the folders are showing up with strange names. 

Example; Folder with the name «Elton John» is showing up as «EDONNL~W», the folder «Marlango» are showing up as «MZ9HT~Q», &#8220;Van Morrison&#8221; is turning up as  &#8220;VDWH39~H&#8221; and so on. Most of the folders are ok. 

This is true both in Nautilus via network and on Vista. There is no problem when I look at the same share on my Desktop using NFS. 

Any suggestions?

Edit; I have turned off and on samba, and also reboot.

---

### Post by _sAm_ on 2008-06-07
bump

---

### Post by _sAm_ on 2009-03-30
I did find the reason for this;

Every folder with a space in the name at the end, will end up with a new strange name when shared via samba. 

If I transferee a folder with a space in the end to a WHS, the adm will not be able to open, rename or delete that folder(?). But I can delete it from Ubuntu(using cifs). 

I often rename folders with F2 then type the new name. It looks like I get a space at the end on some off them - and you cant tell when just looking at the names.

I guess this is a windows problem.

---

