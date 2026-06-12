---
title: "Uncooperative external harddrive"
date: 2007-06-24
forum: General Help
---

### Post by jexdawg13 on 2007-06-24
I bought a SimpleTech 250GB USB External Hard Drive recently. I love Ubuntu, but it isn't compatible with my printer, my wireless mouse/keyboard, or my music-phone, and I'm tired of fighting it every step of the way. I want to go back to Windows (though only because of compatibility issues - I feel Ubuntu to be far superior).

However, before I deleted everything and began anew, I needed to save all the stuff I don't want to delete. School papers, photos, and whatnot, but most of all my 9 gigs of music files.

I inserted the USB harddrive, turned it on, mounted the drive (/media/simpledrive/) and got to work.

First, I tried to just drag the files into the simpledrive folder like you'd do on windows, for which it is compatible. Locked, failure. I sudo nautilus'd and tried again. Failure number 2. After several similar attempts, I changed my tactics.

I downloaded the ntfs-config package (simpledrive was ntfs) and enabled write-support for external devices. Then I    sudo cp - r ~/Desktop/music /media/simpledrive/ and finally it worked. Kind of. I turned my computer off, disconnected the device and brought it to my sister's Windows computer, hooked it up, and tried to extract my files. They weren't there.

I came back to my computer to troubleshoot. Turned it on. Watched it fail. It had an error that summarizes to "GDM cannot be started. Your harddrive is out of space. Kill yourself or contact your system administrator." Well I was the system administrator and I had no idea what to do. I tried inserting my ubuntu live cd to boot off that, but that didn't work for the same error. I even tried to install windows and it wouldn't allow me to do that, either. I couldn't do anything, even install something else off of a boot cd. I finally tried this: "sudo rm /media/simpledrive/" and that fixed the problem.

What I want is to be able to use this hard drive to save all my music and whatnot... but I don't want to break my computer (again) in the process. Can anyone guide me through the process?

Similar HD to mine (amazon doesn't have exactly the same model): [http://www.amazon.com/SimpleTech-SimpleDrive-250-External-Drive/dp/B0001DYUJ8/ref=sr_1_1/104-3077165-8475929?ie=UTF8&s=electronics&qid=1182701791&sr=8-1](http://www.amazon.com/SimpleTech-SimpleDrive-250-External-Drive/dp/B0001DYUJ8/ref=sr_1_1/104-3077165-8475929?ie=UTF8&s=electronics&qid=1182701791&sr=8-1)

Please help.

---

### Post by eggdeng on 2007-06-24
Might be simpler to use gparted ```
sudo apt-get install gparted
``` to format to FAT and then do your fetching and carrying.

---

