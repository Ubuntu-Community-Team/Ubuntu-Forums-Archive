---
title: "Libre Office 4.0 blank menus since latest update"
date: 2013-05-20
forum: General Help
---

### Post by CK000 on 2013-05-20
[SIZE=4][FONT=garamond][SIZE=2]Greetings everyone,

I have a serious problem since yesterday's (20 May 2013) updates of Libre Office 4.0 on my ubuntu 12.04.2 LTS installation. All the menus have turned completely blank making it impossible to use.[/SIZE][SIZE=2]
I would very much appreciate any-one's help on this and I thank you all in advance.[/SIZE][/FONT][/SIZE]

---

### Post by cochisebt on 2013-05-20
Hi,
Same problem here...

I have a temporary solution for you, until an update will correct this bug.

sudo apt-get remove indicator-appmenu

However, this will deactivate the global menubar everywhere...

---

### Post by CK000 on 2013-05-20
[SIZE=2]Thank you. Sorry to ask but just what will replace these menus exactly and how will they appear?
 I am  using a 10 inch net-book so screen space is quite a premium which is my reason for asking.[/SIZE]

---

### Post by cochisebt on 2013-05-20
For a while, we have to live with the menu as they were during the good old time of Gnome 2.

As this issue seems to be quite serious, we can expect a fix to be released soon.

The other solution would be to deactivate the PPA, uninstall libreoffice, clean the apt cache and reinstall from the official Ubuntu repository, means going back to Libreoffice 3.5 or 3.6.

---

### Post by CK000 on 2013-05-20
Your second solution seems quite tempting, although more time consuming. However the only thing I don't know how to do is clean the apt cache. I am sorry if this question takes the thread off topic but how does one do that part,  please..?

---

### Post by cochisebt on 2013-05-20
sudo apt-get clean

---

### Post by cochisebt on 2013-05-20
Don't forget, after deactivate the ppa to do this comand:

sudo apt-get update

---

### Post by deadflowr on 2013-05-20
If you want to deactivate the ppa you'll need to install ppa-purge, then run ppa-purge 'package name'.

However, I would wait for the fix to come down before trying to purge the package(s).

Has anyone looked or posted this bug on launchpad yet?

---

### Post by cochisebt on 2013-05-20
> **deadflowr said:**
> 

Has anyone looked or posted this bug on launchpad yet?

I did it.

[https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1182082](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1182082)

---

### Post by monkeybrain2012 on 2013-05-20
> **cochisebt said:**
> For a while, we have to live with the menu as they were during the good old time of Gnome 2.

As this issue seems to be quite serious, we can expect a fix to be released soon.

The other solution would be to deactivate the PPA, uninstall libreoffice, clean the apt cache and reinstall from the official Ubuntu repository, means going back to Libreoffice 3.5 or 3.6.

Or, install ppa-purge
then purge the ppa which will downgrade all the packages

```
sudo apt-get install ppa-purge

sudo ppa-purge ppa:libreoffice/ppa


```

@OP, as there are at least two LO ppas (one is only for version 4) makes it is the right ppa that you are purging.

---

### Post by rikz10 on 2013-05-22
Same problem here. Blank menu only affects libreoffice using Unity. The menu appears well on Gnome Shell desktop.

I prefer Unty interface, that why I uninstalled libreoffice, and reinstalled it directly from de .tar.gz in the libreoffice web site.

 This is a half solution because this version of libreoffice's menu appears well, but is not compatible with menubar

---

### Post by cochisebt on 2013-05-22
Problem fixed since new update.

---

### Post by andrekp on 2013-05-22
> **cochisebt said:**
> Problem fixed since new update.

I figured it would be fixed quick.

Now, all of you that actually DOWNGRADED...  (that's why you don't do that lightly and quickly)

---

