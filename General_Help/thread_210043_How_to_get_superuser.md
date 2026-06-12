---
title: "How to get superuser"
date: 2006-07-06
forum: General Help
---

### Post by ShirishAg75 on 2006-07-06
Hi all,
       I just installed Ubuntu 6.06. Everything is fine but can't get superuser status. 
I gave su & it asks me for pwd. I gave the same password but didn't work. I need root access.The other way is to re-install the whole thing again.  
   Then also how do I make sure that there is a root & it has some pwd or not.
       Any ideas? Thnx in advance.

---

### Post by blackjack6.21.91 on 2006-07-06
> sudo -i -H
Is probably what your looking for.  That will give you a root terminal.  Did you come from a different distro?  Perhaps redhat or something?  Because in Ubuntu it is more common to add "sudo" in front of commands that require root privelages.  For example:
> sudo gedit /etc/apt/sources.list

peace

---

### Post by barbarian on 2006-07-06
hi, 
*sudo su*

---

### Post by mlind on 2006-07-06
Read this first [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by ShirishAg75 on 2006-07-06
Thnx guys, no was using ubuntu long time back hence had forgotten how the things work :(

---

