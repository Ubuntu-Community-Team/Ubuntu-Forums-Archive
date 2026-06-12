---
title: "need help with permissions!"
date: 2007-06-11
forum: General Help
---

### Post by fflarex on 2007-06-11
Alright, so I'm pretty sure I just completely F'ed up all the permissions on my system. After looking for tutorials on linux permissions for hours and finding next to nothing, I just decided to try a few things and see if it worked. So  I ran the following:

cd /media/disk
sudo chmod -R a+rwx /

Now I can't even use the sudo command, and when I log in to ubuntu it tells me my &HOME/.dmrc file was ignored or something and needs 644 permissions. All my applications are messed up, and the past 2 weeks I've spent trying to get my system switched over to linux 100% seems like it might have been ruined in about a half second.

Is there a way to quickly undo or fix all this?

EDIT: I'm just an idiot, plain and simple. I'm going to reinstall.

---

### Post by nbayiha on 2007-06-12
hej Dude you can fix it just doing this  in the terminal. U don;t have to reinstall your system for that


```
sudo chmod 644 /home/nbayiha/.dmrc
sudo chown nbayiha /home/nbayiha/.dmrc
sudo chmod -R 700 /home/nbayiha
sudo chown -R nbayiha /home/nbayiha
```

PS: ofcourse you replace nbayiha by ur name.

---

### Post by rgustbee on 2007-06-12
I had the same problem and nbayiha's solution fixed the problem for me! Thanks

---

### Post by darkmaster on 2007-07-08
This solved my same problem too, I really thank you. I had this problem because I shared with samba my entire home dir and then setted its permission so that anyone could be able to modify its contents... to be able to write on this folder from another PC. Maybe it should be interesting to write on a FAQ that this hasn't to be done since a lot of ex-windows users will surely try to do this. In Win it is only normal to share anything. Security doesn't even exist in Windows, pratically...

---

