---
title: "[SOLVED] Removal of Spybot S&amp;amp;D"
date: 2007-10-31
forum: General Help
---

### Post by mike g on 2007-10-31
I tried this question in the, Instillation/update, area and received no answers, so I will try it here.

I want to upgrade to gutsy from feisty and have Spybot S&D installed.  I attempted to remove it since I did not get an answer in my earlier post but it appears to have only partially removed.  There are still several places Spybot is listed when running the "whereis" request.

Do I have to remove the program to upgrade?  Did I do myself damage by attempting to remove it and not getting, what appears to be, complete removal?  If I need to remove "all" the Spybot references, what is the easiest way to do this?

                                          OR

Will I be able to upgrade and as before, the upgrade will get rid of what is no longer needed?

---

### Post by por100pre1 on 2007-10-31
Try using Wine uninstaller:

```
uninstaller
```

---

### Post by ubuntu27 on 2007-10-31
SPybot Search & destroy is for WIndows Operating System.

GNU/Linux Operating system such as Ubuntu dosn't get infected with Viruses, Worms, and other malware. So you do not need to install any Antivirus.

[Ubuntu Security article]("http://www.psychocats.net/ubuntu/security")

Now, yes. It is better if you remove those programs before you upgrade.
Even ebtter will be if you just make a backup (hard copy) of your files into a CD or DVD. En then do a fresh install of UBuntu Gutsy.

[How to upgrade to Gutsy from Feisty]("http://www.ubuntu.com/getubuntu/upgrading")


[How to protect your Ubuntu bo]("http://ubuntuforums.org/showthread.php?t=510812")x (and diferences between WIndwos security and Ubuntu security)

---

### Post by mike g on 2007-11-01
Thanks for the info on the uninstaller, used it but it still did not remove Spybot S&D listings in several areas, such as, home directory/ wine/ drive_c/shared........and other similar files.

I attempted to run the uninstaller again and Spybot S&D was no longer listed but the portions of the program are still in the same areas.  

Any further suggestions.

Thanks

---

### Post by ubuntu27 on 2007-11-01
> **mike g said:**
> Thanks for the info on the uninstaller, used it but it still did not remove Spybot S&D listings in several areas, such as, home directory/ wine/ drive_c/shared........and other similar files.

I attempted to run the uninstaller again and Spybot S&D was no longer listed but the portions of the program are still in the same areas.  

Any further suggestions.

Thanks

You can run Nautilus (GNOME's file browser) as root and delete those files manually. Programs installed with Wine are not really "installed" 
So in order to unistall you can just delete those programs files in Wine.


open the terminal, and type

```
gksu nautilus
```


And Nautilus will be executed as root (admin mode). Careful to not delete anything vital to the system.

---

