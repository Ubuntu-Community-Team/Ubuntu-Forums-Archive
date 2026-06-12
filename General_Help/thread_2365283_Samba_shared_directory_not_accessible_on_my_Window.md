---
title: "Samba shared directory not accessible on my Windows 10."
date: 2017-07-04
forum: General Help
---

### Post by marlonmin on 2017-07-04
I have spent hours of hours on this thing, but still unable to get it to work. I am running [FONT=monospace][COLOR=#000000]Ubuntu 17.04, and 

[/COLOR][/FONT][HTML]sudo smbstatus
[sudo] password for abigail:  

Samba version 4.5.8-Ubuntu
PID     Username     Group        Machine                                   Protocol Version  Encryption           Signing               
----------------------------------------------------------------------------------------------------------------------------------------
4027    abigail      abigail      10.0.0.79 (ipv4:10.0.0.79:50655)          SMB3_11           -                    partial(AES-128-CMAC)

Service      pid     Machine       Connected at                     Encryption   Signing      
---------------------------------------------------------------------------------------------
IPC$         4027    10.0.0.79     Tue Jul  4 01:35:36 PM 2017 PDT  -            -            

No locked files

[/HTML]

[FONT=monospace]My samba conf is the default one, and the only change I made is to add this to the end of the file:
[/FONT][HTML][share2]
path =/home/abigail/Documents/share2
available = yes
valid users = abigail
read only = no
browsable = yes
public = yes
writable = yes
write list = abigail
create mask = 0775

[/HTML]

When I try to access the 'share2' folder from my Windows 10 using the user name "abigail", it always says "access is denied".  Is there a way to fix this?

---

