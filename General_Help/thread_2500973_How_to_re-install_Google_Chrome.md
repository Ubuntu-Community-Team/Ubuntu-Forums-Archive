---
title: "How to re-install Google Chrome"
date: 2024-09-18
forum: General Help
---

### Post by satimis on 2024-09-18
Hi all,

Ubuntu 24.04

From time to time, warning popup advises me to re-install Chrome.

I found following link:
How to Install Google Chrome on Ubuntu 24.04
[https://www.liberiangeek.net/2024/04/install-google-chrome-ubuntu-24-04/](https://www.liberiangeek.net/2024/04/install-google-chrome-ubuntu-24-04/)

Please advise whether it works.  Alternatively are there other suggestions?

Thanks in advance.

Regards

---

### Post by howefield on 2024-09-18
Should work, if I want Chrome I use apt install for the installation though, just preference.

```
wget -P /home/hugh/Downloads/ https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb && sudo apt install /home/hugh/Downloads/google-chrome-stable_current_amd64.deb 
```

---

### Post by satimis on 2024-09-18
> **howefield said:**
> Should work, if I want Chrome I use apt install for the installation though, just preference.

```
wget -P /home/hugh/Downloads/ https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb && sudo apt install /home/hugh/Downloads/google-chrome-stable_current_amd64.deb 
```
Hi@howefield.

Thanks for your advice.

I would try your version to re-install Google Chrome.

Do I need to uninstall the running Google Chrome first ?

Regards

---

### Post by howefield on 2024-09-18
I would, but I do not understand why you are not getting an update through the package manager, do you not have the google chrome repository in your system?

---

### Post by ActionParsnip on 2024-09-18
+1 for the wget command. You can get fancy and add the repo and key manually, but the deb does all that for you :)

---

### Post by satimis on 2024-09-18
> **howefield said:**
> I would, but I do not understand why you are not getting an update through the package manager, do you not have the google chrome repository in your system?
Hi@howefield,

I have run periodically;
$ sudo apt update ; sudo apt upgrade
```

........
Calculating upgrade... Done
Get more security updates through Ubuntu Pro with 'esm-apps' enabled:
  libcjson1 libavdevice60 ffmpeg libpostproc57 libavcodec60 libavutil58
  libswscale7 libswresample4 libavformat60 libavfilter9
Learn more about Ubuntu Pro at https://ubuntu.com/pro
The following upgrades have been deferred due to phasing:
  file-roller python3-distupgrade ubuntu-pro-client
  ubuntu-pro-client-l10n ubuntu-release-upgrader-core
  ubuntu-release-upgrader-gtk
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.

```
It doesn't show that Google Chrome needs to update/upgrade

Regards

---

### Post by dragonfly41 on 2024-09-18
Look in .. sudo synaptic .. search google .. to see status.

---

### Post by satimis on 2024-09-18
> **dragonfly41 said:**
> Look in .. sudo synaptic .. search google .. to see status.
Hi@dragonfly41,

Whether you meant on Terminal running following command one by one

$ sudo synaptic
$ search google

?

Regards

---

### Post by dragonfly41 on 2024-09-18
Sorry, I shot from the hip while in a busy moment.

[1] Launch Synaptic Package Manager GUI (you might need to install it first if not in use) either through terminal (sudo synaptic) or Top left of desktop toolbar > Activities > Synaptic.

[2] Use Search button top right in Synaptic GUI and search google-chrome

[3] See google-chrome-stable (a least that is what I see)

[4] Right click on google-chrome-stable for options and properties.

---

### Post by satimis on 2024-09-18
> **dragonfly41 said:**
> Sorry, I shot from the hip while in a busy moment.

[1] Launch Synaptic Package Manager GUI (you might need to install it first if not in use) either through terminal (sudo synaptics) or Top left of desktop toolbar > Activities > Synaptic.

[2] Use Search button top right in Synaptic GUI and search google-chrome

[3] See google-chrome-stable (a least that is what I see)

[4] Right click on google-chrome-stable for options and properties.
Hi@dragonfly41,

I have Synaptic Package Manager installed
1) Start Synaptic Package Manager
2) Search google-chrome

Search result : no package selected

It is very strange.

Regards

---

### Post by dragonfly41 on 2024-09-19
Then it must be snap installation.

[https://snapcraft.io/chromium](https://snapcraft.io/chromium)

---

