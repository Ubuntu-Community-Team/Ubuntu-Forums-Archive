---
title: "How to remove unwanted software"
date: 2017-01-15
forum: General Help
---

### Post by cearlp on 2017-01-15
Running 16.10. Installed Able2ExtractPro 11.0 for Ubuntu from investintech.com and found it didn't work. Always starts with Program Error. 
I would like to get rid of it but can find no uninstall program for it.
It installed itself in /opt/investintech and created a sub directory a2ep with bin and other directories.
I did an rm -rf investintech and got rid of everything except it still shows up in the Dash.
Selecting it gives me a main screen but nothing else. 
How do I get rid of it our of the Dash?

---

### Post by &amp;KyT$0P# on 2017-01-16
How did you install it?

---

### Post by vasa1 on 2017-01-16
> **halogen2 said:**
> How did you install it?

I'm guessing it's a deb from [http://www.investintech.com/prod_downloadsa2e.htm](http://www.investintech.com/prod_downloadsa2e.htm)

Looks like a too-good-to-be-true application!

---

### Post by howefield on 2017-01-16
Have a look for the .desktop file in /usr/share/applications/ and delete it.

```
[Desktop Entry]
Version=1.0
Name=Able2Extract Professional Print Dispatcher
Type=Application
Terminal=false
Exec=/opt/investintech/a2ep/bin/Able2ExtractPro.PrnDisp
Icon=a2ep
StartupNotify=true
Comment=Monitors Able2Extract Professional Printer.
MimeType=application/pdf;
```

Deleting directories manually is bound to leave some residual stuff, using..

```
dpkg-deb -c InstallAble2ExtractPro.deb
```

to examine the deb package shows what looks like an uninstall script in ./opt/investintech/a2ep/setup/PCR/PCR.PrnUnInst.sh - perhaps running that script would clean up the uninstall ?

---

### Post by cearlp on 2017-01-16
Thank you howefield. deleting the a2ep.desktop file in .../applications seemed to do the job.
Then I did a find and rm'd everything that had an Able2Extract in it's name.

---

### Post by howefield on 2017-01-16
Cool, glad to hear it.

---

