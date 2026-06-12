---
title: "Udisks"
date: 2013-03-09
forum: General Help
---

### Post by Treyonator56 on 2013-03-09
Hey everyone, its been a while since I've been on these forums, but this udisks problem has brought be back. I like to test operating systems using a live disk, and I'm using a netbook so I can't use cd's. That being said, I have to use jump drives. Well, I recently tried using a jumpdrive with startup disk creator, and it doesn't want to format for me. It used to work just fine though. I've tried purging all the config files, and even tried to get udisks 2 to work. Startup disk creator doesn't work with udisks 2 and unetbootin never worked for me. So, my question...how do all my other linux gurus out there doing this? There has to be another program or something to use other than udisks. Any help will greatly be appreciated. 

~Treyonator56~

---

### Post by fantab on 2013-03-09
Udisks2 works fine. Its interface has changed a bit though. To format the drive you have to unmount it first. Alternatively, you can use Gparted.

There is CLI method as well, but that is for later, as it can be risky if we don't know what we are doing.

---

### Post by Treyonator56 on 2013-03-09
is there a gui for udisks2? i have it installed and startup disk creator still fails so I'm assuming I'd have to use the terminal?

---

### Post by fantab on 2013-03-10
In Gnome we have "Disks", formerly called "Disk Utility". I don't know what you have in Lubuntu, but I think you can install 'Disks'.

Have you tried Gparted? Why Not? Don't get stuck with Udisks2.

You can use Windows to format your USB drive then burn your ISO using UNETBOOTIN or any other tool to burn .ISO from Windows.

Or...
[http://www.webupd8.org/2009/10/linux-format-your-usb-drive-via-command.html](http://www.webupd8.org/2009/10/linux-format-your-usb-drive-via-command.html)
[http://ubuntuforums.org/showthread.php?t=1316972](http://ubuntuforums.org/showthread.php?t=1316972)

---

