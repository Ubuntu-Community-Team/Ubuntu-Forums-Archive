---
title: "Cannot get past login passward"
date: 2016-01-13
forum: General Help
---

### Post by lelovely7315 on 2016-01-13
Hi There, I cannot go pass my password input on my Laptop. I turn the laptop on it comes up asking for my password like normal, I put the password in and it is correct. Then the laptop goes back and asks for my password again. And it will do this over and over again. I am running an Asus laptop with Ubuntu 14.04.3 LTS, it has been running just fine for over a year, then it started this password problem. Does anyone have any ideas on how to fix my problem?                Thanks Larry

---

### Post by Cabalbl4 on 2016-01-14
What desktop environment to you use? Do you use lightdm at login? If so, can you switch to tty using Ctrl+Alt+F1 .. F7 and login there?
If you can login there then there is a problem with desktop environment
If you can not login using tty then try to reset password (use this tutorial to se how [http://linuxconfig.org/ubuntu-14-04-lost-password-recovery](http://linuxconfig.org/ubuntu-14-04-lost-password-recovery) ), UPD use [COLOR=#111111][FONT=Consolas]**passwd your_user_name** [/FONT][/COLOR]instead of just passwd as in tutorial

---

### Post by lelovely7315 on 2016-01-15
Hi  there, I tried what you said and it didn't work. The only thing I can do is get into the command line and I don't know what to do from there. I know if I can get into the CMOS I can check the password or change it and see if that works. So does anyone have any ideas??:(

---

