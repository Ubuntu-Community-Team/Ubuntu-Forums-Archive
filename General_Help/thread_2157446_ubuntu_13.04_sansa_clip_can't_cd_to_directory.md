---
title: "ubuntu 13.04 sansa clip can't cd to directory"
date: 2013-06-25
forum: General Help
---

### Post by AgentZ86 on 2013-06-25
Hi
I can't access my msc sansa clip from the console

I can cd /media/user to see my media devices plugged in
ls shows the directories for my flash drive and sansa clip

I cd DE30-94A7 for the flash drive and works perfectly
I cd sansa clip it says no such file or directory

I can't cp (copy) any files to /media/user/sansa clip with console commands at all
for example: cp /home/user/Documents/file.txt /media/user/sansa clip

Strangly when I manually run a python script that uses shutil and copy files to this path "/media/user/sansa clip"
It copies to the directory no problem.

Why can't I access this sansa clip from the consol ??
I have the device set to msc mode already and is accessible using any other clickable method

I want to test cp commands in the consol / terminal so I can ad a line to my bash script.

Please advise

---

### Post by oldos2er on 2013-06-25
The shell doesn't parse file or folder names with spaces in them very well; you can either enclose the full path in double quotes: **cd "/media/user/sansa clip"** or use the backslash key like so: **cd /media/user/sansa\ clip**. If you use Tab completion the backslash will be added automatically, which is easiest.

Also Linux is case-sensitive, so if the folder name is actually /media/user/Sansa\ Clip, you will need to specify that, but again, Tab completion makes this simpler.

---

### Post by AgentZ86 on 2013-06-25
that makes sense thanks

Guess it's time I should take some linux consol courses and some bash / sh script lessons

Thanks again.

---

### Post by oldos2er on 2013-06-25
You're welcome.

---

### Post by AgentZ86 on 2013-06-25
I wondered if you might know anything about this which I also posted ?

[http://ubuntuforums.org/showthread.php?t=2156836](http://ubuntuforums.org/showthread.php?t=2156836)
Thanks again

---

