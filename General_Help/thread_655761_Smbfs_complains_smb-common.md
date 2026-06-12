---
title: "Smbfs complains smb-common"
date: 2008-01-01
forum: General Help
---

### Post by rbt123 on 2008-01-01
Hi, i'm using ubuntu desktop 6.06 dapper.

I'm trying to install smbfs, but it keeps complaining that smb-common is missing. 
But i checked smb-common is indeed installed. In fact, my Smbclient is working, and i could already successfully connect samba with Winxp Pro and perform file sharing. 

Please advise. Thanks!

---

### Post by HermanAB on 2008-01-01
Smbfs is deprecated.  Use cifs instead.

See the Samba web site Official Howto for details.

Cheers,

Herman

---

### Post by rbt123 on 2008-01-02
Thanks for the reply.

I don't quite catch what your saying. 

My understanding is the [COLOR="Blue"]smbfs[/COLOR] **package** supports smb and cifs. I've browsed samba.org but can't seem to find a [COLOR="Blue"]cifs[/COLOR] package you mentioned. 

There's an update to problem i faced: I tried "sudo apt-get install smbfs", and i get the following. 
samba: Depends: samba-common (= 3.0.22-1ubuntu3) but 3.0.22-1ubuntu3.1 is to be installed

It seems the smbfs package requires samba-common 3.0.22-1ubuntu**3**, but the version of samba-common installed on my system is 3.0.22-1ubuntu**3.1** (it comes with the ubuntu 6.06 dapper LTS distribution iso). That's why when i tried to install smbfs with synaptic package manager, it complains samba-common is not installed. 

Other people seem to have the [same problem]("https://answers.launchpad.net/ubuntu/+question/1946") as well when installing samba related packages. Unfortunately i cant find a solution on google. 

Please help. Thanks!

---

### Post by rbt123 on 2008-01-04
Hello?

---

