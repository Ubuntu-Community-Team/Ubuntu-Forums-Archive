---
title: "x server help"
date: 2007-06-09
forum: General Help
---

### Post by michaelbmcgee on 2007-06-09
i download nvidia drivers for my 7600gt card and  i am using ubuntu feisty. when i run the driver setup program in terminal it says that i cant install with X server running. i did a little bit of searching but to no avail. is there a way to just boot into terminal or something? please help... ive only know linux for a week and  a half!

---

### Post by cookies on 2007-06-09
CTRL ALT F6 Gets you to a text only console. CTRL ALT F7 gets you back to a GUI.

---

### Post by michaelbmcgee on 2007-06-09
it changes the screen to text but when all is finished loading it comes up to the ubuntu login screen...not text
thnx for help so far...any other ideas

edit: i did ctrl alt f6 at loging screen and it goes to text but i get same error when i run the installer...

error: you appear to be running an x server; please exit x before
installing. for further details, please see the section installing
the nvidia driver in the readme available on the linux driver 
download page at [www.nvidia.com](www.nvidia.com)

heres the readme  [http://us.download.nvidia.com/XFree86/Linux-x86/100.14.09/README/chapter-04.html](http://us.download.nvidia.com/XFree86/Linux-x86/100.14.09/README/chapter-04.html)

---

### Post by nerdman978 on 2007-06-09
Can't you just change your login session at the login screen to be text or something, which will drop you out of the GUI? Oh, and if you still have issues check out envy, 
[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")
Which basically installs the drivers and stuff for you.

---

### Post by logos34 on 2007-06-09
> it changes the screen to text but when all is finished loading it comes up to the ubuntu login screen...not text
thnx for help so far...any other ideas

edit: i did ctrl alt f6 at loging screen and it goes to text but i get same error when i run the installer...

error: you appear to be running an x server; please exit x before
installing. for further details, please see the section installing
the nvidia driver in the readme available on the linux driver 

to exit X:
[B]
sudo /etc/init.d/gdm stop[/B]

OR

**sudo killall gdm**

---

### Post by michaelbmcgee on 2007-06-09
> **nerdman978 said:**
> Can't you just change your login session at the login screen to be text or something, which will drop you out of the GUI? Oh, and if you still have issues check out envy, 
[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")
Which basically installs the drivers and stuff for you.

thanks so much that envy package worked

---

