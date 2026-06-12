---
title: "Problems with update"
date: 2007-02-06
forum: General Help
---

### Post by ginnie6 on 2007-02-06
New Ubuntu user here. i have it installed on my 2nd hard drive (winxp on other) and I'm getting the message that I have updates to install. when I try though it tells me
<E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. >

so I went to terminal and typed that in. I then get the message that  <requested operation requires superuser privilege> 

help please!
I tried typing in my password and it said command was not recognized.

---

### Post by ginnie6 on 2007-02-06
I should've searched! found the answer!

---

### Post by Dr Small on 2007-02-06
> I then get the message that <requested operation requires superuser privilege> 

Type:
sudo dpkg --configure -a


Dr Small

---

