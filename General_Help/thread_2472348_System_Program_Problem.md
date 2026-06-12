---
title: "System Program Problem"
date: 2022-02-24
forum: General Help
---

### Post by mugwump40 on 2022-02-24
Every time I log into Ubuntu Mate, I get a warning message "System Program Problem Detected".  It asks me to 'Report" or "Discard".  What System log should I be looking at to find the problem, or does anyone know why I get this?  I dismiss it and everything works fine.  It's just an annoyance and a question "why?"

---

### Post by deadflowr on 2022-02-24
System Problem Detected usually means a crash report was generated, 
crash reports are located in /var/crash.
So I would check there.

You should be able to turn the message off if you want.
In dconf editor (if installed) look at com > ubuntu > update-notifier.
There is a setting for show apport crashes.
You can toggle it to off.
Or run the command line option
```
gsettings get com.ubuntu.update-notifier show-apport-crashes
```
to see the current value
and set it to false with
```
gsettings set com.ubuntu.update-notifier show-apport-crashes false
```
This setting, of course does not disable the crash reporter, it only stops it from telling you.

If you want to fully disable the crash reporting then you have to edit a file
The file is in /etc/default/apport
Simply change it from enable=1 to enable=0
The file must be edited as root.
Easiest way to edit is the command line
```
sudoedit /etc/default/apport
```sudoedit will use whatever command line editor is set as your default.
Ubuntu's default editor is nano, but you can set it to something else like vi, or ed or other.
To save in nano, press ctrl + X then follow the instructions; usually you can press Y for yes to save the changes, then then enter to save as the intended file.
Hope that makes sense.

---

### Post by MAFoElffen on 2022-02-24
But on how to immediately get a clue... when it generates, it also inserts a button in te lower left of that to "View Details" before you even decide to send the bug report, where it might give clues on what part of the system is involved.

Just a thought...

---

### Post by mugwump40 on 2022-02-24
Thanks for the help.  I looked at var/crash and it seems to be a pulse audio problem.  Strange thing is, it quit giving me the message and I didn't change anything.   So. I'll mark this as closed.

---

### Post by MAFoElffen on 2022-02-24
In apport, if so many crashes have been processed, and you say you want to send the report... (or something like that) then it sees earlier crashes that are the same, as sees those as duplicates, to then skips the duplicates. That is what I read from the logs on my machines.

---

