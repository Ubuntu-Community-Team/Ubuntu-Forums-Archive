---
title: "vnc hostname"
date: 2008-03-29
forum: General Help
---

### Post by closeyourwindows on 2008-03-29
Hey all, I have a simple problem.  I am using 7.10 as a photo and file server for a school.  I have a hostname associated with this and shares so that anyone in the school can access this.  my issue is that I want to be able to remote into this from within the network. I can ping the hostname and get an ipaddress, but when I use vnc on a windows machine, I have to vnc using ipaddress, I would like to be able to use hostname instead.  I have installed bind, I am on the same workgroup, and I can even access the shares by hostname, but vnc is not working, except by ip address.  I am using tight VNC 1.39.

---

### Post by pointone on 2008-03-29
On the Windows machine, run:

```
notepad %SystemRoot%\system32\drivers\etc\hosts
```

And add the IP/hostname to the table.

For a network-wide change, this will need to be done on the router/DNS server.

---

### Post by closeyourwindows on 2008-03-29
good advice.  Thanks.  I did that on one machine and it worked.  I will try to do that on the router but not exactly sure how that will work..
Thanks.

---

