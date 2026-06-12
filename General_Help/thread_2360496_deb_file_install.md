---
title: "deb file install"
date: 2017-05-05
forum: General Help
---

### Post by angel mike on 2017-05-05
Trying to install a Epson Scanner driver but the download file 'iscan-bundle-ubuntu-16.04-1.3.19.x86.deb.tar.gz ' with gdebi gives an error report  that it is not a deb file.

---

### Post by howefield on 2017-05-05
Do you have a link to the file ?

---

### Post by ajgreeny on 2017-05-05
That is because it is a tar.gz file, ie the equivalent in Windows speak to a zip file; you need to extract the .deb file from.it and use that, not the archive itself.

---

### Post by coffeecat on 2017-05-05
@angel mike, that's a tar.gz you've downloaded which contains the deb file. Unpack the tar.gz with right-click -> extract here. Now open the folder that is created, then (probably) the core folder, and you will find the .deb file inside which will open with gdebi.

Before you do that though, a word of caution. I recently installed the drivers for an Epson XP-245, and the iscan-bundle didn't work for me, but I can't remember the details now. What did work was a file named imagescan-bundle-ubuntu-16.04-1.3.20.x64.deb.tar.gz which I got from this page: [http://download.ebz.epson.net/dsc/search/01/search/](http://download.ebz.epson.net/dsc/search/01/search/) . Or rather, several pages in after I had put in my printer model number. Chances are that yours may be the same, but try that page before you try installing the scanner bundle you have.

What is the model number of your Epson?

Tip - after you install the scanner bundle with driver, you need to reboot before it will work.

---

### Post by angel mike on 2017-05-05
Thanks all for the speedy replies - did unpack the tar.gz and used the site given in the link by coffeecat. Will have another try but not holding my breathe. Have a V39 Perfection.
Thanks

---

