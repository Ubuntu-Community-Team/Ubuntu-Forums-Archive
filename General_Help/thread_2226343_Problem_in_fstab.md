---
title: "Problem in fstab?"
date: 2014-05-26
forum: General Help
---

### Post by vlado2 on 2014-05-26
hello, 


my xubuntu 14.04 freezes after 2 or 3 hours with no activity ?¿?¿?¿ when the computer is being used there is no problem.


may be because there is no swap partition? 


or may be due to some settings in the fstab file? 


see something wrong with this line of fstab? 


192.168.1.2/server /media/server cifs user=admin,password=password,user,rw,exec,async,nounix,uid=1000,gid=1000,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

Thanks a lot!!

---

### Post by Toz on 2014-05-26
Hello and welcome to the forums.

Can you explain in more detail what happens when your computer "freezes"? 
- Is the screen blank?
- Is the mouse cursor stuck?
- Any messages on the screen?

I don't think its because the lack of a swap file (I don't have one either) or your fstab entry.

---

### Post by vlado2 on 2014-05-27
First, thanks for the help 

what happens after 2 o 3 hous with no inactivity is that neither the upper or the lower panel panel work because as if you could not read the hard drive (i think) (only the item "places" into upper panel work)


and for example if I run in a terminal the thunar command can not navigate in the "standard folders" Video, documents, desktop, etc ... 


but if I create a folder, for example, called "try" I can get into it. 


when I try to enter, for example, in the folder /media/ the thunar hangs and no longer responds and in the terminal I get this error 


(thunar: 6884): GLib-CRITICAL **: Source ID 1261 was not found When attempting to remove it 


can someone help? 


Thank you!

---

