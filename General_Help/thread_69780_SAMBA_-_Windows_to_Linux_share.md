---
title: "SAMBA - Windows to Linux share"
date: 2005-09-27
forum: General Help
---

### Post by shubjero on 2005-09-27
Hey folks, I have been enjoying ubuntu up to this far.

I have installed and setup samba EXACTLY according to the Unofficial Ubuntu 5.04 starter guide.

I got my Windows shares mounted in Linux just great!  They are in fstab and load on boot.  I love it.

The big problem is I *CANNOT* get Windows to view the Linux shares.  The login/password on the Windows XP & Linux box are the same.  When I try to connect with Explorer to the share via '\\ubuserv\' it prompts me for a login and password.  I enter the login and password that I setup during the Start Guide and it just prompts me again for login/password.

From a command prompt I get this error:
--------------------------------------------------------
C:\Documents and Settings\shubjero>net view ubuserv
System error 5 has occurred.

Access is denied.
--------------------------------------------------------

I have attached my smb.conf and smbusers to this post.  I have renamed them to .txt because the forum didnt like the original names *shrug*.

Please... help me out with this one guys.

---

### Post by Hobgoblin on 2005-09-27
replace system_username in smbusers with your actual username.

That's how I have it and can mount from windows.

---

### Post by shubjero on 2005-09-27
so shubjero = "shubjero"

?

---

### Post by shubjero on 2005-09-27
dude you are a god.  Thank you so much!

---

