---
title: "Samba question"
date: 2007-12-27
forum: General Help
---

### Post by ksinc on 2007-12-27
I'm not sure if this is the right forum for this, if not please let me know which forum is most appropriate. I have Samba 3.0.28 up and running on an Ubuntu 6.06 LTS server. I have created 3 folders on the server and "shared" them in the smb.conf file. From an XP Pro machine I can browse to the server and see all 3 folders however they are all pointing to the /tmp folder on the server not the 3 folders I wanted. My smb.conf file has:

***** SHARES *****

[Data]
/Data
Guest OK = No
Writable = Yes
Write List = Kevin

[Kevin]
/home/Kevin
Guest OK = No
Writable = Yes
Write List = Kevin

[MyBook]
/mnt/MyBook
Guest OK = No
Writable = Yes
Write List = Kevin

Any help would be much appreciated.

Kevin

---

### Post by xdice on 2007-12-27
> **ksinc said:**
> I'm not sure if this is the right forum for this, if not please let me know which forum is most appropriate. I have Samba 3.0.28 up and running on an Ubuntu 6.06 LTS server. I have created 3 folders on the server and "shared" them in the smb.conf file. From an XP Pro machine I can browse to the server and see all 3 folders however they are all pointing to the /tmp folder on the server not the 3 folders I wanted. My smb.conf file has:

***** SHARES *****

[Data]
/Data
Guest OK = No
Writable = Yes
Write List = Kevin

[Kevin]
/home/Kevin
Guest OK = No
Writable = Yes
Write List = Kevin

[MyBook]
/mnt/MyBook
Guest OK = No
Writable = Yes
Write List = Kevin

Any help would be much appreciated.

Kevin

Try changing your config to this one:


[Data]
path = /Data
Guest OK = No
Writable = Yes
Write List = Kevin

[Kevin]
path = /home/Kevin
Guest OK = No
Writable = Yes
Write List = Kevin

[MyBook]
path = /mnt/MyBook
Guest OK = No
Writable = Yes
Write List = Kevin

One thing I noticed, is that my smb.conf file has no capital letters for things like 'Writable' and other keywords, but I don't know if that really matters or not.

---

### Post by ksinc on 2007-12-27
Thank you, that worked. 

Kevin

---

