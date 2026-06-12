---
title: "firefox 3 problem  in opening pdf"
date: 2008-06-16
forum: General Help
---

### Post by black drongo on 2008-06-16
hi i use xubuntu and i have installed firefox 3.0.
problem is firefox doesn't allow me to view pdf direcly, that is on double clicking it asks for a path to save the file, instead of giving the usual options of open, save ..
i tried to change this in Preferences> Applications
but it seems to be empty.
i am able to open the file from the downloaded location as well as by clicking in the downloads (history) window.
another problem is when i try to open any other file in Downloads (word, zip....) it tries to open it in Evince viewer and says wrong mime type.

---

### Post by lswest on 2008-06-16
can you navigate to ```
about:plugins
``` in firefox (type it into the address bar) and see if there is any plugin listed for pdfs, if not, post back.

---

### Post by suhailsqm on 2008-06-16
i gues  i too have the same problem ...
i can't find any plugins for pdf ....
if i try to search fro them in "https://pfs.mozilla.org/plugins/"
it won't open.. my browser works fine and it's configured for the internet.

suggestions plz..
suhail

---

### Post by lswest on 2008-06-16
Well, you could always download [adobe reader]("http://www.adobe.com/products/acrobat/readstep2_servefile.html?option=full&platform=LINUX_.deb&order=1&type=&esdcanbeused=0&esdcanhandle=0&hasjavascript=1&dlm=&os=linux&winPlatform=&macPlatform=&linuxPlatform=LINUX_.deb&solarisPlatform=&aixPlatform=&hpPlatform=&mobilePlatform=&otherPlatform=&language=English&order_radio=1&buttonDownload=&getgtb=0&getsconly=0") (that's a link right to the .deb download of adobe reader).  Otherwise, make sure you've installed ubuntu-restricted-extras, and you can try installing mozplugger (package name, check synaptic to install it) which should allow you to open external viewer applications within firefox (e.g. opens epdfview in firefox so you can read the pdf).  I'm not too sure about open-source plugins for firefox, as I use adobe reader for that stuff.

---

### Post by black drongo on 2008-06-17
thank u lswest.
i looked in about: plugins.
but there is no plugin for pdf.i am attaching the out put.does it throw any light?

---

### Post by rockstarrem on 2008-06-17
Instead of just installing the program itself try installing the plugin for it: [https://addons.mozilla.org/en-US/firefox/browse/type:7](https://addons.mozilla.org/en-US/firefox/browse/type:7)

---

### Post by suhailsqm on 2008-06-17
:popcorn:

---

### Post by ibuclaw on 2008-06-17
If you add yourself to the medibuntu repository, there is a package called **acroread-plugins** that lets you view pdf files with Adobe Reader in Firefox.

```


sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

```

Then
```
sudo apt-get install acroread-plugins
```

Regards
Iain

---

### Post by todak on 2008-06-17
```
sudo apt-get install mozplugger
```
will open a pdf right in firefox/iceweasel.

---

