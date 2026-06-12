---
title: "kmix doesn't work"
date: 2019-10-09
forum: General Help
---

### Post by bjngchn on 2019-10-09
I see volume icon on the panel, which is supposed to be kmix. 
Moving mouse over it, or clicking on it doesn;t help.  Only thing I can do is  right click,
 and if I'm lucky I see some options. One of these options is: restore. I click on it. Nothing happens.

This happens with only one user.
It mught be related to chmod  staus  oor system settings.

If there is a simple solution, like deleting a file, chmoding some direcory, this would be great.

---

### Post by deadflowr on 2019-10-09
Not sure, did you chmod something?

Also, please post information about the system.
Such as which release and/or flavor.

---

### Post by bjngchn on 2019-10-09
14.04   I did chmod ing but my target was some stuff on the desktop.  (a few days ago,  still trying to correct things)
 I had to use sudo chmod , because I moved files from elsewhere (another user),  
and to make files accessible to me I had to use sudo chmod.
  I preferred to do sudo chmod 700 and used some wildcards, but only did when I was on /Desktop directory, 
so such applications  shouln't  have been affected. 

 Should I make application files chmod 777 ?

  .... 
Ok now I see kwin shows volume is at 100 percent. I can't modify it using kwin icon,  but I managed to drop volume using Fn hot keys.
Kwin stays on the panel as an icon is not very useful.

Similarly I can;t run chromium. I click on Chromium link, t goes to the panel and stays there. Nothing can be done about it.
Mentioned in another thread. This is also the case for  some other programs.

---

### Post by QIII on 2019-10-09
You are fighting a losing battle spending your time trying to get an unsupported release to work.

I highly suggest that you install a currently supported LTS version of Kubuntu, which would be 18.04.  Kubuntu 14.04 was, I beleive, the last Kubuntu LTS with 5 years of support.  Kubuntu LTS releases are now supported for 3 years -- versus the 5 years of support that Ubuntu enjoys.

In any case, Kubuntu 14.04 went EOL in April, 2019, and is no longer supported.

---

### Post by bjngchn on 2019-10-10
RESOLVED.

Applied the nautilus reinstall command here:

[https://ubuntuforums.org/showthread.php?t=2247343](https://ubuntuforums.org/showthread.php?t=2247343)

---

