---
title: "Login screen is &quot;Choose a host to conect to:&quot;"
date: 2007-10-21
forum: General Help
---

### Post by anko on 2007-10-21
Hi,
I've recently upgraded to 7.10 and in display settings I have unwittingly choosen an incorrect option.

My login screen (within X) has dissappeared! now it says

"Choose a host to connect to:" and gives a list of hosts with XDMCP enabled.  As XDMCP is not enabled on my machine, I can't log in locally!

I can get a root command line shell outside of X, but i just need to work out which config has changed so I can set it back.

Please help!!!

Anko

---

### Post by Beggar on 2007-10-21
Sounds like a gdm reinstall is in order. It will complain about needing to uninstall ubuntu-desktop, thats fine. If you have messed up gdm

```

sudo apt-get remove gdm
sudo apt-get install ubuntu-desktop

```

Unless I misread this, if you mean you have misconfigured X, then your proper recourse is going to be
```

sudo dpkg-reconfigure -phigh xserver-xorg

```

---

### Post by anko on 2007-10-22
thanks beggar!

It turned out that gdmchooser was being started instead of gdmgreeter,
so I changed it in /etc/gdm/gdm.conf-custom

all fixed!

thanks again

---

### Post by screate on 2008-04-22
Thank you Thank you Thank you! I was about to reinstall the works! been looking for this answer for a week!

---

