---
title: "Adode reader install"
date: 2008-04-30
forum: General Help
---

### Post by vineline on 2008-04-30
I wanted to download and install Adobe Reader 8 on my Ubuntu 7.1 installed computer.  I down loaded a 47meg  linux file from Adobe's web site and tried to install. It would not install as it was the wrong version. The file had a rpm extension.

How do I get the correct version of Adobe and what extension should I be looking for both for Adobe reader and any other application I may download in the future?

---

### Post by ibutho on 2008-04-30
You need to go to the Adobe website and click on the link to download Adobe Reader. You will then need to click on the "different language or operating system" link and choose Linux as the OS and for the Linux Installer, choose Linux x86 deb. You can then install the deb file using dpkg e.g. "sudo dpkg somepackage.deb" or if you have gdebi installed, you can just double click on the deb file.

---

### Post by Monicker on 2008-04-30
> **vineline said:**
> I wanted to download and install Adobe Reader 8 on my Ubuntu 7.1 installed computer.  I down loaded a 47meg  linux file from Adobe's web site and tried to install. It would not install as it was the wrong version. The file had a rpm extension.

How do I get the correct version of Adobe and what extension should I be looking for both for Adobe reader and any other application I may download in the future?

Try this page:

[http://www.adobe.com/products/acrobat/readstep2_allversions.html]("http://www.adobe.com/products/acrobat/readstep2_allversions.html")

Under "Select an Installer", scroll down and choose the .deb package.

```
sudo dpkg -i file.deb
```

---

### Post by ebozzz on 2008-05-17
Does anyone know if there is a 64-bit versions available?

---

### Post by ebozzz on 2008-05-17
> **ebozzz said:**
> Does anyone know if there is a 64-bit versions available?

I found my answer. By installing the Medibuntu repository, acroread was available for me to install.

---

