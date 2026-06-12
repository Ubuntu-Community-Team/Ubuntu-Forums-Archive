---
title: "Error Opening Synaptics Package Manager"
date: 2007-05-30
forum: General Help
---

### Post by skubisnack on 2007-05-30
Earlier today, I attempted to install VirtualBox in Feisty, but it hung up for over an hour.  I canceled the installation.  SPM would not close, so I rebooted.  After reboot, I attempted to open SPM again and got a message that I needed to run "dpkg --configure -a".  I did so, and and now i get the following message when I open SPM:

E: The package virtualbox needs to reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

I have attempted to reinstall VirtualBox and get the message:

Could not open 'VirtualBox_1.3.8_Ubuntu_feisty_i386-4.deb
This package may be corrupted or you are not allowed to open the file.  Check the permissions on the file.

I should mention that when I download the installer, I am choosing the "open with" option.  I have cleared cache and re-downloaded.

I'm fairly new to linux and I'm at a complete loss as to how to fix this.  I can't install anything now, including updates.

Thanks,
Greg

---

### Post by zvacet on 2007-05-31
```
sudo dpkg --configure -a
```

---

### Post by skubisnack on 2007-05-31
I had already done this.  I just did it again, and I get the same message about reinstalling virtualbox.

---

### Post by cisforcojo on 2007-05-31
How are you removing the cache and how are you uninstalling VirtualBox?

---

### Post by skubisnack on 2007-05-31
I removed the cache in Firefox so that I could download a fresh copy of virtualbox.  I am not able to get into SPM at all, so I can't uninstall virtualbox.  It also never completed the install.  It just says that it needs to be reinstalled.

---

### Post by biohypnotix on 2007-05-31
I am in no way an expert, actually I am a dumb newbie. I had the same problem w/ virutalbox last night after trying to install it. I tried all the commands and tricks that others suggested when I searched these forums for an answer but none worked. I freaked out thinking I might have to totally do a fresh install of Ubuntu Feisty. So I turned to Google before resorting to a fresh install and it actually helped me. I found a command that worked for my machine BUT like I said I'm not expert and I haven't rebooted yet although I am able to open Synaptic and Update Manager again with no errors.

Brute force uninstall I am guessing. Use command at own risk!

sudo dpkg --remove --force-remove-reinstreq virtualbox

---

### Post by leopard6661 on 2007-05-31
I had the same thing after installing second life and after a lot of trials I had a very good advice and here is how it worked
In the terminal type:
```
sudo dpkg --remove --force-remove-reinstreq virtualbox
```


It worked for me, hopefully it will work for you[-o<

---

### Post by skubisnack on 2007-05-31
Thanks everybody!  The command:

sudo dpkg --remove --force-remove-reinstreq virtualbox

worked.  I have rebooted and all is well.

---

