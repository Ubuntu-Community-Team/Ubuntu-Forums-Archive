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
/MyBook
Guest OK = No
Writable = Yes
Write List = Kevin

Any help would be much appreciated.

Kevin

---

### Post by Dngrsone on 2007-12-27
Stoopid question/comment... you do know that Linux is very case-sensitive, right?  I'm just asking if you verified that the folders you have listed in the smb.conf file are the same as what your systems has as related to letter-case.

---

### Post by ksinc on 2007-12-27
Thank you for the response, yes I am aware that Linux is case sensitive and the folder names  in to smb.conf file do match the actual folder names, I just double-checked. :)  

Kevin

---

