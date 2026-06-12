---
title: "Firefox and Thunderbird"
date: 2016-12-17
forum: General Help
---

### Post by Jack_Shankle on 2016-12-17
Thanks for any help.
Mind I know just enough about Ubuntu Mate to be dangerous.

On wiffies computer we use Gmail. 
I find that Firefox and Thunderbird are bad programs.
I would like to uninstalled them on her computer.
I'm afraid doing that might mess up something else.
What is your advice.

---

### Post by howefield on 2016-12-17
Uninstalling those applications shouldn't cause anything bad to happen.

Using the command line eg..
```
sudo apt purge firefox thunderbird
[sudo] password for hugh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libdbusmenu-gtk4 linux-headers-4.8.0-22 linux-headers-4.8.0-22-generic linux-image-4.8.0-22-generic
  linux-image-extra-4.8.0-22-generic
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED
  firefox* thunderbird* thunderbird-gnome-support* thunderbird-locale-en* thunderbird-locale-en-us*
0 to upgrade, 0 to newly install, 5 to remove and 80 not to upgrade.
After this operation, 217 MB disk space will be freed.
Do you want to continue? [Y/n] 
```

you can see which packages will be uninstalled.

Alternatively you should be able to use the Software Centre to uninstall if you prefer the GUI.

Which release of Ubuntu Mate are you using ?

---

### Post by Jack_Shankle on 2016-12-17
Thank you very much Howefield,
I used the Software center and was able to uninstall
Firefox and Thunderbird.
Since I am Sudo ignorant I stayed away from that.
I was able to access Gmail with no problem.

Mate version: Mate desktop environment 1.12.1

---

### Post by howefield on 2016-12-17
Cool, glad you got it, feel free to mark the thread as solved if you wish.

---

