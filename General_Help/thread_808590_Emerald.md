---
title: "Emerald"
date: 2008-05-26
forum: General Help
---

### Post by SIXAXIS on 2008-05-26
Sorry to make another thread here, but now I got a theme to work in Emerald. I used "emerald --replace" and now I have no window borders (X button, minimize, maximize, etc.)

---

### Post by Happy_Man on 2008-05-26
Are you using Compiz Fusion (sorry, but it needs to be asked)? Are you using the version provided in the Ubuntu repos, or one that was compiled from source or from git?

---

### Post by Forlong on 2008-05-27
> **SIXAXIS said:**
> Sorry to make another thread here, but now I got a theme to work in Emerald. I used "emerald --replace" and now I have no window borders (X button, minimize, maximize, etc.)
Did you run it via [Alt]+[F2]?

---

### Post by tommyhakinen on 2008-05-27
i am having this issue as well. It might be some compatibility issue when using emerald and compiz fusion at the same time.

---

### Post by njumlin on 2008-05-27
I believe I have the same problems as described above. I have attached a screenshot of the weird rendering. System is Ubuntu 7.10 upgraded to 8.04 TLS. Beryl is selected as window manager and Emerald is choosen as window decorator. I did a testrun with compiz-chec and it went all OK. But clearly I'm still having troubles :-(

Any advice is GREATLY appreciated.

---

### Post by v.man on 2008-05-27
I had the same problem.  I uninstalled Emerald and am just using GTK 2.0 themes now - with zero issues.

---

### Post by SIXAXIS on 2008-05-27
I installed the compiz from the repos. I didn't do that when I had 7.10, maybe that's the problem?

---

### Post by overdrank on 2008-05-27
> **SIXAXIS said:**
> I installed the compiz from the repos. I didn't do that when I had 7.10, maybe that's the problem?

HI and if you have CCSM install then you may check to ensure that the window decorations is checked.

---

### Post by njumlin on 2008-06-13
Hi, 
I'm not using CCSM. I have beryl installed, but I checked to see if window decorations was selected - and it was. Any other suggestions?

---

### Post by ad_267 on 2008-06-13
What do you mean by you have beryl installed? How did you install this? Beryl has been replaced by compiz-fusion which is installed by default in hardy. You shouldn't have installed anything except compizconfig-settings-manager to customize your compiz settings.

Edit: Try installing fusion-icon to change window decorators, it works for me.

---

### Post by Nullack on 2008-06-13
I dont use the icon as I find it clutters up my GUI

You see if you type in the terminal "emerald --replace &" even though youve backgrounded the task as soon as the terminal is closed you loose your window decorator......This is why you have no window decorations

They key is to open a new terminal, do your emerald command, hit alt+f2 to get a run dialog, close the terminal, then run your emerald command *from* alt+f2. This way emerald will "stick" for that session

---

### Post by Forlong on 2008-06-13
If you have Beryl installed, Emerald won't run with Compiz, because Beryl's version of Emerald is not compatible with Compiz.

---

### Post by benjaminjames on 2008-06-17
bump im getting this problem too, also if i run the emerald replace command then close the terminal the window borders disapear(same prob i know but hear me out) then if i untick window decoration then retick it my borderws come back but emerald theme manager doesnt work(as in i click on a theme and nothing happens) wtf is this all about any help guys?

---

### Post by Forlong on 2008-06-17
Do not run ```
emerald --replace
``` in the terminal but via [Alt]+[F2]

---

### Post by ad_267 on 2008-06-17
Also, if you want to permanently enable emerald you can use the compizconfig-settings-manager and set the window decoration command to "emerald --replace"

---

