---
title: "[SOLVED] Run command inside terminal from shell script"
date: 2007-12-30
forum: General Help
---

### Post by Super TWiT on 2007-12-30
Is there anyway that when a shell script is executed, it can run the commands in the terminal?

---

### Post by tgilber1 on 2007-12-30
> **Super TWiT said:**
> Is there anyway that when a shell script is executed, it can run the commands in the terminal?

Try "sh -v <scriptname>" #e.g., sh -v myscript

---

### Post by Super TWiT on 2007-12-30
Thanks for responding:KS  I should have been more clear, see I am trying to construct a backup script that will auto run when I plug in my thumb drive.  I have gotten this far. ```
gnome-terminal -e
rsync -a -r -v /home-directory /destination
```
By naming it autorun.sh, enabling it to be run as a program, and enabling Ubuntu to auto run apps, it works.  However, I want to be able to see it in a terminal window, and am not sure how to do that.  gnome-terminal -e isn't showing it in a terminal window.  If I run it all as 1 line, it will say that /home-directory is an invalid argument.

---

### Post by dagnabit dang doohickey on 2007-12-30
Use quotes:
```
gnome-terminal -e "rsync -a -r -v /home-directory /destination"
```
There may be a way to keep the window open after the command completes, but I don't use gnome-terminal so I can't be sure. (xterm has the -hold option and xfce4-terminal has the -H option.)

---

### Post by Super TWiT on 2007-12-30
Thank you!  This is exactly what I needed!  It works!!  I have been trying to get this to work all day.  Thank you tgilber1 and dagnabit dang doohickey for participating in this form.  These forums are awesome!

---

