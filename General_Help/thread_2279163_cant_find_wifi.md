---
title: "cant find wifi"
date: 2015-05-21
forum: General Help
---

### Post by thedoctor818772 on 2015-05-21
I am using Ubuntu 15.04 on an Acer Aspire M laptop. This morning I just updated my box and upon restarting it found that I now can no longer see my wifi network or any of the neighbors, and am not sure what to do about this. Help please. Thanks,

Michael Dykes

---

### Post by thedoctor818772 on 2015-05-21
I tried the command   sudo service network-manager restar   but nothing happened.

---

### Post by thedoctor818772 on 2015-05-21
The update in question was to the linux kernel.

---

### Post by dino99 on 2015-05-21
then boot to the previous working one ;)
today i have already seen a user complaining that the latest 3.19 kernel have (mistakingly) dropped some modules (wait for a fix)

---

### Post by thedoctor818772 on 2015-05-21
How exactly do i do this again? Forgive my ignorance.

---

### Post by thedoctor818772 on 2015-05-21
I tried pressing and holding SHIFT but that did not work to open grub.

---

### Post by ajgreeny on 2015-05-21
Does that laptop use UEFI?
If so you may need to keep tapping Esc at boot to get the grub menu, but different machines seem to make it hard and if you have only Ubuntu installed, you may need to make some changes to the /etc/default/grub file in order to ever see grub; I have to do that.
Here's the appropriate lines of my file with a few extra lines commented out that I added as an "aide-memoire" to myself showing in red.
```

GRUB_DEFAULT=0
[COLOR=#ff0000]#Next line will make the countdown time show menu by default[/COLOR]
#GRUB_TIMEOUT_STYLE=menu
[COLOR=#ff0000]#Next line changed from 0 to 2 for 2 second delay[/COLOR]
GRUB_HIDDEN_TIMEOUT=0
[COLOR=#ff0000]#Next line changed from true to false to allow delay countdown to show[/COLOR]
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR="Xubuntu-14.04"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
 
```

---

### Post by thedoctor818772 on 2015-05-22
Thanks I was able to get into grub and revert to a previous version of the linux kernel. Now my machine can see my wifi network and connect to it. Thanks again.

---

