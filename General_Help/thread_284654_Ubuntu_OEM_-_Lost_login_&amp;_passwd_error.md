---
title: "Ubuntu OEM - Lost login &amp; passwd error"
date: 2006-10-25
forum: General Help
---

### Post by Guadian12 on 2006-10-25
Hi, new here...

This what happen...I just finish installing Ubuntu OEM..After login on as OEM, I update the software & i restarted...when i log on as OEM again i got this error..

"GDM could not write to your authorizatin file.  This could mean that you are out of disk space or that you home directory could not be opened for writing.  In any case, it is not possible to log in.  Please contact your system administrator"

I know a fact that I given ubuntu enough hd space.

---

### Post by catlett on 2006-10-25
Did you create a user account? You probably do not have a user account and therefore do not have a home folder. Try to boot to the recovery mode (it will be an option in the grub menu). If you can get into the recovery mode, at the  command line enter this command ```
sudo oem-config-prepare
```That is the command to set up the initial user account.
If you already made a user account, disregard this reply. If you haven't, this is what I would try first. The recovery mode should be the second entry in your grub menu. It will look like the first ubuntu entry in the menu except it will say (recovery mode) after ubuntu in the title. If you can log in, you will get a terminal window with a command line. That is where you would enter the command sudo oem-config-prepare. I do not know for certain if it will work but if you definitely have disk space, then it has to be a home folder issue. If you didn't create a user account, then I would assume oem doesn't have one and therefore the system doesn't have one yet. Long story short, I would give it a try if I was in your position. As the saying goes, 'nothing to loose and everything to gain.' Good luck.

---

### Post by Guadian12 on 2006-10-25
I appreciate for the help..thx catlett

I just found this out..If any newbie (like me) need help i would recommand going here [https://help.ubuntu.com/community/CategoryDocumentation]("https://help.ubuntu.com/community/CategoryDocumentation")

---

