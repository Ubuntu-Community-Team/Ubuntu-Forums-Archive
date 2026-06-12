---
title: "nfs client problem"
date: 2008-01-05
forum: General Help
---

### Post by thick0 on 2008-01-05
Hi, I have several linux boxes. The desktops run fedora and the laptops run ubuntu fiesty. I set up an nfs server on one of my desktops. I can access files from the other desktops.

When I try to access the nfs share from my laptop:


[INDENT]sudo mount 192.168.1.104:/home /mnt/home [/INDENT]

this works but takes about 1 minute. The desktops are directly connected to the router, the laptop is connected wirelessely.
[INDENT]
ls /mnt/home and I can see my user name directory (tim) but

ls /mnt/home/tim[/INDENT]

returns "Permission denied". Now I guess the server is rejecting this request. All IP addresses are defined the same at the server end. Any ideas why I can see the share but not the contents?

---

### Post by HermanAB on 2008-01-05
Ensure that your UID is the same on all machines.

Cheers,

Herman

---

### Post by thick0 on 2008-01-05
Hi Herman,

that seems to be the problem. Thanks

---

