---
title: "Cron to run command lines?"
date: 2018-09-21
forum: General Help
---

### Post by grandkodiak2 on 2018-09-21
I've never attempted to add anything to cron so I'd like some help. I have a raspberry pi that runs a service called motion which is a camera server with picture by picture analysis built in so it works through glass or what have you... but i only need it to be a remote view... I dont even need it to record... plus, it crashes very often with the motion analysis running. That aside, I have found that running the program with -m flag disables the analysis part, and runs nearly crash free now... but everyone 10 hours or so it does still. I have to stop then restart the service to get it back up and running, as there is no config entry that replaces the -m flag that i can tell.

so... can I add a cron task, or something somewhere else, that will simply run 2 command line statements every say, 6 hours to keep it up? the commands would be

sudo service motion stop
sudo motion -m

how can I make this happen?

thank you!

---

### Post by yancek on 2018-09-21
Did you review the documentation at their web site?  Config files are discussed there.

[https://motion-project.github.io/motion_guide.html](https://motion-project.github.io/motion_guide.html)

If you need to use cron, write a script with those command and then create a crontab entry as root/sudo using crontab -e.  Make sure you include the full path to the script in the cron entry.

---

### Post by grandkodiak2 on 2018-09-21
sounds good... except, dont know how.

---

### Post by yancek on 2018-09-22
If the commands you want to run are what you posted in your first post, you can create a bash script with the commands in it as below, save the file.

```
#!/bin/bash
sudo service motion stop
sudo motion -m
```

You can then right click on it, select Properties then click the Permissions tab and check the executable box or use the chmod command to make it executable.

There are numerous sites available with example crontab entries such as the one below.  I expect you would need to use root (sudo) to stop/start motion so do:  sudo crontab -e and then enter the various time/date parameters you want and make sure you have the full path to the script in the crontab entry.  If the script fails because you have it in your /home/user directory, move it to one of the directories below which should be in the PATH:

/sbin:/usr/sbin:/bin:/usr/bin

[https://tecadmin.net/crontab-in-linux-with-20-examples-of-cron-schedule/](https://tecadmin.net/crontab-in-linux-with-20-examples-of-cron-schedule/)

---

### Post by grandkodiak2 on 2018-09-22
perfect, thank you!

---

