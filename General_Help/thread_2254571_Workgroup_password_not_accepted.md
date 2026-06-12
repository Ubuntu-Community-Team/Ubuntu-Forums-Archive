---
title: "Workgroup password not accepted"
date: 2014-11-28
forum: General Help
---

### Post by maviscruet2 on 2014-11-28
Hello,

I am relatively new to Ubuntu (I have used it casually in the past, but never for anything technical) and have set up an old PC as a file server.  I have installed Samba, set up various options for folders to share including usernames and passwords.  I have set up a workgroup and have no trouble accessing the computer from my android phone using ES File Explorer.  Now I am trying to get my Windows 7 PC and the Ubuntu machine to communicate.  When I try to connect, via browse Network, it sees the workgroup and has my username in the box, but won't accept the password.  I have changed it using sudo smbpasswd -a [username] and it still won't accept it. 

What am I doing wrong and is there more information you'd need?

I did search the forum, and found someone with the same issue, but the smbpasswd solution fixed it for them.

Hope you can help.

---

### Post by SeijiSensei on 2014-11-28
Take a look at the logs in /var/log/samba and see what problems they report.  There's a general one, smbd.log, and host-specific logs as well.

---

### Post by maviscruet2 on 2014-11-28
The last entry in log.mnbd is: 

  register_name: NetBIOS name MAVIS-SYSTEM-PRODUCT-NAME is too long. Truncating to 
[2014/11/28 11:00:49,  0] ../source3/nmbd/nmbd_become_lmb.c:397(become_local_master_stage2)
  *****
  
  Samba name server MAVIS-SYSTEM-PRODUCT-NAME is now a local master browser for workgroup ETHERMAVIS on subnet 192.168.0.7

And in log smbd: 

[2014/11/28 11:01:24.186622,  0] ../source3/param/loadparm.c:3188(lp_do_parameter)
  Global parameter username map found in service section!

I can make neither head nor tail of either.  They're repeated a lot so I guess that is when I am trying to do it.

My netbios name in smb.conf is "netbios name = mavis-system-product-name".

Is that conflicting because it's too long?

---

### Post by redmk2 on 2014-11-28
> **maviscruet2 said:**
> The last entry in log.mnbd is: 

  register_name: NetBIOS name MAVIS-SYSTEM-PRODUCT-NAME is too long. Truncating to 
[2014/11/28 11:00:49,  0] ../source3/nmbd/nmbd_become_lmb.c:397(become_local_master_stage2)
  *****
  
  Samba name server MAVIS-SYSTEM-PRODUCT-NAME is now a local master browser for workgroup ETHERMAVIS on subnet 192.168.0.7

And in log smbd: 

[2014/11/28 11:01:24.186622,  0] ../source3/param/loadparm.c:3188(lp_do_parameter)
  Global parameter username map found in service section!

I can make neither head nor tail of either.  They're repeated a lot so I guess that is when I am trying to do it.

My netbios name in smb.conf is "netbios name = mavis-system-product-name".

Is that conflicting because it's too long?
Yes!  It should be no longer than 15 characters.

---

### Post by SeijiSensei on 2014-11-29
> **maviscruet2 said:**
> [2014/11/28 11:01:24.186622,  0] ../source3/param/loadparm.c:3188(lp_do_parameter)
  Global parameter username map found in service section!
This means you have the "username map" directive in a section that defines a service, like [homes].  It should be in the [global] section at the top of smb.conf.

---

### Post by maviscruet2 on 2014-12-01
Isn't my netbios name tied to my computer's name?  If so, is that okay to change?

---

### Post by maviscruet2 on 2014-12-01
This is the full text of my smb.conf file (if this makes my computer insecure, please enjoy my wildlife photos and collection of Leonard Cohen!):

> [global]	server string = Linux Server
	workgroup = ETHERMAVIS
;	netbios name = mavis-system-product-name
	security = user
;	encrypt passwords = yes
;	guest account = nobody
	name resolve order = bcast host
	include = etc/samba/smbshared.conf
	username map = /etc/samba/smbusers
;	guest ok = no


[My Music]
	path = /media/mavis/New Volume/My Music
;	writeable = no
;	browseable = yes
	guest ok = yes


[My Pictures]
	path = /media/mavis/New Volume/My Pictures
;	writeable = no
;	browseable = yes
	guest ok = yes


[My Videos]
	path = /media/mavis/New Volume/My Videos
;	writeable = no
;	browseable = yes
	guest ok = yes

---

### Post by redmk2 on 2014-12-02
> **maviscruet2 said:**
> Isn't my netbios name tied to my computer's name? If so, is that okay to change? 

The netbios name is the name that is always used to define a SMB resource (the share) as in //NETBIOS_NAME/SHARE_NAME.  The hostname does not have to be the same as the netbios name.  If you do not define the netbios name then the *nmbd *daemon attempts to use the hostname (in /etc/hosts) as the netbios name.  There is a 15 character limit plus a 1 character suffix that is used to define the type of SMB object (server, master browser, client, etc.).  If the hostname is greater than 15 characters Samba will truncate it.  Will that cause problems?  Who knows.  I have always observed the netbios naming convention.  Fifteen characters plus one character for the suffix (15+1).  I suggest you pick a shortened netbios name for your server.  You define the name in the [global] section of the smb.conf file like this```
netbios name = <some-short-name>
```... where <some-short-name> is a name you define.

---

