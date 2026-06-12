---
title: "Unable to access Samba shares."
date: 2013-04-09
forum: General Help
---

### Post by pingaan on 2013-04-09
Hi,

I'm not sure if I should post here, on some Windows forum or Samba sub-forum. 


My issue is that I'm not able to access my Samba shares from my Windows 7 computer. It works fine on my Android devices. 
I'm running Ubuntu 12.04.
At the point where I'm supposed to enter login/pw I just get the message: "Windows cannot access \\machine\share".


Any ideas?


Cheers.

---

### Post by pingaan on 2013-04-11
Is there relly no one else who has had this problem?

---

### Post by kuifje09 on 2013-04-11
Sorry , smbfind does not exist on my system,  so go for smbclient.

smbclient -L address -U username

It will ask for a passwd or  just give return.

In both cases you should get some information back...

what is your command to look at /  or mount from

---

### Post by pingaan on 2013-04-14
Isn't that if you want to connect to another computer from the Debian platform? I'm having problem doing the opposite! :-P
Maybe I should go NFS instead.

---

### Post by kuifje09 on 2013-04-14
For Unix and Linux systems you can use NFS. To mount from windows you can use samba/cifs .  Or if you want to, you also can get a free version of some nfsserver and or client for windows.  Windows default exports in a samba/cifs way.

---

### Post by pingaan on 2013-04-15
NFS works fine in Vista/7 Ultimate or Enterprise. It's built-in.

---

