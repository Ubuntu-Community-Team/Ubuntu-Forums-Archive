---
title: "pls help me make game server auto start"
date: 2013-09-23
forum: General Help
---

### Post by keiko112 on 2013-09-23
i am not so good in linux and stugle very to make a game server auto start after reboot 
the comand i have to use is this ./Start.sh dm i think its the space beetwen .sh dm beqause i have added in init.d but it will not start 
when i run the comand manualy its work can some one pls help me :)

---

### Post by cariboo on 2013-09-23
I moved this to General Help, and made the title of the thread more descriptive, as the thread title as it was, would make our members just pass it by, as we see so many threads with the same title.

---

### Post by CaptainMark on 2013-09-23
Add it to your crontab with the @reboot option, here is a guide [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by XBNCPRk on 2013-09-23
Was the game servers start script marked as executeable after being put in the init.d folder?

---

### Post by keiko112 on 2013-09-23
yeap it have the premissions :) i will try to add it to crontab :) ty all for respons and ty for moving my missposted post :)

---

