---
title: "Installing EnvyNG for Nvidia Card."
date: 2008-06-05
forum: General Help
---

### Post by Vigh on 2008-06-05
Hi, I downloaded EnvyNG Core, installed it, how exactly do I open the program now. I want to download drivers for my Gainward GeForce 8800GT 512MB, also how do I bring up a list of hardware from the terminal? Cheers Vigh

---

### Post by iaculallad on 2008-06-05
Use this [page]("http://www.albertomilone.com/nvidia_scripts1.html") to guide you through the process of your driver installation.

---

### Post by Vigh on 2008-06-05
sudo apt-get install envyng-gtk as stated in the guide doesnt work, neither does uninstall envyng

---

### Post by iaculallad on 2008-06-05
If you're following this [guide]("http://www.albertomilone.com/envyngfaq.html#A"), try enabling the "Universe" repository first as stated before installing it.

Navigate to System->Administration->Software Sources, You must be on the "Ubuntu Software" tab, check your Main, Universe, Restricted, and Multiverse. Uncheck "Installable from CDROM/DVD" if checked. Click on close button.

Open your terminal (One command at a time):

> sudo apt-get update && sudo apt-get upgrade

> sudo apt-get install envyng-gtk

---

### Post by Vigh on 2008-06-05
How do I enable Universe? I know it has something do to with synaptic package manager.

---

### Post by Vigh on 2008-06-05
Universe is already enabled.

---

### Post by iaculallad on 2008-06-05
> **Vigh said:**
> How do I enable Universe? I know it has something do to with synaptic package manager.

Look at my last post.

---

### Post by Vigh on 2008-06-05
Its says downloadable from server australia, how do I download Universe.

---

### Post by Vigh on 2008-06-05
Okay something happening now.

---

### Post by iaculallad on 2008-06-05
> **Vigh said:**
> Its says downloadable from server australia, how do I download Universe.

You don't download "Universe", that's a repository. And change your download server to point to "Main Server" (that's under the "Ubuntu Software" tab). Click on close button. Open up your terminal and re-issue the commands below one at a time:

```
sudo apt-get update && sudo apt-get upgrade
```

```
sudo apt-get install envyng-gtk
```

---

