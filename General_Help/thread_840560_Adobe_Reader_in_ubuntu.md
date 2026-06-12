---
title: "Adobe Reader in ubuntu"
date: 2008-06-25
forum: General Help
---

### Post by hosseinrostamzadeh on 2008-06-25
Hi Everybody!
How can I run Adobe Reader(already insatled) in ubuntu?
More info: 
I have downloaded Adobe reader as rpm package, installed Adobe reader via **sudo alien -i ....** and everything seemed to be ok. But now I don't find where its executable file lies. I have tried every possible name combination in a terminal, but I get "command not found". I have checked installation by synaptic and there exists an installed version of AdobeReader-enu. But can not find/run it.
Any help is appreciated.
:)

---

### Post by fooman on 2008-06-25
the adobe reader is "acroread" in linux.

so in a terminal, try:

```
acroread
```

---

### Post by mempman on 2008-06-25
I would not recommend alien, because converting from *.rpm to something else won't result in the most stable software.

However, if you are wanting to read pdfs in linux, there are many many options...such as ePDFViewer-which works well-among many.

---

### Post by Nepherte on 2008-06-25
The normal command to start adobe reader is acroread. You could have installed adobe reader a lot easier. It is located in the medibuntu repository: [http://www.medibuntu.org/](http://www.medibuntu.org/)

---

### Post by lswb on 2008-06-25
There is also a .deb install available from adobe.com; If you go to adobe.com and click on the link to download adobe reader, it does recognize that linux is running and immediately offers an .rpm file. However, ff you click on the link for "other operating system", then click on linux, you get a choice of installers, including debian. Download the .deb file to the desktop and just double-click, or from terminal type dpkg -i whatever_the_package_name_is.

---

### Post by hosseinrostamzadeh on 2008-06-25
Tried it and Then I get error message : "permission denied",
Thanks for the answer!

---

### Post by mempman on 2008-06-25
> **hosseinrostamzadeh said:**
> Tried it and Then I get error message : "permission denied",
Thanks for the answer!


That is because you aren't super user, and you account isn't allowed to install.
Try "sudo dpkg -i package-name"

---

### Post by hosseinrostamzadeh on 2008-06-25
Tried it and Then I get error message : "permission denied",
Thanks for the answer!

---

### Post by hosseinrostamzadeh on 2008-06-25
> **lswb said:**
> There is also a .deb install available from adobe.com; If you go to adobe.com and click on the link to download adobe reader, it does recognize that linux is running and immediately offers an .rpm file. However, ff you click on the link for "other operating system", then click on linux, you get a choice of installers, including debian. Download the .deb file to the desktop and just double-click, or from terminal type dpkg -i whatever_the_package_name_is.
Thanks, it worked!

---

### Post by hosseinrostamzadeh on 2008-06-25
After a new downloading of *.deb version of Adobe Reader the problem is solved!
thanks!

---

