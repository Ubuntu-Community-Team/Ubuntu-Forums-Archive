---
title: "I guess i messed up with permissions when i was upgrading ubuntu from disc"
date: 2013-01-24
forum: General Help
---

### Post by Batoussai on 2013-01-24
So... since ubuntu 12.04 was getting me plenty of problems about my gpu i decided to give 12.10 a try... 
So i got my 12.10 Live-CD, booted it up and run the installer, i choose to upgrade ubuntu on the installer menu and when i was setting up my acc I made the (ridiculously stupid) mistake of putting a different password for my acc. And since my /home was encrypted, now i can't log in on my acc (just as guest).
 
When i try to log from lightdm it shows the 4 first lines saying that some services had started i guess (it's just too fast to read), and then it shows the log in screen once again.

If i try to log in using gdm it goes to a screen with my wallpaper and them shows a error box saying:
"Could not update ICEauthority file /home/<myusername>/.ICEauthority"

This problem with ICEauthority makes me think that the problem is with the permissions, anyway, i tried chown <myusername> /home/<myusername> and nothing seems to have changed.



Annnnd, since my home is encrypted i can't get my files out and format the partition because i did (the even more stupid) mistake of letting the sheet of paper were I took note of the decryption key inside my drawer and it got lost cause the sheets in there were used to print things '-'

Any ideas of what can i do? (besides loosing all my data and overwrite the /home)

---

### Post by elgordodude on 2013-01-25
> **Batoussai said:**
> Annnnd, since my home is encrypted i can't get my files out and format the partition because i did (the even more stupid) mistake of letting the sheet of paper were I took note of the decryption key inside my drawer and it got lost cause the sheets in there were used to print things '-'

This is a worrisome line, because if your directory was encrypted with a different password then your user, and was complex enough that it was stored on printer paper... well, it's probably gone... sorry...

But if you just need to recover the lost account, the easy way is to use grub. Hold SHIFT to pull up the menu at boot, select recovery mode, select root prompt or something similiar it's near the bottom, then ```
passwd *username*
``` where username is your actual username. You may then enter a new password and start fresh. If you get a cannot lock error use ```
mount -o remount,rw /
``` and try again.

Good luck

---

### Post by Batoussai on 2013-01-30
Hey, i managed to find my old password and used " ecryptfs-mount-private " as root to mount my old home and backup the files,  after that I reinstalled ubuntu and everything is working just fine.

---

