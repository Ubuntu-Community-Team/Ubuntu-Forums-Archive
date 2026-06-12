---
title: "Spideroak will not run after install"
date: 2015-06-28
forum: General Help
---

### Post by Stephen_Wright on 2015-06-28
Spideroak will not run after install. I'm running Ubuntu 15.04 and installing the file found here [https://spideroak.com/getbuild?platform=ubuntu&arch=x86_64]("https://spideroak.com/getbuild?platform=ubuntu&arch=i386"). Seems to open and install without an issue in Software Centre. I've tried reinstalling and uninstalling and purging every remaining Spideroak file from my drive with reboots before installing again. [http://ubuntuforums.org/showthread.php?t=1682602](http://ubuntuforums.org/showthread.php?t=1682602) does not seem to apply any more. The .Spideroak folder is never created in my home folder.

Updated: It seems I managed to copy the wrong link. I never tried to install the 32-bit.

Help would be appreciated.

---

### Post by Vladlenin5000 on 2015-06-28
What happens when you start it in the terminal?
```
SpiderOak
```
And, unless you're running a 32-bit installation you should install the 64-bit package...

---

### Post by Stephen_Wright on 2015-06-28
To my surprise it runs when I type it with the caps like you wrote it. Thank you! However, I'm left with a terminal I can't close.

---

### Post by Stephen_Wright on 2015-06-28
Well, I found and installed 'screen' then used Ctrl+a+d so I can then close the terminal and leave SpiderOak running. I still think it should run from the launcher like any other program and would like to know if it is somehow a problem with my Ubuntu installation or is a careless bug on the part of SpiderOak that is the cause of this problem.

---

### Post by Stephen_Wright on 2015-06-28
I had trouble before with SpiderOak and also did not get any help from SpiderOak support at that time, but I see now I have the following in my notes which I think worked without a problem in the past. I've yet to try uninstalling and reinstalling with this method.

wget -O spideroak.deb "https://spideroak.com/directdownload?platform=ubuntulucid&arch=x86_64"
sudo dpkg -i spideroak.deb
sudo apt-get -f install
SpiderOak --setup=-

---

