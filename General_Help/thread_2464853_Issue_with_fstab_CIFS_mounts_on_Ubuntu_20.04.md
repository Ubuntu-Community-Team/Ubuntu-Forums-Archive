---
title: "Issue with fstab CIFS mounts on Ubuntu 20.04"
date: 2021-07-14
forum: General Help
---

### Post by essin on 2021-07-14
Hello,
I realize that plazman just posted a problem mounting nfs volumes from fstab.
There is another problem - mounting cifs volumes from fstab.

The web is peppered with reports of not being able to mount windows shares via fstab. These reports have a long history yet the problems persist.
I have tried every suggested permutation of the fstab entries that has been proposed as the "solution" but none of them make any difference.

My two entries work on the debian provided with raspberry pi but they do not work on ubuntu
#mount server_e
//192.168.1xxxServer_E /mnt/server_e   cifs credentials=/root/.smbcredentials_server,vers=3.0  0  0 

#mount server_d
//192.168.1.xxx/Server_D /mnt/server_d   cifs credentials=/root/.smbcredentials_server,vers=3.0  0  0

they don't work at boot and they don't work with mount -a, although some have found that it makes a difference.

Putting the two corresponding mount commands in a shell script works perfectly:
#!/bin/bash
mount -t cifs //192.168.1.xxx/Drive_E /mnt/server_e -o credentials=/root/.smbcredentials_server
mount -t cifs //192.168.1.xxx/Drive_D /mnt/server_d -o credentials=/root/.smbcredentials_server

I've been fighting with this problem for over a year now on 5 separate ubuntu installs.

it seems to me the the only possible remaining conclusion is that there is something broken in the interaction between cifs and whatever process processes the fstab.

I personally don't have the skill necessary to debug and resolve this issue. It would really be a big help if the developers that deal with fstab and cifs got together and resolved it once and for all. And while they are at it, perhaps document some of the non-helpful error messages like "file not found".

I might add that in my opinion unresolved issues like this that are critical to functioning in the real word contribute to the "slow" adoption of linux on the desktop. While I can put up with manually running a script to workaround a flaw in the system, the average computer user could not create such a script and would not put up with the annoyance even if they could.

Thank you

---

### Post by TheFu on 2021-07-14
So, I just tested CIFS from 20.04 to Windows and Samba systems.  Nothing wrong here.

Check everything in the mount. 
[LIST]
[*]Ping the IP? Check.
[*]Verify permissions on the credentials file?  Whoa.  There isn't any file on the 20.04 box.  Hum....  Add one. Restart autofs.  Try again ... JOY!
[/LIST]
```
$ ls /Data/K
'$RECYCLE.BIN'/        pagefile.sys                  Users/
'Hauppauge Capture'/   Photos/                       V/
 IPv6.disable.txt     'Recorded TV'/                 VirtualBox/
 n4-back.cmd          'System Volume Information'/

$ df .
Filesystem        Size  Used Avail Use% Mounted on
//172.22.22.14/K   74G   18G   57G  24% /Data/K
```
Appears to be working here.

About 5 yrs ago, systemd-mount took over from whatever the fstab subsystem do previously.

```
//192.168.1xxxServer_E /mnt/server_e cifs credentials=/root/.smbcredentials_server,vers=3.0 0 0
```
Looks like it has 2 typos. Try this:
```
//192.168.[COLOR="#800080"]{missing}.[/COLOR][COLOR="#0000FF"]1xx[/COLOR][COLOR="#FF0000"]/[/COLOR]Server_E /mnt/server_e cifs credentials=/root/.smbcredentials_server,vers=3.0 0 0
```

LAN IPs don't need to be hidden. They aren't sensitive at all.
I use a few other options. ```
iocharset=utf8,file_mode=0660,dir_mode=0770
```

Ensure the credentials file has a valid Windows/Samba name.

BTW, around March of 2020, Microsoft changed some of these long-standing defaults when it comes to CIFS shared storage.  There are a few threads here about those changes with corrective solutions. [Https://ubuntuforums.org/showthread.php?t=2435292&p=13925468#post13925468](Https://ubuntuforums.org/showthread.php?t=2435292&p=13925468#post13925468) is one of those.  I have in my notes that a reboot is required for this. Restarting services on either Linux or Windows systems isn't sufficient.

---

