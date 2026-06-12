---
title: "Help :("
date: 2007-08-12
forum: General Help
---

### Post by UK-Wobbie on 2007-08-12
Help i installed  iTunes on wine and it did not work! And now i can not unstill it lmfao :(
When i go to unstill a block window pops up and then wine crash... Any one?? 
Do any one no how to delete wines registry to this iTunes? So i can delete the files? :)

Thanks

---

### Post by gobbles414 on 2007-08-12
UK,

Your post is a bit vague. Are you trying to use the iTunes uninstaller or the Wine Software Uninstaller. You should use the Wine Software Uninstaller. On my system, it is located in System Tools.

---

### Post by UK-Wobbie on 2007-08-12
> **gobbles414 said:**
> UK,

Your post is a bit vague. Are you trying to use the iTunes uninstaller or the Wine Software Uninstaller. You should use the Wine Software Uninstaller. On my system, it is located in System Tools.

I had a go on the Wine Uninstaller and the iTunes uninstaller they do the same thing.. Black Window then Wine crash! I had to keep restarting my pc to get Wine working..
I done all to have a go on getting iTunes of my pc! I had a go instill a old v of iTunes to see if that fix it! But had no luck :(

Thanks

---

### Post by zach12 on 2007-08-12
itunes does not work in ubuntu well sorry.
i would use Songbird or if you have 512mb ram or more try vmware or vbox (VirtualBox)
sorry
ps vbox is faster but you need a installer cd or dvd of windows to use it.

---

### Post by gobbles414 on 2007-08-12
Make sure that Wine is emulating either Windows 2000 or XP. You can do that by going into winecfg, which is located in System --> Administration. Alternatively, you can launch the utility from terminal.

Do you mind losing any other Windows programs you have installed? If not, you can remove Wine in a special way. When you reinstall Wine, iTunes will be gone. Here is what you'll need to type in terminal:

sudo apt-get --purge remove wine

It may interest you to know that a newer version of Wine will be made available to you if you enable backports in System --> Administration --> Software Sources. BTW, it's a good idea to check [here]("http://appdb.winehq.org") before installing programs in Wine.

---

### Post by UK-Wobbie on 2007-08-12
> **gobbles414 said:**
> Make sure that Wine is emulating either Windows 2000 or XP. You can do that by going into winecfg, which is located in System --> Administration. Alternatively, you can launch the utility from terminal.

Do you mind losing any other Windows programs you have installed? If not, you can remove Wine in a special way. When you reinstall Wine, iTunes will be gone. Here is what you'll need to type in terminal:

sudo apt-get --purge remove wine

It may interest you to know that a newer version of Wine will be made available to you if you enable backports in System --> Administration --> Software Sources. BTW, it's a good idea to check [here]("http://appdb.winehq.org") before installing programs in Wine.

Thanks i give that a go,
I been on a website what shows you how to instill iTunes on Wine.. But it looks like it do not work!! :)
Here [http://www.frankscorner.org/index.php?p=itunes6](http://www.frankscorner.org/index.php?p=itunes6)

---

### Post by UK-Wobbie on 2007-08-12
> **UK-Wobbie said:**
> Thanks i give that a go,
I been on a website what shows you how to instill iTunes on Wine.. But it looks like it do not work!! :)
Here [http://www.frankscorner.org/index.php?p=itunes6](http://www.frankscorner.org/index.php?p=itunes6)

Dam  I have instill 
iTunes 6.0.5 on Wine and it Worked :( Only if i did that at the start then instilling a more new one :( lol

---

### Post by gobbles414 on 2007-08-12
UK,

You probably know this already, but I don't think that you can access the iTunes Music Store with anything less than iTunes 7. I recommend Banshee as an alternative to iTunes in Linux.

---

