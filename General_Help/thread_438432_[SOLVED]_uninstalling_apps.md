---
title: "[SOLVED] uninstalling apps"
date: 2007-05-09
forum: General Help
---

### Post by fifthwind on 2007-05-09
I've had several cases where I will uninstall an application, and when I reinstall it, it STILL maintains the prior configurations/settings it had before. So, when I remove a program, how do I make sure that it is completely removed including all settings?

Current example of this issue:  I tried out screenlets, and ended up locking it up because I had too many screenlets running at once. So I uninstalled screenlets. But when I reinstall, It still loads all the screenlets I was running before.

I had the same thing happen with firefox. uninstall reinstall doesn't RESET things to some kind of initial or default configuration.

How do I get things back to the initial configuration?

---

### Post by 5-HT on 2007-05-09
You can remove application config files manually (they're usually stored as hidden files in your home directory) or by using a package manager (e.g., Aptitude, Synaptic, etc...)
The following lists some convenient commands for searching for and deleting residual configuration files using Aptitude (APT frond-end). You can also do the same using Synaptic (delete anything in the 'residual' config section).

1)Search for and list all residual config files
```
aptitude search ~c
```2)To remove individual residual configs (and the package if it is installed)
```
sudo aptitude purge <package> 
```3)To remove all residual configs (and the package if it is installed)
```
sudo aptitude purge ~c
```To remove a package and its configuration files concurrently, you can use 'aptitude purge <package>' instead of 'aptitude remove <package>' or, if using Synaptic, select the package for 'complete removal'.

---

### Post by fifthwind on 2007-05-09
Thanks for the reply.

That was an interesting adventure, I learned a lot. Unfortunately it didn't help.

I purged the residual configs. Then ran the search again to verify they were ALL gone... and they were. Then I uninstalled screenlets and verified that no residual configs were left behind... and there was nothing there. Then I even went into var/cache/apts/ and removed the screenlet deb packages, so that on reinstall synaptic would be force to redownload everything from scratch.

Then when I reinstalled screenlets and ran it for the first time, it threw the same widgets onto my desktop in the exact same locations/configurations/settings ect. as I had it with my first install.

With the clean install I'm looking for, it should just sit there and wait for my to configure it (for the first time). Instead it is still somehow remembering the configs from prior installs.

I appreciate your help. I really don't even intend to keep using screenlets anyway. I'm just the kind of person that this is going to eat me up inside until I solve it. :)

---

### Post by mckryptyk on 2007-05-09
You should try your home folder there could be a ".screenlets" (or similar) config folder containing
widget placement information that screenlets uses. 

Also if you go to the screenlets website and examine the "screenlets.tar.gz" download  you will see where it wants to install to and what configs are made. 

Synaptic also will tell you where files are installed to if you look under "package properties" section.

Hope that helps :)

Cheers.

---

### Post by fifthwind on 2007-05-09
Well, I've gained a lot of useful knowledge... 

I found out that most of the things in the Home folder are hidden files, so I went into conf. editor  desktop/gnome/fileviews and showed the files. NOw I can see the config files for almost all my apps. Unfortunately, there was not one there for screenlets. 

I was able to somewhat solve my problem, by identifying which widget was causing the lock up, and then going into user/local/share/screnlets  and deleting the entire folder of the suspect widget (mail notifier). that got rid of the crash issue and screenlets started working again. 

Boy, I'd really like to find where that dang configuration file is... tried everything mentioned, with no luck. Oh, well, the app is working properly now. I'm just going to uninstall it anyway (don't really like the idea of widgets, was just taking them out for a ride :))

thanks for the help guys... maybe I'll learn my way around file locations better in time.

---

### Post by sorcererx84 on 2007-05-10
Your Screenlets config is located in ~/.config/Screenlets

---

### Post by fifthwind on 2007-05-10
sure enough... there it be... now I can sleep.   thanks a bunch!!!!    :)

---

