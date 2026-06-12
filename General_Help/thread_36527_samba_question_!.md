---
title: "samba question !"
date: 2005-05-23
forum: General Help
---

### Post by hiptrop on 2005-05-23
hi ! 

i got a little problem concerning samba ! 

 10 min ago everything worked ! i have a windows desktop pc and a linux ubuntu laptop and i used nautlius  for windows and linux comunications ( folders that where given free in a network ! ) 

well ... i did a update  ... a samba update was included too ... and now ... the folders from my windows pc are not there anymore :( 

can you help me out with that problem please ? 

i am pretty new to samba so any kind of help could be useful :) 

thanks alot !!!

---

### Post by Zelut on 2005-05-23
Have you restarted since you updated Samba?  I didn't try to use my network right after the update but I know I have restarted since & everything is working.

Just for starters you can give that a try (if you haven't) and we'll see what we need to do after that if it doesn't solve anything.

---

### Post by hiptrop on 2005-05-23
well that was the first thing i did :) i even restarted my windows pc :) did not help :( 

maybe you know some other things i could try ?  ;-)

---

### Post by Zelut on 2005-05-23
Well my first guess would be to make sure samba is running at all.  

to start samba:
sudo /etc/init.d/samba start (or restart)

Also try this command:

sudo dpkg-reconfigure samba-common

that will reconfigure the samba settings (in case anything was corrupted during the update).

---

### Post by hiptrop on 2005-05-24
i did as you said and it did not help :( thanks alot but do you have other ideas too ? 

 O:)

---

### Post by hiptrop on 2005-05-24
mhmhm i don't know whats going on ... suddenly it works again !!!

i did not change anything ... 

well ! for now it works ! hope it will for longer :P 

maybe you can tell me what the problem could be that it sometimes works and sometimes not :( 

all in all thanks alot for the help !!

---

