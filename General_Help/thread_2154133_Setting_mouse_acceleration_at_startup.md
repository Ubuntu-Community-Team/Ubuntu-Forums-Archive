---
title: "Setting mouse acceleration at startup"
date: 2013-06-13
forum: General Help
---

### Post by Aspras on 2013-06-13
My rc.local looks like this :

```

#!/bin/sh -e

sudo razerd

sleep 4

xinput set-prop 11 288 2.8
xinput set-prop 11 290 1
xinput set-prop 11 287 -1

exit 0

```

razerd is the driver daemon which has to be initialized before using xinput. While the daemon does initialize the xinput commands do not work and I always have to execute them manually in a terminal.

---

### Post by Toz on 2013-06-13
/etc/rc.local is not a good choice for running x-based commands as there is no guarantee that X has been initialized. You are better off creating a script that contains the xinput commands (you can leave razerd in /etc/rclocal - note, sudo is not required there) and running that script through the Xfce Startup Applications facility. So:

**/etc/rc.local**:
```
#!/bin/sh -e
razerd
exit 0
```

**$HOME/bin/mouse_init** (create bin directory if it doesn't exist):
```
#!/bin/bash
xinput set-prop 11 288 2.8
xinput set-prop 11 290 1
xinput set-prop 11 287 -1
```
...make the script file executable.

Then in ***Settings Manager-> Session and Startup -> Application Autostart***, add an entry for mouse_init.

---

### Post by ajgreeny on 2013-06-13
You don't need the sudo when you put commands in /etc/rc.local as they are executed by root at bootup, so I wonder if that is stopping the command from working; try removing the **sudo** to see if it makes any difference.

---

### Post by Aspras on 2013-06-13
Thanks for the replies, I did what Toz suggested. On restart the mouse wasn't working as it should be again so I manually executed the "mouse_init" script in a terminal and this was the ouput:

```

property 288 doesn't exist, you need to specify its type and format
property 290 doesn't exist, you need to specify its type and format
property 287 doesn't exist, you need to specify its type and format

```

Now this is what happens when the daemon hasn't been initialized yet which means its not being initialized correctly in rc.local . Is there another init script I can make use of to initialize it from there ? I thought of making a separate script and adding it to the applications autostart list just like with mouse_init but can I make it so that razerd starts before mouse_init ?

---

### Post by Toz on 2013-06-13
Hmmm, that really should of worked. Can you post back the contents of your /etc/rc.local script? Perhaps adding in the sleep 4 command is in someway necessary. You could try:
```
#!/bin/sh -e
razerd
sleep 4
exit 0
```
...or with nohup:
```
#!/bin/sh -e
nohup razerd &
exit 0
```

---

