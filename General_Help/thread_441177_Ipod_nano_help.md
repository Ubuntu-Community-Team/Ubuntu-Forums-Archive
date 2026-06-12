---
title: "Ipod nano help"
date: 2007-05-12
forum: General Help
---

### Post by zedi123 on 2007-05-12
Hi, i need some help with my ipod nano connecting to ubuntu. Iv read all the forums and i cant find an answer to my problem.
When i first connected my ipod it ran good but after transferring one song it went wierd. Now it cant be read by programs like rythmbox or gtkpod.
It shows up on the desktop but the permissions have changed i think. It wont let me write to the ipod and iv tried the chmod thing in terminal but doesnt do anything.
This is what it says in gtkpod:

Could not open "iTunesDB.ext" for reading extended info.
Extended info will not be used.
iPod Database Import Failed: 'iTunesDB '/media/ZEDI'S IPOD/iPod_Control/iTunes/iTunesDB' corrupt: mhsd expected at 368837.'

help plz...

---

### Post by strabes on 2007-05-12
Just delete everything off of the ipod (with SHIFT+DELETE) and then use gtkpod to recreate the iPod's directories and recopy all your music onto it. It looks like your database is corrupt or something.

---

