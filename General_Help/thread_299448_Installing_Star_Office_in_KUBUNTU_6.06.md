---
title: "Installing Star Office in KUBUNTU 6.06"
date: 2006-11-14
forum: General Help
---

### Post by mishranurag on 2006-11-14
I was trying to install star office in KUBUNTU 6.06. For those who do not know it is free for students.  I downloaded the installer file from Sun's website which was so-8-pp3-bin-linux-en-US.sh.  I used the command sudo sh so-8-pp3-bin-linux-en-US.sh

The installer started and after accepting the license agreement and stuff, it failed and gave me following errors as log file. Does any body have any idea or suggestions?

Installing StarOffice
        Log file: /var/opt/sun/install/logs/StarOffice_install.B11140730
Installed: /opt/staroffice8/uninstall_StarOffice.class
Uninstaller is at: /opt/staroffice8/uninstall_StarOffice.class

Installing  Base module

Installing RPM: staroffice-core01

Error: RPM staroffice-core01 install failed}.
Install complete. Package: staroffice-core01

Uninstalling /opt/staroffice8/./setup
rpm: Skipping rpm remove of staroffice-agfafonts, not installed.
rpm: Skipping rpm remove of staroffice-ooofonts, not installed.
rpm: Skipping rpm remove of staroffice-gnome-integration, not installed.
rpm: Skipping rpm remove of staroffice-core10, not installed.
rpm: Skipping rpm remove of staroffice-core09, not installed.
rpm: Skipping rpm remove of staroffice-core08, not installed.
rpm: Skipping rpm remove of staroffice-core07, not installed.
rpm: Skipping rpm remove of staroffice-core06, not installed.
rpm: Skipping rpm remove of staroffice-core05u, not installed.
rpm: Skipping rpm remove of staroffice-core05, not installed.
rpm: Skipping rpm remove of staroffice-core04u, not installed.
rpm: Skipping rpm remove of staroffice-core04, not installed.
rpm: Skipping rpm remove of staroffice-core03u, not installed.
rpm: Skipping rpm remove of staroffice-core03, not installed.
rpm: Skipping rpm remove of staroffice-core02, not installed.
rpm: Skipping rpm remove of staroffice-core01, not installed.
rpm: Skipping rpm remove of staroffice-suse-menus, not installed.
rpm: Skipping rpm remove of staroffice-desktop-integration, not installed.
rpm: Skipping rpm remove of staroffice-lngutils, not installed.
rpm: Skipping rpm remove of staroffice-fonts, not installed.
rpm: Skipping rpm remove of staroffice-gallery, not installed.
rpm: Skipping rpm remove of staroffice-javafilter, not installed.
rpm: Skipping rpm remove of staroffice-xsltfilter, not installed.
rpm: Skipping rpm remove of staroffice-graphicfilter, not installed.
rpm: Skipping rpm remove of adabas-13.01.00, not installed.
rpm: Skipping rpm remove of staroffice-math, not installed.
rpm: Skipping rpm remove of staroffice-base, not installed.
rpm: Skipping rpm remove of staroffice-impress, not installed.
rpm: Skipping rpm remove of staroffice-draw, not installed.
rpm: Skipping rpm remove of staroffice-calc, not installed.
rpm: Skipping rpm remove of staroffice-writer, not installed.
Uninstalling /opt/staroffice8/./setup
rpm: Skipping rpm remove of staroffice-agfafonts, not installed.
rpm: Skipping rpm remove of staroffice-ooofonts, not installed.
rpm: Skipping rpm remove of staroffice-gnome-integration, not installed.
rpm: Skipping rpm remove of staroffice-core10, not installed.
rpm: Skipping rpm remove of staroffice-core09, not installed.
rpm: Skipping rpm remove of staroffice-core08, not installed.
rpm: Skipping rpm remove of staroffice-core07, not installed.
rpm: Skipping rpm remove of staroffice-core06, not installed.
rpm: Skipping rpm remove of staroffice-core05u, not installed.
rpm: Skipping rpm remove of staroffice-core05, not installed.
rpm: Skipping rpm remove of staroffice-core04u, not installed.
rpm: Skipping rpm remove of staroffice-core04, not installed.
rpm: Skipping rpm remove of staroffice-core03u, not installed.
rpm: Skipping rpm remove of staroffice-core03, not installed.
rpm: Skipping rpm remove of staroffice-core02, not installed.
rpm: Skipping rpm remove of staroffice-core01, not installed.

.... 
MyResources:summaryPanel-More-Information:
MyResources:summaryPanel-Log-File-Location-Notice

---

### Post by mishranurag on 2006-11-14
Any help?

---

### Post by taurus on 2006-11-14
Why not use OpenOffice!!!

---

### Post by tminuszero on 2006-11-14
Make sure you have RPM support installed. I think you may have to install alien and rpm.

So do this:

```
sudoapt-get install rpm alien
```

Then do this:

```
sudo mkdir /var/lib/rpm
sudo rpm --initdb
```

Then go about installing again and see if there's a problem. There may be a java issue, but hopefully it will work :)

---

### Post by tminuszero on 2006-11-14
I agree with Taurus re: Open Office as well. It works automatically!

---

### Post by mishranurag on 2006-11-14
From what I understand Star Office is a better version of Open Office, isn't it?

---

### Post by tminuszero on 2006-11-14
Better *how*? The only difference, I see is that StarOffice has the Adabas database component, more premade document templates & converters, and clipart included.

For the database component (MS-Office Equivalent: Access), Open Office has the OpenOffice Database. 

If you install Automatix you can install "OpenOffice Clipart" which works great for clipart.

Document templates  & converters - I think that's where StarOffice wins.

---

### Post by mishranurag on 2006-11-14
O ok. I didn't know these much details. I just thought...

---

### Post by tminuszero on 2006-11-14
I would say install both and try them both out. It can't hurt :)

---

### Post by Cable on 2006-11-14
I installed it after installing alien from the repo's and it worked perfectly, no need for the rpm package.

---

### Post by mishranurag on 2006-11-15
I followed the steps given by tminuszero and it worked perfectly.  Thank you. One thing is for sure. StarOffice loads quicker than openoffice.

Anurag

---

### Post by karamba_kid on 2006-11-15
Don't forget>> KOffice 1.6 is also avalible for (k)ubuntu dapper. [http://kubuntu.org/announcements/koffice-16.php](http://kubuntu.org/announcements/koffice-16.php)

---

