---
title: "Software index broken"
date: 2007-06-29
forum: General Help
---

### Post by Norm2787 on 2007-06-29
I am new to Linux and Ubuntu so I am not up the command lines etc. Would like any help I can get to solve this problem need baby steps, Thanks
I can't update or remove any packages. I get error:

Preconfiguring packages ... 
, in file `/var/lib/dpkg/status' near line 7196 package `avahi-autdpkg: parse erroroipd': 
 newline in field name `G' 
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by mouseboyx on 2007-06-29
run the command:
 ```
gksu synaptic
```If it gets any errors then do what it says, if it doesn't then, click on the button in the lower left hand corner that says status, then in the column on the left if it displays the word broken, click on it then completely remove all the packages in that section.

---

### Post by ProxyGUTSY on 2008-02-19
Thanks three day , I didn't solve the same problem on my Laptop.

I remove and everything is fine now ...:guitar:

---

