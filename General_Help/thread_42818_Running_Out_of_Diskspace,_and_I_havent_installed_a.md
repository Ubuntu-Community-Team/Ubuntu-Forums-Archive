---
title: "Running Out of Diskspace, and I havent installed anything!!!"
date: 2005-06-19
forum: General Help
---

### Post by Bandit on 2005-06-19
Hello Everyone,
I got something going on with my Uby 5.04 Linux box that I can not figure out.
Yesterday I was installing some apts (not that many) and this morning I woke up and went to check my email and it started complaining about running out of diskspace..
I have a 80GB MaXtor. Right now I had to delete a few things just to login to Gnome.
It shows I only have 4.21GB left as of now.
I honestly dont have much at all installed....
The only other files I have installed besides the base CD w/Gnome is:
K3B & deps,
NVU
FFox 1.0.4
UT2004
GDesklets 0.35 w/deps..
and about 200MB worth of personal files..
I also installed , GCC, G++, libc (ya know compile tools)
I had all this plus my Oggs and Music videos installed on my SuSE box's and never went about 30GB total usage.
Does anyone have any idea about what is going on??
I thought I could have some cached files from the installs, but I can not find theme.
I would highly appriciate any help.
Thanks,
Joey

---

### Post by Bandit on 2005-06-19
OK, I found out WHAT was taking up so much space.
The folder mysql in /var/log/mysql was taking up 60GB.
Now WHY it was even being used it totaly mystery to me.
I dont have mysql running???
I used rm -dvr mysql and then just re added the dir.
Rebooted and everything seems fine.
I would like to know why this happend incase I run into someone else haveing the same problems.
Thanks,
Joey

---

### Post by afonic on 2005-06-19
Are you sure the mysql server was NOT running on your machine before?

---

### Post by Bandit on 2005-06-19
[QUOTE=afonic]Are you sure the mysql server was NOT running on your machine before?[/QUOTE]
Ya know, it may have been. But what the heck could it have been doing?
I never used MySQL before. I think I just installed it not paying attention last night becuz I had a migrain headache.
Does MySQL require 60GB of space for a log file???
Even when I not using it, installed or not??
Thanks,
Joey

---

### Post by shakin on 2005-06-19
[QUOTE=Bandit]Ya know, it may have been. But what the heck could it have been doing?
I never used MySQL before. I think I just installed it not paying attention last night becuz I had a migrain headache.
Does MySQL require 60GB of space for a log file???
Even when I not using it, installed or not??
Thanks,
Joey[/QUOTE]

It might use that much space if something had gone wrong and it was logging errors.

---

### Post by Bandit on 2005-06-19
[QUOTE=shakin]It might use that much space if something had gone wrong and it was logging errors.[/QUOTE]
Hmm,, thats a thought... Would it log me trying to install some software.
I know i had to go back and forth a few times tring to configure and hunt down dependencies..
Thanks,
Joey

---

### Post by afonic on 2005-06-20
[QUOTE=shakin]It might use that much space if something had gone wrong and it was logging errors.[/QUOTE]
 Exactly. It would not log stuff like installations, but probably a bug somewhere or something you did made it create logs with no stop.

If you don't need it just remove it, as well as apache if you have it installed as well.

---

### Post by Bandit on 2005-06-20
[QUOTE=afonic]Exactly. It would not log stuff like installations, but probably a bug somewhere or something you did made it create logs with no stop.

If you don't need it just remove it, as well as apache if you have it installed as well.[/QUOTE]
Done, this morning when I woke up everything was still working  :) 
Thanks everyone,
Joey

---

