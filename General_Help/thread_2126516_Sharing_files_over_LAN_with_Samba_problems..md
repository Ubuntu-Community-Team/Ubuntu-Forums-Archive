---
title: "Sharing files over LAN with Samba problems."
date: 2013-03-17
forum: General Help
---

### Post by Sacrum on 2013-03-17
[COLOR=#000000][FONT=verdana]Hi! Recently I bought a HTPC for my living room and I ran into a problem I was hopping you guys could help me with![/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]So, currently the HTPC runs Ubuntu 12.04 and my desktop runs Windows 7. The thing I want to do is to share all the files in the external hard-drive on the HTPC with my Windows desktop. I'm using [Samba]("http://www.samba.org/samba/docs/") on the HTPC to share files but the problem is that it won't allow me to share my external hard-drive, I can share my /home folder but nothing else. When trying to access the external-drive from my Windows-computer I get an error message saying I don't have permission.[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]h[ttp://fuskbugg.se/dl/0jCPUB/Samba-Ubuntu.png]("http://fuskbugg.se/dl/0jCPUB/Samba-Ubuntu.png") <- That is a picture of the network sharing setting in my /home and external-drive in Ubuntu. The only difference is the "folder access" under "group". This is the thing I need to change. Furthest to the right is Sambas setting. Everything in /home and /external-drive is the same, but I still can't access the external drive from my Windows-computer. If I try to change the "folder access" settings under "group" on the external hard-drive it just changes back to "none". How do I stop it from changing back?[/FONT][/COLOR]

---

### Post by zero2xiii on 2013-03-17
Hay,

It has to do with permissions of the file system.

NTFS, FAT and the EXT's has very different permissions.

Fat for example has no "group" permission where as ext has.

To get around this, try sharing the drive as sudo, or use your local user to log in via samba.

Cheers

---

### Post by Sacrum on 2013-03-17
> **zero2xiii said:**
> Hay,

It has to do with permissions of the file system.

NTFS, FAT and the EXT's has very different permissions.

Fat for example has no "group" permission where as ext has.

To get around this, try sharing the drive as sudo, or use your local user to log in via samba.

Cheers
Sorry, but I'm not that experienced with Ubuntu.
How do I do that?

---

### Post by zero2xiii on 2013-03-17
Hay,

Okay so it is forum policy to state how dangerous it might be to do things as root etc. So please be careful and never use root or sudo if you are not sure what you are doing.

Right.

In terminal do the following:
```
gksudo nautilus
```

This will open up nautilus with sudo privileges . Now do exactly as you did before in this new sudo level nautilus and check access on your windows machine.

If this fails, try going into the windows machine, right click on the folder and look for an option such as "log in as" or similar.

There are several places windows provide this option. Right click on the computer in the "my network places". I think this might be one location (I cant remember exactly).
Now use the ubuntu username and password to log in.

If all the above fail, please post the output of:
```
cat /etc/samba/smb.conf
```

Cheers

---

### Post by Morbius1 on 2013-03-17
Remember that when the system mounts the external ntfs usb drive it will mount with owner = ###-family ( in this case ) and with permissions of 700. The only person getting access to that folder is ###-family. One way around this is to make the remote user appear to be ###-family by adding the following line to the share definition for [Expansion Drive]:
```
force user = ###-family
```

So edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```
Add the force user line to the share definition - something like this:
> [Expansion Drive]
path = /media/###-family/Expansion Drive
writeable = yes
;    browseable = yes
[COLOR=#0000cd]**force user = ###-family**[/COLOR]
guest ok = yes

Or something like this if you require username and password authentication:
> [Expansion Drive]
path = /media/###-family/Expansion Drive
writeable = yes
;    browseable = yes
[COLOR=#0000cd]**force user = ###-family**[/COLOR]
guest ok = no
Then restart samba:
```
sudo service smbd restart
```

---

### Post by Sacrum on 2013-03-18
> **Morbius1 said:**
> Remember that when the system mounts the external ntfs usb drive it will mount with owner = ###-family ( in this case ) and with permissions of 700. The only person getting access to that folder is ###-family. One way around this is to make the remote user appear to be ###-family by adding the following line to the share definition for [Expansion Drive]:
```
force user = ###-family
```

So edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```
Add the force user line to the share definition - something like this:


Or something like this if you require username and password authentication:

Then restart samba:
```
sudo service smbd restart
```
It worked! Thank you, thank you, thank you!

> **zero2xiii said:**
> Hay,

Okay so it is forum policy to state how dangerous it might be to do things as root etc. So please be careful and never use root or sudo if you are not sure what you are doing.

Right.

In terminal do the following:
```
gksudo nautilus
```

This will open up nautilus with sudo privileges . Now do exactly as you did before in this new sudo level nautilus and check access on your windows machine.

If this fails, try going into the windows machine, right click on the folder and look for an option such as "log in as" or similar.

There are several places windows provide this option. Right click on the computer in the "my network places". I think this might be one location (I cant remember exactly).
Now use the ubuntu username and password to log in.

If all the above fail, please post the output of:
```
cat /etc/samba/smb.conf
```

Cheers
I got it work. Thanks for helping me with this!

---

