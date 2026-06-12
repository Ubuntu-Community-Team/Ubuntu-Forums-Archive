---
title: "Need help with smb client utilities"
date: 2005-09-03
forum: General Help
---

### Post by otakuj462 on 2005-09-03
Hi, I'm having trouble using any and all of the smb client-type utilities, that is: smbclient, smbpasswd, smbfs. The problem seems to be on the Windows end, having to do with how Windows XP handles the password, and I was wondering if anyone had ever run into this problem before, and had found a way to thwart it. 
Here's the network setup:
On the XP box, I have enabled sharing on the folder "itunes_music".
The ip of the Ubuntu box is: 68.113.210.173
The ip of the XP box is: 68.113.210.199
The workgroup name is: @HOME
The hostname of the XP box is: Cm35669-A
And the hostname of the Ubuntu box is: mcomp
On the XP box, the username with admin priveledges is: "smbaccount"
This username uses the password: "smbaccount"
Here's an example of the problem  using smbclient:

```
smbclient -L Cm35669-A -U smbaccount
password: smbaccount

``` 

The output is:

```
session setup failed: NT_STATUS_LOGON_TYPE_NOT_GRANTED
``` 

When I do not specify a password, the output is:
```

Domain=[@HOME] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]
Domain=[@HOME] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]
Anonymous login successful

	Sharename       Type      Comment
	---------       ----      -------
Error returning browse list: NT_STATUS_ACCESS_DENIED
Anonymous login successful

	Server               Comment
	---------            -------

	Workgroup            Master
	---------            -------

```

I always either get NT_STATUS_LOGON_TYPE_NOT_GRANTED or NT_STATUS_ACCESS_DENIED, depending on whether I do or do not give a password. This is true, even when I try to use an XP Guest account that does not have a password. 
smbpasswd and smbfs also return these errors. Does anyone know what's going on?
Thanks.

-Jake

---

### Post by [pl]ice on 2005-09-04
try turning 'guest' acc. and access via net on xp, there are actually couple of 'things' that you can change in the admin tools, that will prevent you from logging in to xp. i think the last time i had to add access for guest in network allowed connection, and turn guest acc on. mind you never tried with passwd for xp.

try net share -I hostname  , should show info; did you try to mount something like that?
 mount -t smbfs //hostname/folder   /something/  ; thats how i do it for the xp box

---

