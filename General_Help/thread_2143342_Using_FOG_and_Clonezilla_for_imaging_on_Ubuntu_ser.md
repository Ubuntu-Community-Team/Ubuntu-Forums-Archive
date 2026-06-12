---
title: "Using FOG and Clonezilla for imaging on Ubuntu server"
date: 2013-05-08
forum: General Help
---

### Post by amelnyk1 on 2013-05-08
Hi, I'm currently working for a school division where the mainstay of imaging has been done with FOG for the last few years. However It doesn't work with the new computers that are coming out with uefi. Since they are migrating to mostly windows 7 computers they need to find a new way of doing this since FOG fails to image them and there has been no active development in the last two years. We have started trying to use clonezilla on an Ubuntu server now which seems to solve this issue, however it doesn't do the remaining parts of the work that FOG was doing, namely some post image processing (changing the hostname, joining the work station to the domain or active directory). Our idea then was to use both somehow. To have clonezilla do that actual imaging and to have FOG do all the post imaging tasks. Digging around on the internet I came up with a few solutions, one of which was using the live CD in clonezilla, however I thought that this would probably require going to every workstation and starting clonezilla manually (this may turn out to be the best option however it is unfavourable). Now the idea is to somehow get the machines to PXE boot into clonezilla, and then have FOG do the rest, putting both on the same server. For now I'll be doing some experimenting with this to see if I can get it to work. But from what I've gathered from my internet travels it doesn't seem like anything anyone has tried.

---

