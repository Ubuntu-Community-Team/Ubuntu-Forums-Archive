---
title: "Uninstalling Python programs"
date: 2005-09-22
forum: General Help
---

### Post by banjobacon on 2005-09-22
Often, Python programs are installed with the command "python setup.py install". 

Is there a simple command for uninstalling these programs, or should I just be careful and remember to use checkinstall when installing such a program?

---

### Post by John.Michael.Kane on 2005-09-22
Becareful with any and all Python removes  that you may do. i say this having remove almost all python programs it broke the install. if you want use synaptic and search for python and remove the files that way..

---

### Post by banjobacon on 2005-09-22
If I could remove these programs via Synaptic, I wouldn't have a problem. I'm asking about Python programs installed from source.

---

### Post by ow50 on 2005-09-23
Python distutils (the setup.py stuff) does not have uninstallation unless the package distributor self coded that feature. Distutils can make RPMs, but not DEBs. Checkinstall can be used only with GNU autotools (./configure && make && checkinstall/make install).

So there are no good options. The best you can do is create a list of installed files with the "--record" switch, for example "python setup.py install --prefix=/usr/local --record=installed-files.log". It will create a text file that lists all installed files. However, it does not list any created directories. Based on the file list you can either delete the files manually or write a simple shell script to do the uninstallation.

---

### Post by banjobacon on 2005-09-23
[QUOTE=ow50] Checkinstall can be used only with GNU autotools (./configure && make && checkinstall/make install).[/QUOTE]

Are you sure about that? I used checkinstall (sudo checkinstall python setup.py install) and it worked. I didn't get any errors or anything, which suggests all went well.

EDIT: Uninstalling the package checkinstall created works, too.

---

### Post by ow50 on 2005-09-23
[QUOTE=banjobacon]Are you sure about that? I used checkinstall (sudo checkinstall python setup.py install) and it worked. I didn't get any errors or anything, which suggests all went well.[/QUOTE]
I was wrong. Apparently checkinstall can be used with pretty much any installation method.

---

