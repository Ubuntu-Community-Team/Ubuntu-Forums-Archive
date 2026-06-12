---
title: "I Want The Automatix Nautilus Scripts"
date: 2008-05-02
forum: General Help
---

### Post by Eddie Wilson on 2008-05-02
Good Day All,
I know that this is a silly question but I've been using a Kde distro. It has a superuser mode for the file manager. I was told that I could do the same thing in Ubuntu using Nautilus scripts. I was told I could install it using Automatix. Automatix will not work with 8.04. How can I install the Nautilus scripts that were installed using Automatix.

Thanks,
Eddie

---

### Post by fragos on 2008-05-02
The scripts are for the Gnome environment with uses Nautilus. You can get the latest from [http://gnomefiles.org/download.php?soft_id=2194&where=http%3A%2F%2Fwww.nanolx.org%2Ffree%2FNScripts-2.5.tar.bz2](http://gnomefiles.org/download.php?soft_id=2194&where=http%3A%2F%2Fwww.nanolx.org%2Ffree%2FNScripts-2.5.tar.bz2). If you don't have the following directory, create it ~/.gnome2/nautilus-scripts. Right click the NScripts tar ball and select extract here. Directory NScripts will appear. Move the 3 folders in to the directory you created in ~/.gnome2. When you restart nautilus and right click a file, "Scripts" will be an option.

---

### Post by Eddie Wilson on 2008-05-02
Thank you very much sir.

Eddie

---

### Post by explainer on 2008-11-14
I would like the Nautilus Scripts as well.  I tried the link in George's reply, and it is no longer active.  Does anyone have an alternate source?

---

### Post by dullard on 2008-11-14
Newer version:

[http://www.nanolx.org/free/NScripts-3.4.tar.bz2](http://www.nanolx.org/free/NScripts-3.4.tar.bz2)


Untested here, btw.

---

### Post by oldos2er on 2008-11-14
> **Eddie Wilson said:**
> Good Day All,
I know that this is a silly question but I've been using a Kde distro. It has a superuser mode for the file manager. I was told that I could do the same thing in Ubuntu using Nautilus scripts. I was told I could install it using Automatix. Automatix will not work with 8.04. How can I install the Nautilus scripts that were installed using Automatix.

Thanks,
Eddie

 No need for Automatix. Install the package nautilus-gksu, then restart X.

---

