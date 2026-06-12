---
title: "Fstab format"
date: 2005-09-18
forum: General Help
---

### Post by Robgould on 2005-09-18
Hello,

This is my first post on this forum, coming from Fedora.  I am running ubuntu on  a laptop, toshiba satellite P35, and it is running fine.  I have a wireless routher that I share my cable with.  My desktop funs winxp.  My network is working, but I want to mount my desktop as part of my file system,  If I make my desktop IP static I can do this with this line in fstab:

```
//Server/Share        /mount/point    smbfs    rw,username=XXX,password=XXX,uid=XXX,gid=XXX 0 0
``` 

In that code I would put my IP as the server.  My problem is that my provider uses DHCP.  Does anyone know how to format this first part of this with the rmote computer name and resolve tne IP each time?  Thanks for your help.

---

