---
title: "Is it possible to control loading order of startup programs on bootup?"
date: 2008-04-22
forum: General Help
---

### Post by caljohnsmith on 2008-04-22
In System > Preferences > Sessions, under the "Current Session" tab, it is possible to change the "order" in which startup programs load. But this doesn't seem to have any effect on how the programs load at the next bootup, because the values get reset. What then is the purpose then of changing the "order" numbers? :confused:

What I'm actually trying to accomplish is to have Ubuntu simply load the apps listed under the "startup programs" tab, but I want to be able to modify their loading order. Is this possible? When I highlight an app and click "edit" it has no option to set its startup order. This would help me prevent some conflicts where some programs need to be loaded before others that need them in order to work.

Any help would be greatly appreciated!

---

### Post by warp99 on 2008-04-22
> **caljohnsmith said:**
> In System > Preferences > Sessions, under the "Current Session" tab, it is possible to change the "order" in which startup programs load. But this doesn't seem to have any effect on how the programs load at the next bootup, because the values get reset. What then is the purpose then of changing the "order" numbers? :confused:

What I'm actually trying to accomplish is to have Ubuntu simply load the apps listed under the "startup programs" tab, but I want to be able to modify their loading order. Is this possible? When I highlight an app and click "edit" it has no option to set its startup order. This would help me prevent some conflicts where some programs need to be loaded before others that need them in order to work.

Any help would be greatly appreciated!

You can place your executables in a script, then just use one link in your 'startup programs' tab. Example:

I create a startup script file using netcat, uname, and firefox called 'startup.sh' and place the file in /usr/local/bin:

```
sudo nano /usr/local/bin/startup.sh
```
the script in the file:
```
#!/bin/bash

/usr/bin/firefox &
/bin/nc -q 0 locahost 6546
/bin/uname -r


```
change the file to make it executable:
```
sudo chmod +x /usr/local/bin/startup.sh
```
you can change the order of the programs in the script to your needs and can also run them in the background with an '&' appended to the command string. If you need a delay between one program loading and another you can use the 'sleep' argument:

```
#!/bin/bash

/usr/bin/firefox &
sleep 1
/bin/nc -q 0 locahost 6546
/bin/uname -r


```
There are plenty of guides and script samples available out in the wild.

---

### Post by caljohnsmith on 2008-04-23
Thank you Warp99, that makes perfect sense. It sure would be nice if this functionality was built into the Sessions program, but your workaround will get me by in the meantime. Thanks for taking the time for the detailed explanation! :)

Unfortunately though, in the process of trying to learn more about this issue, I'm a bit confused now as to exactly which programs get executed on bootup, and how they might be related to each other, for instance:

1) Programs listed in the "Sessions" app
2) Scripts in the /etc/init.d folder 
3) /etc/rc.local script (also seems to be a place where you can put commands/programs for execution on bootup)
4) .bashrc file and other .files in my home directory

If it is too much trouble to explain all this in a single reply, can somebody maybe point me to a good tutorial/documentation of where it explains in depth what gets loaded on bootup in Ubuntu (and in what order it happens)?

---

### Post by warp99 on 2008-04-23
> **caljohnsmith said:**
> If it is too much trouble to explain all this in a single reply, can somebody maybe point me to a good tutorial/documentation of where it explains in depth what gets loaded on bootup in Ubuntu (and in what order it happens)?

I'll try to help you the best I can with an explaination, so here it goes:

> 1) Programs listed in the "Sessions" app
These are programs that you would run during your Gnome session. It's the GUI for a startup script but with less control over the arguments. I never use it because I have better control over the loading process by using a script and placing a '*.desktop' file with a pointer to a script in the autostart directory. Gnome's autostart directory is in ~/.config/autostart for local files and /usr/share/gnome/autostart or /usr/share/autostart for system-wide starting during a Gnome session.
> 2) Scripts in the /etc/init.d folder
Those are services scripts that are run at boot time and are initialized by symlinks placed in the runlevel directories (rc0.d, rc1.d, rc2.d, etc.).  Configuration is done by using the program 'update-rc.d' to add, remove, or change the runlevel of the scripts. These scripts are not depended on a Gnome session.
> 3) /etc/rc.local script (also seems to be a place where you can put commands/programs for execution on bootup)
Your are correct. This is the file to place misc services/commands to be run at boot at the end of each multiuser runlevel without using the 'update-rc.d' to make a seperate script and runlevel settings. Once again not depended on a Gnome session.
> 4) .bashrc file and other .files in my home directory
This file sets the bash environment for your login session and can run certain programs when you start a bash session. The system-wide file is located in /etc/bash.bashrc. Most of the time you would use this file to set environment variables, such as 'export' or 'path'. If you want some more detailed information look in your '/usr/share/doc/bash' directory.

---

### Post by caljohnsmith on 2008-04-28
warp99, sorry I didn't get back to you sooner, because I wanted to thank you for taking the time to explain it so clearly. I understand it alot better now. :)

---

### Post by Icarin on 2009-11-21
Hi everyone,

I know this is an old post, however I have the following situation:
1) A command was added using the Sessions App.
2) I need to change it, however I have no physical access to the server (I'm over ssh).

So the question is, does anyone knows where is the file in which all the commands from the Sessions App are written? I just need to change a line or two and I can't find it.

Thanks in advance!

---

### Post by venicequeen7706 on 2009-12-23
It seems like mine go to .config/autostart but i'm totally new to ubuntu and in fact am having some trouble interpreting what was said in the first response, so maybe i'm not the best one to trust

---

### Post by venicequeen7706 on 2009-12-23
I'm trying to change the order to ensure that an app i installed runs after my computer connects to the internet. would this method work for that? I'm still new to linux so please make any explanation simple if possible.
thanks.

---

### Post by 666f6f on 2010-03-09
> **warp99 said:**
> 
Gnome's autostart directory is in ~/.config/autostart for local files and /usr/share/gnome/autostart or /usr/share/autostart for system-wide starting during a Gnome session.


Based on **sudo find / -type d -name autostart** results I'd like to add /etc/xdg/autostart and /usr/share/gdm/autostart in the list of directories containing system-wide autostart entries.

At least this is the case in my system (Karmic Koala)...

---

