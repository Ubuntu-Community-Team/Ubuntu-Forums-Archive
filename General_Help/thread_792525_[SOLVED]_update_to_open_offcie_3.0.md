---
title: "[SOLVED] update to open offcie 3.0"
date: 2008-05-13
forum: General Help
---

### Post by elidoperezmd on 2008-05-13
how can i update my open office 2.4 to 3.0 from terminal, is there any way?

---

### Post by atomkarinca on 2008-05-13
Download the tar.gz file from the website

```
tar -xvzf filename.tar.gz
cd filename/DEBS
sudo dpkg -i *.deb
```

---

### Post by zenwalker on 2008-05-13
Read man page of apt-get for that. 

If 2 lazy, then use Synaptic or similar Graphical package manager.

---

### Post by atomkarinca on 2008-05-13
> **zenwalker said:**
> Read man page of apt-get for that. 

If 2 lazy, then use Synaptic or similar Graphical package manager.

OpenOffice.org is not in the repos yet and AFAIK they haven't put up a howto for 3 beta yet.

---

### Post by jlh on 2008-05-15
You have to uninstall OO 2.4 before you install the beta.  That's easiest to do in Synaptic.

---

### Post by atomkarinca on 2008-05-15
> **jlh said:**
> You have to uninstall OO 2.4 before you install the beta.  That's easiest to do in Synaptic.

No, you don't. I have both of them installed and without any problems.

---

### Post by forestpixie on 2008-05-15
> **atomkarinca said:**
> No, you don't. I have both of them installed and without any problems.
+1

---

### Post by carlkhabbaz on 2008-05-15
how do you do that? I dpkg -i *.deb , and then when I run any OO application, it's v2.4

---

### Post by forestpixie on 2008-05-15
I added a launcher to the menu - pointing at here

/opt/openoffice.org3/program/soffice

---

### Post by atomkarinca on 2008-05-15
> **carlkhabbaz said:**
> how do you do that? I dpkg -i *.deb , and then when I run any OO application, it's v2.4

Installing those debs doesn't mean updating your current OpenOffice.org. You are beta testing it now so it installs to a different directory and that's /opt/openoffice.org3/program/. You can create a shortcut in your applications menu for this.

Right-click the menu and select Edit Menu, under Applications > Office, select New Item,

Name: Whatever you like
Command: /opt/openoffice.org3/program/soffice

---

