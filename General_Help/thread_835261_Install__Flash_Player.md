---
title: "Install  Flash Player"
date: 2008-06-20
forum: General Help
---

### Post by Dave Otter on 2008-06-20
I am trying to watch ITV Catch up but it says I must download Adbe Flash Player.I have done this and downloaded  install_flash_player_9_linux

   How do I now proceed

---

### Post by Pjotr123 on 2008-06-20
Do this, for 100 % multimedia support:

Step 1:
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)

Step 2:
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)

---

### Post by Nepherte on 2008-06-20
No offence, but on the two pages you gave you can't find anything about flash.

You can easily install flash as follows:
```
sudo apt-get install flashplugin-nonfree libflashsupport
```

The above is the easiest way, but it seems you have already downloaded the flashplayer from adobe's site. You can unpack the archive and run the installation file:
```
cd the_directory_where_you_unpacked_the_archive
sudo ./nameofinstallfile
```

---

### Post by Pjotr123 on 2008-06-20
> **Nepherte said:**
> No offence, but on the two pages you gave you can't find anything about flash.

My how-to most certainly does install Adobe Flash Player as well: it's namely in ubuntu-restricted-extras.  :-)

---

### Post by Nepherte on 2008-06-20
My bad :)

---

