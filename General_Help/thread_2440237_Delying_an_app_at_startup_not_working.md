---
title: "Delying an app at startup not working"
date: 2020-04-07
forum: General Help
---

### Post by donmatas on 2020-04-07
Hi,

I would like to make Nextcolud to run 90 seconds after other apps at the startup. I used sleep command without success, as shown in the image attached. What would be the problem?

```
sleep 30; /usr/bin/nextcloud
```

---

### Post by Frogs Hair on 2020-04-07
You could try the following. Create a text document, place it where you want, make it executable in properties- permissions then navigate in the command section to the script. I don't have nextcloud, but have used this script before.  
```
#!/bin/bash sleep 90 && nextcloud;
```

---

### Post by deadflowr on 2020-04-07
if using Ubuntu or a gnome  desktop you can delay it with the line
```
X-GNOME-Autostart-Delay=##
```
add it to the Startup Applications .desktop file that was created.
(Startup .desktop files should be in ~/.config/autostart)

---

### Post by donmatas on 2020-04-08
Should I add X-GNOME-Autostart-Delay=## to the file Nextcloud.desktop placed at ~/.config/autostart?

---

### Post by donmatas on 2020-04-08
Thanks, but the solution looks incomplete for a beginner like me. I can create the text document (which format?). I can make it executable, but then, what?

---

### Post by deadflowr on 2020-04-08
> **donmatas said:**
> Should I add X-GNOME-Autostart-Delay=## to the file Nextcloud.desktop placed at ~/.config/autostart?

Yep.
Change ## to the number of seconds you want to delay it for.

---

### Post by Holger_Gehrke on 2020-04-08
And here a bit of explanation as to why it didn't work the way you originally tried:  the program executing other programs from .desktop-files is not as "intelligent" as the shell. It simply takes the first word in the command and calls that as a program and passes the rest of the line to it as parameters. So it calls 'sleep' and gives it the parameters "30;" and "/usr/bin/nextcloud". This obviously fails, because neither '30;'  nor '/usr/bin/nextcloud' is a valid duration. 

By creating a script and putting the path to and name of that script as the command to execute - as Frogs Hair suggested - you'd have the command executed by the shell, which knows to split the line on the ';' and execute the commands one after the other. Another way to do it would be to call the shell as the command and pass the command line to the shell as a parameter:
```

bash -c 'sleep 30 ; /usr/bin/nextcloud'

```

Holger

---

### Post by donmatas on 2020-04-09
> **deadflowr said:**
> if using Ubuntu or a gnome  desktop you can delay it with the line
```
X-GNOME-Autostart-Delay=##
```
add it to the Startup Applications .desktop file that was created.
(Startup .desktop files should be in ~/.config/autostart)

This solution certainly worked. Thank you very much to you and to all of them that helped me.

---

