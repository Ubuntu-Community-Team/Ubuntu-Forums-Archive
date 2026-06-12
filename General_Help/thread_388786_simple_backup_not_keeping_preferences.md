---
title: "simple backup not keeping preferences"
date: 2007-03-19
forum: General Help
---

### Post by space2k on 2007-03-19
I'm having a funky little problem with simple backup config, and I'm looking for help. After I first installed it, I thought that I new better and I decided to select "Manual Backup Only". Later on, I decided I had better things to worry myself with, and wanted to switch back to "Use recommended backup settings", but when I switch back, it's not saving my preferences. 

Here's the scenario:
* Open Simple Backup Config.
* On the "General" tab - "Manual backups only" radio button is selected.
* I click "Use recommended backup settings", "Save", then "Close".
* Re-open Simple Backup Config to confirm, and "Manual only..." is selected again...

what gives?

thanks to anyone that can help!

:confused:

---

### Post by Repabil on 2007-03-20
I used Simple Backup for a while and ran into the same problem. So I chose to use [backup-manager](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=backup-manager) instead.

---

### Post by dannyboy79 on 2007-03-20
i use sbackup. I have switched from incremental to manual and back again. I have always clicked on multiple tabs though, I wonder if that has anything to do with it? like maybe before hitting save, make the change to default method, then open other tabs to make sure everything is as you wish, so on and so forth. I can maybe help, you know the config file for this program is kept in /etc/, it's name is sbackup.conf, I think. maybe you should open it up before you try to change anything, save a copy as another name, then open the gui and change some stuff, then hit save after clicking on some tabs and actually moving around in the gui, then open /etc/sbackup.conf again and see whats different, this will tell you that your settings are saving. 

I don't  have this problem so I am not sure, when you do it, it is asking you for a password right? maybe your simple-backup-config button is opening the gui with sudo privalages? good luck.

---

