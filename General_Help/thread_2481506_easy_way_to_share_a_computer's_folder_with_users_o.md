---
title: "easy way to share a computer's folder with users on same wifi as computer ?"
date: 2022-12-01
forum: General Help
---

### Post by vincentm77 on 2022-12-01
Hi everyone,

I have a computer with Ubuntu connected to a wifi router (FritzBox). 
my users (who don't have access to the computer and are not Ubuntu user) can connect their apple/android smartphones to the router (they know the wifi password). 


I would like to be able to share the content of a folder (say, /home/vincent/Music ) with these users.

What is the easiest way to do this ?!

I guess I could install a cloud server (nextcloud/owncloud) on the computer, and ask my users to install the corresponding app on their smartphones... I guess this is cumbersome, since i would need to install an web server first to host the cloud server.
Or it is possible to create samba/cifs shares on the computer, which the users could access using their smartphones ?

Thanks !!!
Vincent

---

### Post by Morbius1 on 2022-12-01
This may only be a partial answer since I have no idea what android can do but the iPhone issue can be done with Samba.

I have created a samba share of my Public folder on Xubuntu 22.04 by adding a share definition to the end of /etc/samba/smb.conf:
```
[Pulbic]
path = /home/tester/Public
read only = no
guest ok = yes
force user = tester

```

The iPhone has a bult in file manager called **[COLOR="#0000CD"]Files[/COLOR]** and I can open that up and go to:
Browse > Connect to Server and enter the mDNS host name of my Xubuntu server:
```
xub2204.local
```
The Public folder can be opened and it's contents displayed.

There is no need to specify the protocol because iOS and MacOS both assume all network file transfers are Samba ( SMBx ) by default.

---

### Post by vincentm77 on 2022-12-01
Thanks Morbius, this sound quite interesting. I m pretty sure that Android can do this as well.
Best,
V

---

### Post by HermanAB on 2022-12-01
The easiest is probably via a small web server.  That way anyone can use web browser to access the files. Eg lighttpd.

---

