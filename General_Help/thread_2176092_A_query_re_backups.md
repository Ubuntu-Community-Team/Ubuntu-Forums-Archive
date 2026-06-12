---
title: "A query re backups"
date: 2013-09-22
forum: General Help
---

### Post by Mal_Ellis on 2013-09-22
I am using 'Backup' to backup my files to a usb stick once weekly. Am using Lubuntu 12.04 Gnome . My query is this: if I do an install of Ubuntu 12.04 can I use the usb stick to restore my files to Ubuntu 12.04 using 'Backup restore'. How can I transfer all my current programs to the Ubuntu OS or would I have to restore them manually eg KMymoney, Scribus, Backup etc

---

### Post by david98 on 2013-09-22
Here's some link's iv'e just been giving about backing up program's hope they are as helpful to you as they were to me.
[URL="http://ubuntuforums.org/showpost.php?p=7157175&postcount=5"]
http://ubuntuforums.org/showpost.php...75&postcount=5[/URL]

[http://kevin.vanzonneveld.net/techbl...selectupgrade/]("http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/")

---

### Post by Mal_Ellis on 2013-09-22
Thankyou David98 . Looks promising . Will get on to it shortly.

---

### Post by Mal_Ellis on 2013-09-23
If I do a backup putting it into the /tmp directory would that not be wiped out upon doing a new install. Does this mean that I would have to put the /tmp/dpkglist.txt into another medium like an external CD or DVD then bring it back when I have completed the new install.

---

### Post by stinkeye on 2013-09-23
> **Mal_Ellis said:**
> If I do a backup putting it into the /tmp directory would that not be wiped out upon doing a new install. Does this mean that I would have to put the /tmp/dpkglist.txt into another medium like an external CD or DVD then bring it back when I have completed the new install.
One guides says to save to /tmp/dpkglist.txt and then include that location in your normal backups.
Can save it to your normal backup location with the initial command be that another drive, partition or usb.
eg I use another drive (and also copy to my ubuntuone folder)....
```
sudo dpkg --get-selections > /media/Data/BUPS/Raring/my_applications/dpkglist.txt
```

---

### Post by SeijiSensei on 2013-09-24
Anything written to /tmp will be destroyed at the next boot.  Put files you want to keep in your home directory.

---

### Post by Mal_Ellis on 2013-09-24
Thank you all for your help. I have resolved the problem but not really as I had desired.  
I put the /dpkglist.txt onto a USB stick, did a complete new install of Ubuntu 12.04 then took the /dpkglist.txt back to /tmp directory.  Then following instructions 1/2/3 and it reinstalled everything. Took about 4 hours and when it was completed my computer would not start up again . I ended up reinstalling 12.04 again and manually installihng all the programs I require. As an aside I think the instructions for getting the /dpkglist.txt back onto the HDD is a fine idea. Is there some way that you could go through all the programs and delete the ones you don't want back in the new installation . My one picked up the old Lubuntu OS which was one thing that I did not require and I think that this lead to my computer not restarting.

---

### Post by stinkeye on 2013-09-25
> **Mal_Ellis said:**
> Thank you all for your help. I have resolved the problem but not really as I had desired.  
I put the /dpkglist.txt onto a USB stick, did a complete new install of Ubuntu 12.04 then took the /dpkglist.txt back to /tmp directory.  Then following instructions 1/2/3 and it reinstalled everything. Took about 4 hours and when it was completed my computer would not start up again . I ended up reinstalling 12.04 again and manually installihng all the programs I require. As an aside I think the instructions for getting the /dpkglist.txt back onto the HDD is a fine idea. Is there some way that you could go through all the programs and delete the ones you don't want back in the new installation . My one picked up the old Lubuntu OS which was one thing that I did not require and I think that this lead to my computer not restarting.
While your installing manually create your own install script for your next fresh install..
eg last time I installed all the applications I use I created a **new-install.sh** script so next time I can just run the script.
```
#!/bin/bash

sudo apt-get install man2html synaptic easystroke kupfer guake conky-all xdotool wmctrl numlockx curl glipper lm-sensors hddtemp w3m ffmpeg keepassx artha p7zip-full p7zip-rar shutter gdebi vlc smplayer cairo-clock gnote gcolor2 compizconfig-settings-manager sox libsox-fmt-all
```

---

### Post by Mal_Ellis on 2013-09-25
A good idea thanks for that .

---

