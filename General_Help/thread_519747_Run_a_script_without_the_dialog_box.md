---
title: "Run a script without the dialog box"
date: 2007-08-07
forum: General Help
---

### Post by yanewby on 2007-08-07
I have written a small bash script that I would like to keep accessible on my Desktop.

When I double-click the script to run it a dialog box pops up asking me "Run in terminal", "Display", "Cancel" or "Run".

I would like to bypass this box and have it "Run" every time.

How do I do this?

---

### Post by g2g591 on 2007-08-07
Does it have permission to execute?

---

### Post by yanewby on 2007-08-07
I have right-clicked the file and chosen Properties->Permissions and checked the execution box there but I still get the dialog box.

---

### Post by rainwalker on 2007-08-07
You could try creating a launcher in your panel insted of putting it on the desktop, I don't know if that will make a difference though. The only reason I think it might work is because I've always been able to run custom scripts and stuff my making launchers in the panel rather than double-clicking them on the desktop

---

### Post by brennydoogles on 2007-08-07
> **rainwalker said:**
> You could try creating a launcher in your panel insted of putting it on the desktop, I don't know if that will make a difference though. The only reason I think it might work is because I've always been able to run custom scripts and stuff my making launchers in the panel rather than double-clicking them on the desktop

Yup, creating a launcher on the desktop or the panel is your best bet. where it says command, simply put ```
sh /path/to/script.sh
``` or if it needs root access ```
sudo sh /path/to/script.sh 
``` or if you want to use BASH specifically (in case it is not your default shell: ```
bash /path/to/script.sh
``` That should do it!!

---

### Post by rainwalker on 2007-08-07
In the path, you don't have to put the "sh", it can just be > /path/to/script

---

### Post by yanewby on 2007-08-07
Thanks brennydoogles and rainwalker!

Creating a launcher in my panel and dragging it onto my desktop worked.

---

