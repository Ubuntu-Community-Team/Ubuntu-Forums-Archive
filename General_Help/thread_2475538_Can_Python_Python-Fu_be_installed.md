---
title: "Can Python Python-Fu be installed ?"
date: 2022-05-31
forum: General Help
---

### Post by satimis on 2022-05-31
Hi all,

Can Python Python-Fu, the plugin of GIMP, be installed and run on Ubuntu20.04 and 22.04.  My searching result on Internet was negative.

On Ubuntu 20.04
$ apt policy python```

python:
  Installed: (none)
  Candidate: (none)
  Version table:
     2.7.15~rc1-1 -1
        100 /var/lib/dpkg/status

```        
Python is NOT on repo.

Please advise.  Thanks

Regards

---

### Post by Impavidus on 2022-05-31
I don't know about Gimp plugins or Phython. Python however is a core component of Ubuntu. For compatibility reasons, the package python installs the old version Python 2.7 and is no longer installed by default. The current version is installed using the package python3.

---

### Post by satimis on 2022-05-31
> **Impavidus said:**
> I don't know about Gimp plugins or Phython. Python however is a core component of Ubuntu. For compatibility reasons, the package python installs the old version Python 2.7 and is no longer installed by default. The current version is installed using the package python3.
Thanks for your advice.

I'll run flatpak to install python3.9

Maybe on Ubuntu 22.04 desktop

Regards

---

### Post by Topsiho on 2022-06-01
First try  type in the terminal:

python3  (and then enter)

You should get something like:


Python 3.10.4 (main, Apr  2 2022, 09:04:19) [GCC 11.2.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> 

As said above python3 is a core component of the modern Ubuntu's, which means that Ubuntu can't run without it.

Topsiho

---

