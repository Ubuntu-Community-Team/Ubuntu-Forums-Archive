---
title: "Trouble installing hp c5180 printer on new ibm t41"
date: 2008-01-29
forum: General Help
---

### Post by mrufino1 on 2008-01-29
Hi, I just got an ibm t41 yesterday and 7.10 installed without a hitch. However, I am not able to install my printer, either manually or using hp's installer. I have used their installer successfully on 2 other machines in my house- the printer is running on my wireless network. When running the installer, it is saying I am missing dependencies, but it won't install them. I also tried installing them manually using sudo apt-get install, as suggested in a similar topic that I found when searching, but it said I already had what I needed. Here is the error I get on install, any ideas?

Running 'sudo apt-get install --yes --force-yes build-essential python2.5-dev libcupsys2-dev cupsys-bsd libusb-dev libtool libjpeg62-dev openssl libsnmp9-dev python-qt3 python-reportlab libsane-dev python-imaging libsane'
Please wait, this may take several minutes...
[COLOR="Red"]error: Package install command failed with error code 100[/COLOR]

Thanks, I would really appreciate the help, I am not sure why this is not working.

---

### Post by mrufino1 on 2008-01-29
In case others search for the same issue, it was solved by doing:
apt-get install libsnmp-dev

Then the HP installer worked and the printer is working great. If anyone can explain this I'd love to know, because I didn't have to do it on my other machines, but it is working now so I am happy.

---

