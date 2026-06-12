---
title: "'Command not found' script problem"
date: 2007-11-28
forum: General Help
---

### Post by warnec on 2007-11-28
Strange thing happened. I wanted to configure a CF git script, and I've got errors and i shouldn't get them. Watch this:
```

maciek@maciek-ubuntu:~$ sudo bash CF_Installer-Updater_v.3.sh
: polecenie nieodnalezioneh: line 2: 
: polecenie nieodnalezioneh: line 5: 
: polecenie nieodnalezioneh: line 6: clear
Welcome to CF Installer-Updater version 3.0
: polecenie nieodnalezioneh: line 8: echo
Reminder: You must have Main, Universe and Multiverse repositories enabled in order this script to work properly (otherwise not everything needed will be able to be downloaded).
: polecenie nieodnalezioneh: line 10: echo
Warning: If you get an error about libcairo.so.2 uninstall Mono and it will be solved (the version which is pre-installed in Ubuntu should not cause any problems).
: polecenie nieodnalezioneh: line 12: 
: polecenie nieodnalezioneh: line 13: echo
Do you use Gnome or KDE?(g/k):

```
And if i run an unchanged script, it works as it should work:
```

maciek@maciek-ubuntu:~$ sudo bash CF_Installer-Updater_v.3.sh

Welcome to CF Installer-Updater version 3.0

Reminder: You must have Main, Universe and Multiverse repositories enabled in order this script to work properly (otherwise not everything needed will be able to be downloaded).

Warning: If you get an error about libcairo.so.2 uninstall Mono and it will be solved (the version which is pre-installed in Ubuntu should not cause any problems).

Do you use Gnome or KDE?(g/k):

```
How come? I have changed NOTHING of the beggining. It looks like this:
```

!/bin/bash



downdir=~/.cf_i-u		#choose download directory - make sure that the path you enter exists, as the sript can only create the final directory (download directory)

gitpluginsall="3d addhelper animation atlantis bench colorfilter compiz-scheme crashhandler cubecaps cubereflex expo extrawm ezoom fadedesktop fakeargb firepaint gears group jpeg mblur mswitch neg opacify put reflex resizeinfo ring scaleaddon scalefilter screencasting shift showdesktop snap snow splash text thumbnail tile trailfocus vpswitch wall wallpaper widget winrules workarounds"



clear

echo -e "\033[7mWelcome to CF Installer-Updater version 3.0\033[0m"

echo

echo -e "\033[1mReminder: You must have Main, Universe and Multiverse repositories enabled in order this script to work properly (otherwise not everything needed will be able to be downloaded).\033[0m"

echo

echo -e "\033[1mWarning: If you get an error about libcairo.so.2 uninstall Mono and it will be solved (the version which is pre-installed in Ubuntu should not cause any problems).\033[0m"



echo

echo -e "\033[1mDo you use Gnome or KDE?(g/k):\033[0m" ; read answer

```

"polecenie nieodnalezioneh" - means "command not found"in english. It's the same code in both scripts! why unchanged works, and mine not? Why is "clear" not recognized, and when i run "clear" in console it works? Why Can't i have "echo" without any text? ANY WHY DOES IT RUN WITH UNCHANGED SCRIPT? I really don't understand that. Help.

---

### Post by llamakc on 2007-11-28
The first line should be:

#!/bin/bash

not

!/bin/bash

---

### Post by warnec on 2007-11-28
Actually, it was

#!/bin/bash

and not 

!/bin/bash

My mistake during copying. With #!/bin/bash I've got that problem.

---

### Post by llamakc on 2007-11-28
Run a diff on the scripts. Do you know how to do that?

---

### Post by Keith Hedger on 2007-11-28
silly question i know but have you set the execute bit on your copy?

---

### Post by warnec on 2007-11-28
> **Keith Hedger said:**
> silly question i know but have you set the execute bit on your copy?

Huh? I don't know what it is :P

PS.: I know how to run diff, will do it tommorow, no i go to sleep :P

---

### Post by Keith Hedger on 2007-11-28
chmod 755 /PATH/TO/YOUR/SCRIPT Or right click on your file > propertiews > permissions > "Allow executing file as program"

---

### Post by warnec on 2007-11-29
Now it works. I just downloaded orginal script, then after each change run the script in terminal. Now i don't have any 'unfound commands' thanks for your help, anyway!

---

