---
title: "cifs mount problem in Gutsy tribe 4"
date: 2007-08-21
forum: General Help
---

### Post by ttwaro on 2007-08-21
Hi. Until yesterday I have been running kubuntu 7.04 and for months was able to mount via fstab two XP shares using

//192.168.4.10/NetworkShare /shares/windows_f cifs rw,credentials=/root/.creds,uid=ttwaro,gid=ttwaro 0 0
//192.168.4.10/NetworkShare2 /shares/windows_o cifs rw,credentials=/root/.creds,uid=ttwaro,gid=ttwaro 0 0

Yesterday, I did a fresh install of Gutsy Tribe 4 which went smoothly. However, after I created /shares, /shares/windows_f and /shares/windows_o and updated my new fstab with these lines and copied my .creds file to /root the shares get a "Permissions error".

The permissions on the shares is:

drwxrwxrwx   4 root root  4096 2007-08-21 06:22 shares

drwxrwxrwx  4 root   root   4096 2007-08-21 06:22 .
drwxr-xr-x 22 root   root   4096 2007-08-21 06:18 ..
drwxrwxrwx  1 ttwaro ttwaro    0 2007-07-10 08:18 windows_f
drwxrwxrwx  1 ttwaro ttwaro    0 2007-08-21 07:53 windows_o

My .creds file is:

username=ttwaroadm
password=roller:coaster

If I update my fstab by including my username and password like so it works:

//192.168.4.10/NetworkShare /shares/windows_f cifs rw,domain=localdomain,username=ttwaroadm,passwd=roller:coaster,uid=ttwaro,gid=ttwaro 0 0
//192.168.4.10/NetworkShare2 /shares/windows_o cifs rw,domain=localdomain,username=ttwaroadm,passwd=roller:coaster,uid=ttwaro,gid=ttwaro 0 0

I have also tried changing my .creds file to:

username=ttwaroadm
password=roller:coaster
domain=localdomain

but this still doesn't mount when boot or try to manually mount it.

Does anyone have any ideas? I want to run with a credentials file for security reasons but can't get this to work under Gutsy.

TIA

Tom

---

