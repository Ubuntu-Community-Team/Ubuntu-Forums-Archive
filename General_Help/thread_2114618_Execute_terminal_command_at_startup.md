---
title: "Execute terminal command at startup"
date: 2013-02-10
forum: General Help
---

### Post by odinsothereye on 2013-02-10
Hi everyone,

I've been using Lubuntu 12.10 for a while now and I really like it. Lightning fast and no-nonsense, and generally easy to customize. This time, though, I'm having trouble figuring out how to customize my trackpad settings in a lasting way. 

Specifically, the default settings are to have vertical edge scrolling on, and two finger horizontal scrolling off. I want the opposite of the default, i.e. two finger horizontal on and vertical edge off. I've found that the terminal commands ```
synclient HorizTwoFingerScroll=1

``` and ```
synclient VertEdgeScroll=0
``` work well for making that change, but whenever I restart or power off the computer, I have to run these commands again from the terminal when I log in the next time. I'm trying to figure out how to obviate this annoying, repetitive step.

I've heard tell that one can put a script containing these commands in a certain format and location, but I do not know the location I should use. I have some experience writing bash scripts and I think those should work, but the recommended locations I've found don't seem to exist in my OS and so I'm not sure what my next step should be.

Summary/TLDR: How do I run terminal commands on startup? Specifically, where do I put a file containing the scripts I want to run, in order for the script to be run when I start up the computer, and what file type should it be?

---

### Post by schragge on 2013-02-10
I usually put my settings into ~/.xsessionrc

---

### Post by SeijiSensei on 2013-02-10
If you want a command to run at boot, put it in /etc/rc.local.  That will execute whether you're running in text-mode or graphics mode with X.  Use the full path to the program or script, too.

---

### Post by ajgreeny on 2013-02-10
Make the script with leafpad containing
```
#!/bin/bash
synclient HorizTwoFingerScroll=1 &
synclient VertEdgeScroll=0
```
Save it as touchpad.sh in you home, make it executable with ```
chmod +x touchpad.sh
``` then point to it in the startup applications list in ~/.config/lxsession/Lubuntu/autostart with the full pathway as command , ie, ```
/home/*username*/.config/lxsession/Lubuntu/autostart/touchpad.sh
```

---

### Post by odinsothereye on 2013-02-11
All of your answers have been great, but I'm encountering a problem. There is no lxsession directory in the .config directory. I did find an autostart folder in the .config directory that contains applications which start up automatically, but putting a file containing the script you wrote into that directory didn't work. I also tried creating an application called touchpad.desktop, but that didn't work either. Is there something I'm not understanding about these solutions?

> **ajgreeny said:**
> Make the script with leafpad containing
```
#!/bin/bash
synclient HorizTwoFingerScroll=1 &
synclient VertEdgeScroll=0
```
Save it as touchpad.sh in you home, make it executable with ```
chmod +x touchpad.sh
``` then point to it in the startup applications list in ~/.config/lxsession/Lubuntu/autostart with the full pathway as command , ie, ```
/home/*username*/.config/lxsession/Lubuntu/autostart/touchpad.sh
```

---

### Post by c2tarun on 2013-02-11
> **odinsothereye said:**
> All of your answers have been great, but I'm encountering a problem. There is no lxsession directory in the .config directory. I did find an autostart folder in the .config directory that contains applications which start up automatically, but putting a file containing the script you wrote into that directory didn't work. I also tried creating an application called touchpad.desktop, but that didn't work either. Is there something I'm not understanding about these solutions?

I guess you can create lxsession and .autostart directories. Isn't there any GUI tool to control startup application in Lubuntu?

---

### Post by Cheesemill on 2013-02-11
> **SeijiSensei said:**
> If you want a command to run at boot, put it in /etc/rc.local.  That will execute whether you're running in text-mode or graphics mode with X.  Use the full path to the program or script, too.
Please remember that this method will run anything in rc.local ***as root***. This may be what you want to do, then again it may not be.

---

### Post by Bufeu on 2013-02-11
> **Cheesemill said:**
> Please remember that this method will run anything in rc.local ***as root***. This may be what you want to do, then again it may not be.
Yeah, but you can always use *sudo -u <user you want to run the command as> <command>* to run a command as a specific user.

---

### Post by odinsothereye on 2013-02-18
> **Cheesemill said:**
> Please remember that this method will run anything in rc.local ***as root***. This may be what you want to do, then again it may not be.

Sorry for the delay, everyone! So I just create a file in Leafpad containing the commands and put the file into the above directory?

---

### Post by seppalta on 2013-02-19
[http://lxlinux.com/#17](http://lxlinux.com/#17)
The autostart for Lubuntu will be a slight distortion of /etc/xdg/lxsession/LXDE/autostart, probably has lubuntu replacing lxde.

---

### Post by kjohri on 2013-02-20
You can try putting these commands in the .bashrc file in the HOME directory.

---

