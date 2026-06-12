---
title: "shut-down and restart are no longer options of my ubuntu :O"
date: 2008-07-02
forum: General Help
---

### Post by chriskin on 2008-07-02
when i press the button to shut down, there are no options for restart and shut-down as there where before

also, when i ask for a log-out, the screen goes crazy if i do it from ubuntu, showing colours and symbols, or just black if i do it from kubuntu
:S

can someone help please?

---

### Post by rampageoberon on 2008-07-02
Please check if the user you are using has admin privilages. If I'm not mistaken you need root privilages to shut down or restart the system.

I'm not too sure about the log out. Have you tried restarting gdm in gnome or kdm in kde? You can do this by opening the fixed terminal CTRL+ALT+F1 and using code below

```
sudo /etc/init.d/gdm restart
sudo /etc/init.d/kdm restart
```

---

### Post by chriskin on 2008-07-02
i definetely had the rights to turn off my computer before, i mean which user doesn't have the rights to turn off his own computer? 

i did the restart thing but nothing really happened :S

---

### Post by chriskin on 2008-07-02
Solved

---

### Post by pastalavista on 2008-07-02
I'm curious. What was the problem?

---

### Post by chriskin on 2008-07-02
i have no idea
i restarted gdm as said by rampageoberon but got nothing
so i kept on doing whatever i was doing, i updated my system and the options went there once again :O

---

### Post by Marshal0505 on 2008-07-02
I am able to reproduce this problem by enabling sli and closing my current gdm session.(i usually then start playing a game on a seperate x server).
When i restart gdm my shutdown and restart options are gone until i reboot.

Could it be this is the same issue you are experiencing?

My current workaround is either not closing my original gdm session or disabling sli.Or.....sudo reboot/shutdown in a terminal :D

Bugs like this really dont bother me , but i thought i'd add in case someone finds this info useful.

Ubuntu Hardy with driver 169.12 and 2x 7800GTX btw

---

### Post by danwood76 on 2008-07-02
This issue is caused by the graphics drivers I think.
I remember it happening each time I uninstall fglrx, upon a reboot without reconfiguring X, shutdown options are gone so you have to logout and shutdown from there.

Once the correct drivers are re loaded the options come back.

---

