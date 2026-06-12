---
title: "Conky issue"
date: 2015-09-06
forum: General Help
---

### Post by alain.roger on 2015-09-06
Hello,

i'm playing around with conky and i have 2 questions:
1. how to stop the default conky script to be run at boot ?
2. i created several conky scripts as explained in [https://help.ubuntu.com/community/SettingUpConky](https://help.ubuntu.com/community/SettingUpConky) and if i launch the conky_start executable in console, all conky windows appear, so scripts work. But in KUbuntu i'm trying to run conky_start script from boot and even if i add it as script in "System settings > Startup and Shutdown > autostart" nothing happen :( no conky window appears. what could be my mistake ?

thx.

---

### Post by ajgreeny on 2015-09-06
If the script tries to run before your DE is running fully it is possible that conky will not start as you expect.  A delay or pause if usually needed if conky is autostarted with a session.

First make certain that your script is executable, though I assume it already is as you are running it from terminal, and also you can try putting a sleep command at the start of your conky_start script, or in the script where the command conky is written add the pause option, eg, conky -p 20 to delay conky execution for 20 seconds.

It is difficult to know exactly what syntax to use as we have no idea about your script, but as an example, if you use the sleep option in then script it might start something like
```
#!/bin/bash
sleep 20; &
<here add the rest of your script
```

---

### Post by alain.roger on 2015-09-06
here is my executable script

#!/bin/bash
sleep 20 &
conky -c ~/.conky/.conkyrc_top_right &
conky -c ~/.conky/.conkyrc_top_middle &
conky -c ~/.conky/.conkyrc_top_left

i have to remove the ; after 20 because i raise error in my last script

But it does not launch conky :(

---

### Post by ajgreeny on 2015-09-06
Sorry but I think I may have given you the wrong script syntax with the use of both the ; and & in that script; try using the ; alone without the & so it looks like
```
#!/bin/bash
sleep 20;
conky -c ~/.conky/.conkyrc_top_right &
conky -c ~/.conky/.conkyrc_top_middle &
conky -c ~/.conky/.conkyrc_top_left
```
As you are using three separate conky windows when it runs, why not just add those three separate commands to the autostart list but add the -p 20 option to each of them or even change the pause time of each by a few seconds.

By the way, I assume you really do have the configuration files named .conkyrc_top_right, .conkyrc_top_middle & .conkyrc_top_left in your home?  If you don't that is why the conky windows are not showing, but as you say the script works when you run it manually, I think they must exist.

If the script works in terminal but not from the autostart system you might also like to try the full pathway to the config files, ie /home/*user*/.conky/.conkyrc_top_right, etc instead of the ~/ shortcut; I am not sure if it matters, but would be worth trying.

---

