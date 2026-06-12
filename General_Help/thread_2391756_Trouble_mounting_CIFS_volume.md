---
title: "Trouble mounting CIFS volume"
date: 2018-05-12
forum: General Help
---

### Post by xeddog on 2018-05-12
I am having a devil of a time trying to get a cifs volume mounted in fresh install of Ubuntu 18.04.  I've been working on this for two days (off and on, mostly off though).  I have copied settings for the /etc files from a running 16.04 machine to get started, and then trying google and this site to get resolutions for problems.  Here is where I am now.

nfs-kernel-server, nfs-common, and cifs-utils have been installed.

The fstab entry for the device is:
  //10.1.1.1/Data_Store_3		/media/Cloudy	cifs	guest,uid=1000,iocharset=utf8	0	0

For now, guest logins are allowed and do not require passwords.  I'll take care of that if I can ever get this thing mounted.  And If I really want to get the groans going, this is a disk drive attached to an Asus router.  It is a temporary solution for a problem until I can get a NAS.


Permissions for /media:
drwxr-xr-x   5 root root       4096 May 12 17:06 media

Permissions for /media/Cloudy (the cifs volume)
drwxrwxrwx  2 <my userid> <my userid> 4096 May 12 17:06 Cloudy

When I issue "mount /media/Cloudy" command I get:
mount: /media/Cloudy: operation permitted for root only.

When I use "sudo mount /media/Cloudy" I get:
mount error(112): Host is down
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

Read the manpage for mount.cifs (and even understood a line or two) and then tried the command 
sudo mount.cifs //10.1.1.1/Data_Store_3 /media/Cloudy -o user=<my userid> pass=<my password> 

I get prompted:
Password for <my userid>@//10.1.1.1/Data_Store_3: 
 
No matter what password I use (even the correct one), I get 
mount error(112): Host is down
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

I also tried using "user=guest" with no password, and a "pass=guest" and I still get the same response.


Any suggestions?


Thanks,

Wayne

---

### Post by Morbius1 on 2018-05-13
Regrettably "Host is down" can mean many things aside from the host actually being down.

When you run a cifs mount in Ubuntu 18.04 it has by default the following settings which may be applicable to this issue:
> sec = ntlmssp
vers = 3.0
This ASUS router is probably running Samba but it may be a very old version so I would try different variations of your mount command:
> //10.1.1.1/Data_Store_3 /media/Cloudy cifs guest,uid=1000,iocharset=utf8[COLOR=#0000cd]**,vers=1.0,sec=ntlm**[/COLOR] 0 0

There was a post yesterday where the user had to go as far as setting sec=none before he could connect to his NAS so you might want to try that one next:
> //10.1.1.1/Data_Store_3 /media/Cloudy cifs guest,uid=1000,iocharset=utf8[COLOR=#0000cd]**,vers=1.0,sec=none**[/COLOR] 0 0

THere is one more thing and it may or may not be an issue here but you may need to add one more option: [COLOR=#0000cd]**nounix **[/COLOR][COLOR=#000000]to you list of options. It doesn;t impact the inital mount of the share but it may have an impact regarding permissions on it's content.[/COLOR][COLOR=#0000cd][/COLOR]

---

### Post by xeddog on 2018-05-13
Thanks Morbius.  Your first option "vers=1.0,sec=ntlm" did the trick.  I had tried putting in just the vers=1.0 by itself earlier and it had no effect.  Adding the sec=ntlm to it works, but now I don't know if it was just adding the sec=, or the combination.  Anyway, thank you.

Wayne

---

