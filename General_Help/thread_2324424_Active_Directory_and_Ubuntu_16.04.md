---
title: "Active Directory and Ubuntu 16.04"
date: 2016-05-13
forum: General Help
---

### Post by Joe_Miller on 2016-05-13
Hello all,

Joining Linux to AD has always been a pain but I thought after 14.04 it would be significantly less painful with things like realmd being available.  I'm starting to test 16.04 and my process for joining 14.04 doesn't work... not really surprising but after trying a bunch of stuff I am stuck.  I'm using more or less the process detailed here: [http://www.unixmen.com/how-to-join-an-ubuntu-desktop-into-an-active-directory-domain/](http://www.unixmen.com/how-to-join-an-ubuntu-desktop-into-an-active-directory-domain/)

This is what happens when I try to realm join:
```

cooladmin@box:/home/cooladmin# sudo realm --verbose join -U admin DOMAIN.COM * Resolving: _ldap._tcp.domain.com
* Performing LDAP DSE lookup on: 10.1.4.18
* Performing LDAP DSE lookup on: 192.168.11.227
* Performing LDAP DSE lookup on: 192.168.11.221
* Successfully discovered: domain.com
Password for admin: 
* Unconditionally checking packages
* Resolving required packages

```

It just hangs there forever without any errors in the logs.
[SIZE=2]
A few things to note and known issues I've tried troubleshooting:
- I'm not generating a krb5.keytab file for some reason.  I thought "kinit" did this. My krb5.conf is correct and so is my sssd.conf
- I removed the[COLOR=#333333] line "samba-common-bin = /usr/bin/net" from /usr/lib/realmd/realmd-distro.conf - this didn't change my result[/COLOR]
[COLOR=#333333]- I removed the "fully-qualified-domain..." line from sssd.conf - didn't change result
[/COLOR]- I removed the 'automatic-update...' line from realmd conf - didn't change result
[/SIZE]
Help!

---

### Post by craig56 on 2016-05-16
I think I was having the same problem. I remember finding an obscure forum or bug report saying to update to the latest version of packagekit. I wish I could remember where I saw it so I could give you the link. 

Anyways, for me the fix was to run: 

```

sudo add-apt-repository ppa:xtrusia/packagekit-fix
sudo apt-get update
sudo apt-get install packagekit

```

Hope this works for you.

---

### Post by Joe_Miller on 2016-05-16
Hey Craig,

Thanks a lot for this, it seems to have resolved the problem I was having.... however I have another issue now :)  I think I can work through this one, Thanks again!

---

