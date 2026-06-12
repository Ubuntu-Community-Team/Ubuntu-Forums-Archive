---
title: "Getting a script to run in the terminal when resuming from suspend/hibernate"
date: 2008-07-01
forum: General Help
---

### Post by cup0spam on 2008-07-01
So I purchased a Thinkpad T61. The 15.4" screen is known for having a bluish tint with Ubuntu. This is solved using xcalib & a custom .icm file. I run a script at startup to apply this display profile, but when I resume from suspend/hibernate/lid-closed (display off) or even when the screen fades to save battery life, I must reapply the script.

I run "xcalib /home/<user>/<file>.icm" from the terminal to enable the display profile manually. I have it applied automatically when gnome launches by placing that code in the sessions app as well.

I'd love to be able to have this run for me automatically when I resume from the scenarios I mentioned above. 

Is there a way in Ubuntu for me to do this? Or if anyone familiar with xcalib would car to chime in I'd greatly appreciate it.

Thanks in advance!

---

### Post by soccerboy on 2008-07-01
i am pretty sure the files under /etc/acpi should be the ones but I wouldn't edit them without knowing what you are doing.

---

### Post by cup0spam on 2008-07-01
Yeah I've never edited any of those files before. Someone must have a way to do it.

---

### Post by soccerboy on 2008-07-01
they look like bash script so you could back them up and then add your command but I can't guarantee it.

---

### Post by Andreas1 on 2008-07-26
I do not know how to run a script after resume, but i have a solution for your xcalib problem:

1) create file ".xinitrc" in your home folder (/home/yourname/) with the following content: ```
xcalib -blue 1.0 0.0 85.0 -a &
exec gnome-session
```

2) create a link ".xsession" to ".xinitrc" (both files in /home/yourname/)

more information:
[http://ubuntuforums.org/showthread.php?t=367810&highlight=xcalib]("http://ubuntuforums.org/showthread.php?t=367810&highlight=xcalib")
[https://help.ubuntu.com/community/CustomXSession]("https://help.ubuntu.com/community/CustomXSession")

---

