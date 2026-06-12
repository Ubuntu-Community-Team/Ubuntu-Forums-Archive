---
title: "Installing ath9k_regdomain_override.patch"
date: 2015-12-28
forum: General Help
---

### Post by legion3 on 2015-12-28
Hello.  

I am three months new to Linux/Ubuntu and working my way around using the terminal.    

I have been installing drivers for my Alfa usb wifi card,  So far so good until I go to install the patch.

First stage ok:  

```
~$ wget [http://patches.aircrack-ng.org/ath9k_regdomain_override.patch](http://patches.aircrack-ng.org/ath9k_regdomain_override.patch) --2015-12-28 20:11:26--  [http://patches.aircrack-ng.org/ath9k_regdomain_override.patch](http://patches.aircrack-ng.org/ath9k_regdomain_override.patch)
Resolving patches.aircrack-ng.org (patches.aircrack-ng.org)... 213.186.33.2
Connecting to patches.aircrack-ng.org (patches.aircrack-ng.org)|213.186.33.2|:80... connected. 
HTTP request sent, awaiting response... 200 OK Length: unspecified [text/plain] 
Saving to: &#8216;ath9k_regdomain_override.patch.2&#8217;  ath9k_regdomain_ove     [                   ]   1.48K  --.-KB/s   in 0s       2015-12-28 20:11:29 (31.9 MB/s) - &#8216;ath9k_regdomain_override.patch.2&#8217; saved [1520] 
```

Second stage where I am failing :  

```

~$  patch -Np0  -i ath9k_regdomain_override.patch can't find file to patch at input line 5 
Perhaps you used the wrong -p or --strip option? 

The text leading up to this was: -------------------------- |PaulFertser> Get _your_ country code from regd.h, add 32768 and supply as a parameter. |fercerpav@gmail.com |--- linux-2.6.32-gentoo-r1-orig/drivers/net/wireless/ath/ath9k/main.c	
2009-12-03 06:51:21.000000000 +0300 |+++ linux-2.6.32-gentoo-r1/drivers/net/wireless/ath/ath9k/main.c	2010-01-16 02:04:00.000000000 +0300 -------------------------- 
File to patch: ath9k_regdomain_override.patch patching file ath9k_regdomain_override.patch Hunk #1 FAILED at 28. 
Hunk #2 FAILED at 1588. 
2 out of 2 hunks FAILED -- saving rejects to file ath9k_regdomain_override.patch.rej
```
                                                                                                               I am not wanting to be spoon fed but I have been searching for solutions some time now.  A million and 80 thank yous to who ever replies.  Thanks

---

### Post by matt_symes on 2015-12-28
May i bring to your attention, the following passage from the forums code of conduct.

> Cracking: Requests for help about any form of password or encryption "cracking" are not supported. Even though there are packages such as aircrack in the repositories, discussions about cracking or software related to cracking often lead to discussions about illegal activities. Such threads will be closed.

Thread closed.

---

