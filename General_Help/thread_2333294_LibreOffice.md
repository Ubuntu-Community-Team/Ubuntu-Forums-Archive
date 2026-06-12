---
title: "LibreOffice"
date: 2016-08-08
forum: General Help
---

### Post by shane_faulkinbury2 on 2016-08-08
I was curious about LibreOffice 5.2.0.4  I downloaded it from LibreOffice's website because Ubuntu Software gives no information on what version you will download.  The problem is when I click on the .deb files it opens Ubuntu Software and I click to install it and it says installing for like 5 seconds and then it says install again.  Is there a problem with it or is it because I'm on VPN?  It might be that I already have it since I run the sudo apt-get update everyday when I log on.  Can someone please give me an update on this?  :confused:

---

### Post by Linuxisfast on 2016-08-09
Libreoffice is provided by Canonical, its not advisable to download deb file. In case you want latest, use Libreoffice PPA.

---

### Post by claracc on 2016-08-09
Please, see [http://tipsonubuntu.com/2016/08/03/libreoffice-5-2-released-how-to-install/](http://tipsonubuntu.com/2016/08/03/libreoffice-5-2-released-how-to-install/).

It is recommended to install the libreoffice ppa for ubuntu 16.04, and from it, to install the new libreoffice release.

Deb files method is not recommended in this case.

---

### Post by howefield on 2016-08-09
> **shane_faulkinbury2 said:**
> ... Ubuntu Software gives no information on what version you will download. 

Scrolling down to the Details section should reveal the version number or use apt-cache show packagename in the terminal.

---

### Post by speartip on 2016-08-09
If you read the "read me" file that comes with the official LibreOffice packages, you will find the easiest way to install LO is to enter the folder containing all the .debs, open a terminal, and issue the command:
```
sudo dpkg -i *.deb
```
You will need to do this for all 3 of the archives you have downloaded, after you have extracted the folders. (the help pack & language pack are the other 2)

ps. To get more information about the official packages you are installing in Ubuntu, try using synaptic rather than the software centre.

---

### Post by sgage on 2016-08-09
That said, I had no trouble installing, and now using daily, LO 5.2 from the debs at their website. Didn't even know there was a PPA to get the latest version.

---

### Post by shane_faulkinbury2 on 2016-08-10
Thanks guys!  I really appreciate the info!

---

