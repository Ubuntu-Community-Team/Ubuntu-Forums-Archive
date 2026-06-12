---
title: "Help with AVG for Linux"
date: 2007-02-04
forum: General Help
---

### Post by SirPaPa on 2007-02-04
Hello, I'm needing help with [COLOR="Red"]AVG[/COLOR] for Linux.
I dual-boot with XP and read somewhere that is smart to use some sort of AV becuase of that. When I launch [COLOR="Red"]AVG[/COLOR] for Linux and try to update it I get the attached error message. Is there anyone that can help me with this? 
  Thank,you.

---

### Post by DeadEyes on 2007-02-04
The opt folder is owned by root.It may be that you don't have the right permissions. try running avg as root when you want to do an update.

---

### Post by SirPaPa on 2007-02-05
> **DeadEyes said:**
> The opt folder is owned by root.It may be that you don't have the right permissions. try running avg as root when you want to do an update.

I'm sorry but I thought that when I login is as root. Can you explain please I'm fairly new to linux.:confused:  
     
      Thank,you.

---

### Post by budgie9 on 2007-02-05
USe the Terminal window and type the following to update AVG.
sudo avgupdate -o 
That is not a zero.
The program will update for you.

---

### Post by SirPaPa on 2007-02-05
Thank,you budgie9 [COLOR="Red"]AVG[/COLOR] successfully updated seems like. Another thing , it can't scan my ./ folder. Is this a Ubuntu(Linux) security measure? Because I would like to be able to scan everthing. Thanks again.

---

### Post by go_beep_yourself on 2007-11-19
If it is a permission error, then you can scan everything with this command.

gksu avggui &

---

### Post by go_beep_yourself on 2007-11-19
If it is a permission error, then you can scan everything with this command.

gksu avggui &

---

### Post by go_beep_yourself on 2007-11-21
Has anyone had this problem?

[http://img214.imageshack.us/img214/5953/screenshotavgforlinuxwoco2.png](http://img214.imageshack.us/img214/5953/screenshotavgforlinuxwoco2.png)

---

