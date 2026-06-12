---
title: "[SOLVED] How can I remove thoroughly a software?"
date: 2008-02-10
forum: General Help
---

### Post by yingzhou on 2008-02-10
I do unistall my firefox with this code:

sudo apt-get remove --purge firefox

but when I reinstall, it still have configuration like before Uninstall. How can I remove  thoroughly it. I want to install the new clean version. :confused:

Thanks anyway!

---

### Post by stchman on 2008-02-10
> **yingzhou said:**
> I do unistall my firefox with this code:

sudo apt-get remove --purge firefox

but when I reinstall, it still have configuration like before Uninstall. How can I remove  thoroughly it. I want to install the new clean version. :confused:

Thanks anyway!

Do the following:

```
sudo apt-get -y autoremove <application>
```

In Edgy and later autoremove removes the program and dependencies.

Go into synaptic and remove the residual config.

---

### Post by yingzhou on 2008-02-10
> **stchman said:**
> Do the following:

```
sudo apt-get -y autoremove <application>
```

In Edgy and later autoremove removes the program and dependencies.

Go into synaptic and remove the residual config.

It's not complete remove firefox, when I'm reinstall it still exactly like before.

anyway how to remove the residual config?

Thanks :)

---

### Post by dhysk on 2008-02-10
i belive the config is user dependent so once you uninstall firfox se if you have the file /home/username/.mozilla

notice its a hidden file so you can find it if you type do the command:
ls -a /home/username/ | grep mozilla

if that file is still there you may have to delete it before you reinstall

---

### Post by yingzhou on 2008-02-10
> **dhysk said:**
> i belive the config is user dependent so once you uninstall firfox se if you have the file /home/username/.mozilla

notice its a hidden file so you can find it if you type do the command:
ls -a /home/username/ | grep mozilla

if that file is still there you may have to delete it before you reinstall

Thanks you all! Problem solved!!!

---

### Post by stchman on 2008-02-11
> **yingzhou said:**
> It's not complete remove firefox, when I'm reinstall it still exactly like before.

anyway how to remove the residual config?

Thanks :)

To finish completely removing Firefox remove the ~/.mozilla folder.  That folder contains all your configuration files.

TO remove the residual config do

System--->Administration--->Synaptic Package Manager

Click the Status button and highlight the residual config portion.

When there Mark for complete removal each item.

---

