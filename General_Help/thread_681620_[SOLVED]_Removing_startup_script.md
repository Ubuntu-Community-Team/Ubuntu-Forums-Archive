---
title: "[SOLVED] Removing startup script"
date: 2008-01-29
forum: General Help
---

### Post by dynamethod on 2008-01-29
Hey there ive used this info to create a startup script of KNetworkAnalyzer

[http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/)

but ive dont want it to run at boot anymore, so i deleted the script in /etc/init.d

however i noticed in the link above how it says to run sudo update-rc.d whatever defaults, is there something i should do after deleting a script to remove or undo whatever that sudo update-rc.d does?, thanks

---

### Post by doddo on 2008-01-29
In etc there are some folders with scripts in them which runs under different runlevels. 

If you removed the file from /etc/init.d, then it might be a good idea to also remove those links. It wont harm if you keep them there, but I feel that after a while you get lots of stuff in those folders, and its best to keep those folders as nice and tidt as possible.

just enter one of those directories (relative to /etc)
```

rc0.d/    rc2.d/    rc4.d/    rc6.d/    rcS.d/    rc1.d/    rc3.d/    rc5.d/ 

```
and an ls -l will show which files link back to the removed file. They will brobably be red. The link will probably appear in more than one of those folders

---

### Post by dynamethod on 2008-01-29
ah sweet ty, i just notcied though, there was a couple in called K20whatever, which i could remove with rm, but theres some in other rc* directories that start with s20 but i cannot remove? it says that theres no such file as s20whatever, but its right there infront of me after a 'ls' lol?

---

### Post by doddo on 2008-01-29
Hmm 

The "whatever" corresponds with the name of the script you removet, right ;D

it strikes me as strange that you can not remove a file which you can see... but And I am not at my Ubuntu box ATM so I can not investigate that further...

---

### Post by dynamethod on 2008-01-29
Heres the copied text within konsol too which i mean:

me@home:/etc/rc2.d$ ls
README                       
S20apmd           
S89anacron
S05vbesave                   
S20apport         
S89atd
S10acpid                     
S20hotkey-setup   
S89cron
S10powernowd.early           
S20kde-guidance   
S90binfmt-support
S10sysklogd                  
S20makedev        
S98usplash
S10xserver-xorg-input-wacom  
S20nvidia-kernel  
S99acpi-support
S11klogd                     
S20powernowd      
S99rc.local
S12dbus                      
S20rsync          
S99rmnologin
S12hal                       
S20TrafficA       
S99stop-readahead
S13kdm                       
S20wireless
S19cupsys                    
S24dhcdbd
me@home:/etc/rc2.d$ rm s20TrafficA
rm: cannot remove `s20TrafficA': No such file or directory
me@home:/etc/rc2.d$


^ s20TrafficA being the file im trying to delete

EDIT, i just noticed what i was doing wrong, the font appeared to be lowercase for the 's', it was actually uppercase 'S' lol my bad

---

### Post by doddo on 2008-01-30
Oh I see! bummer! 
Great that the problem is resolved!!! :KS

---

