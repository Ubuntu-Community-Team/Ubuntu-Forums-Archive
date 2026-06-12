---
title: "Folder Disappeared. Need help to restore/recover"
date: 2008-01-23
forum: General Help
---

### Post by blastfm on 2008-01-23
I know this has been asked several times before, but I tried searching around the forum and couldn't get anything that could help me :(

I'm using Feisty Fawn and using ext3 fs. I seem to have lost a folder (/home/*myusername*/My_Pictures) which contained mostly wallpapers, icons, and digital image stuff I created or edited.

The last time I had access to this folder was 3 days ago. I was working on some files from this folder, shutdown the computer, turned off the power to the AVR and power strip, and left. 2 days later, i turned my computer back on and it was gone. I'm pretty sure I did not delete this folder (about 99.8% sure, i may have pressed delete and looked away) but I couldn't find it anywhere, hidden or in the trash can. 
- I tried searching for the files inside the folder and nothing came up 
- I tried booting up with the live CD and XP and still nothing. 
- I ran fsck using a live CD and got a message about 10% non-contiguous space found, but nothing was recovered after
- I checked the space utilization (Disk Usage Analyzer) and found around 800MB unaccounted for, which is approximately the size of the missing folder.

Is there anything I can do to recover the missing folder and files, or is it bye-bye (good thing the real valuable contents of this folder had a back up)? 

If not, is there a way for me to recover the diskspace at least?

Also since this folder contained the personalized icons, I couldn't get the AWN Manager to open. I found somewhere that this is because there were launchers with missing icons, and all I have to do was delete the .awn and .config/awn folders but that didn't work.

Lastly, aside from me (no one else has access to this PC) stupidly deleting the folder, what other factors could have caused this issue? The hard drive is relatively new (6 months old) and fsck does not  report any damage or bad sectors, and as far as I know, no mal-ware (from the XP partition) is present on the system. I'm worried this might happen to other files and folders on my PC in the future, if it hasn't already.
 
BTW, it would really be nice if you can provide a solution that would not require me to connect to the Internet, since this particular PC is currently located at home and I just moved and my DSL connection wont be available for at least 2 more weeks.

Thank you so much for your help.

---

### Post by sumguy231 on 2008-01-23
If it's anywhere, it might be in the lost+found directory at the top of the filesystem it was on. Unlikely though unless you've gotten any filesystem errors.

---

### Post by blastfm on 2008-01-24
YES!... I am stoopid.](*,)

I found the "missing" folder in .Trash-root folder. Not sure how it got there but I guess when I was logged in as root to fix something with the access of some files, I clicked on the Del button on the keyboard.

Oh well. Thanks anyway :-)

---

