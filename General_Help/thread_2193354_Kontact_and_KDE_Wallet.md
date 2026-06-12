---
title: "Kontact and KDE Wallet"
date: 2013-12-12
forum: General Help
---

### Post by linuxnewbie3 on 2013-12-12
Hi there,
I used Thunderbird as my E-Mail client but I wanted to switch to KMail in combination with Kontact beacause the Kontact overview fits better to my kind of organisation than Thunderbird with Plugins like Lightning.

I installed Kontact and tried setting it up myself but I gues I made some mistakes. Therefore I deinstalled the programm and reinstalled it. But my changes remain.

Most annoyingly is KDE Wallet. It asks for my KDEWallet password about every 30 minutes.

-How can I delete all my setting, so that I can install a "clean" version of contact?
-Why do I even need KDEWallet? Is it possible to dont have this service. I just need KMail to automatically remember my passwords like Thunderbird does.

---

### Post by SeijiSensei on 2013-12-12
KDE applications like KMail use the wallet for stored passwords.  You can manage your wallet from System Settings.

---

### Post by linuxnewbie3 on 2013-12-12
I use Ubuntu. I dont see any options in my system settings in there. Now I installed Kwalletmanager but this doesnt open.

EDIT: Can anybody tell me how I COMPLETELY delte alle Kontact and Kdewallet files, with all my settings and stuff so that I can have a clean reinstall

---

### Post by SeijiSensei on 2013-12-13
```
sudo apt-get purge kontact
sudo apt-get purge kwalletmanager
```

You should consider trying Kubuntu if you prefer Kontact and other KDE applications.  In my experience, running GTK applications like Thunderbird on KDE works more smoothly than running KDE applications on GNOME systems like vanilla Ubuntu or Lubuntu.

If you want to take Kubuntu for a spin, you can [download the appropriate ISO here]("http://cdimage.ubuntu.com/kubuntu/releases/13.10/release/").

---

