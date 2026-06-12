---
title: "Can't Find App to Uninstall it"
date: 2022-09-04
forum: General Help
---

### Post by rafiqcombrinck on 2022-09-04
Hi All

Yeah this is a weird one for me, I'm no expert but I thought at this point I knew enough to do something as simple as uninstalling an app, but this has me stumped.

I installed an app from a local supplier, via script, and it's been running perfectly but I want to repurpose the machine so want to remove the app. Problem is I can't find it anywhere. I've tried checking via APT, dpkg, Software Manager, Synaptic and even checked for a service (service --status-all) but can't find any reference of it anywhere.

Any ideas?

PS. I tried opening the script to see where it installed to but it's not readable.

Thanks,
R

---

### Post by QIII on 2022-09-04
Hello.

What's the app?  Who maintains it?  Can you post the text of the script at pastebin.ubuntu.com?

---

### Post by rafiqcombrinck on 2022-09-04
It's a VMS by CathexisVision. The script is 1.2Gb and not "plaintext".

I RDP'd onto the machine and noticed there were shortcuts on the Desktop which I found pointed to a folder in /usr. 

Does this mean the app is runs in like a "standalone state"? Can I simply remove the folder to get rid of it? If something is run in this fashion, how can you find/monitor it?

Thanks,
R

---

### Post by QIII on 2022-09-04
If you don't have a system monitor, top and htop can let you find it and give you some information about its cpu and memory use.  For applications other than system processes, you might even be lucky enough to see exactly which directory it lives in.

It is often the case that things that install to /usr/bin/whatever can be "uninstalled" by removing their directory.  But you have to be careful not to delete something else unintentionally.  Doing that does not remove any user settings/config, which may have to be removed as well.

---

### Post by rafiqcombrinck on 2022-09-04
Thanks, using htop it shows the various processes running and showed a partial file location. In this case I knew where it was but how would you normally tell if it just shows as ./whatever?

I see the app stores some configs in a hidden folder in the home directory. I don't suppose there is a way to search for all related files/configs, is there?

---

### Post by ActionParsnip on 2022-09-04
Do you have a link to the place you downloaded the script from, please?

---

### Post by ActionParsnip on 2022-09-04
RDP'd to the machine? Did you setup xrdp or is this a Windows server?

---

### Post by rafiqcombrinck on 2022-09-05
[https://cathexisvms.com/](https://cathexisvms.com/)

Ok so I was using the RDP term a little loosely, it's a VM so I accessed it via the host's http console :P

---

### Post by ActionParsnip on 2022-09-05
If you rerun the installer, is there an uninstall option?
If you run:
```

cd /usr/nvr
ls

```
Is there an uninstaller there?

---

### Post by rafiqcombrinck on 2022-09-05
No uninstall option in either.

---

### Post by ActionParsnip on 2022-09-05
Have you contacted the developers.
[https://cathexisvms.com/contact-us/](https://cathexisvms.com/contact-us/)

---

