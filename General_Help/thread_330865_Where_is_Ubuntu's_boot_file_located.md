---
title: "Where is Ubuntu's boot file located?"
date: 2007-01-03
forum: General Help
---

### Post by Quillz on 2007-01-03
>     7. 915resolution must run before the X server is started.  So I don't need to          do this every time I put it in my startup scripts.  I'm running SUSE 9.2,          so I put the definition in /etc/init.d/boot.local:         #! /bin/sh        #        # Copyright (c) 2002 SuSE Linux AG Nuernberg, Germany.  All rights reserved.        #        # Author: Werner Fink , 1996        #         Burchard Steinbild, 1996        #        # /etc/init.d/boot.local        #        # script with local commands to be executed from init on system startup        #        # Here you should add things, that should happen directly after booting        # before we're going to the first run level.        #         /usr/bin/915resolution 38 1280 800 [http://www.geocities.com/stomljen/readme.html](http://www.geocities.com/stomljen/readme.html)

Needless to say, I cannot find /boot.local in the /init.d/ directory. Where is it?

---

### Post by lloyd_b on 2007-01-03
Ubuntu is a little different from SuSe.  The equivalent file in Ubuntu is "/etc/rc.local".

Lloyd B.

---

### Post by Quillz on 2007-01-03
Can you tell me why this isn't booting properly?
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

/usr/bin/915resolution 38 1440 900 24

exit 0

```

---

### Post by az on 2007-01-03
The 915resolution package already installs a script for you.

Read the instructions in /usr/share/doc/915resolution

---

### Post by Quillz on 2007-01-03
> **azz said:**
> The 915resolution package already installs a script for you.

Read the instructions in /usr/share/doc/915resolution
I follow the instructions and it still doesn't work. When I reboot, I can log in to 1440x900, but the PC freezes and takes me back to the login screen, where I'm forced to use the failsafe terminal and revert back to 1024x768.

---

### Post by Quillz on 2007-01-03
Am I supposed to rename rc.local to something else in order for it to load before X does?

---

### Post by amd-64 on 2007-01-03
If you want to set this up on your own or debug the script provided, just install ksysv and have a look at the priority of each process. 

rc.local is typically run near the end with priority 99 in runlevel 2 whereas kdm starts at 13. You need to use a value lower than 13 for rc.local to start it before kdm or gdm and you could run it from runlevel 1. You can also do all of this by hand by modifying the links in /etc/rc1.d and /etc/rc2.d

Be very careful and use this tool wisely, better yet save a back up copy of /etc/rc*.d directories and /etc/init.d just in case you need to revert all of this.

---

### Post by Quillz on 2007-01-03
Or even better, I could've just read the wiki and ran the auto reconfigure script. ;) I did that, and my Intel video card was instantly detected, so I'm now running 1440x900 natively, with no "hacking" necessary. :D

---

### Post by FlashOmega on 2007-01-09
I see this topic is a bit old but hopefully someone can help me... when configuring ksysv you are asked for 2 locations

Service Path:

Run Level Path:

what are they in edgy?

---

### Post by amd-64 on 2007-01-09
The service path is /etc/init.d  This is where all the services are stored. Each may be started stopped or restarted from the command line with 
"sudo /etc/init.d/servicename start" 
similarly you can replace start with stop or with restart. You may want to read the files in this folder for additional info. Use
"less /etc/init.d/servicename"

The path to the run levels is /etc
The run levels themselves are located in rc0.d, rc1.d, ... which are all located in /etc
runlevel 0 stops the machine, level 2 is the default runlevel for a desktop, and runlevel 6 restarts the machine

---

### Post by Zarate on 2007-01-10
Hi there,

Pretty much the same problem here. I went through the tuto, then tried "sudo dpkg-reconfigure xserver-xorg" (that didn't work AT ALL for me, had to go back to xorg.conf backup file) and now I'm trying with KSysV.

I can see 915resolution service in levels 2,3 and 4, but always AFTER gdm. Should I put it before? In ALL levels?

I'd really appreciate the final push to fix this.

Thanks a lot.

---

### Post by Zarate on 2007-01-14
Como on guys, nobody has any idea?

It's really annyoying working with a wrong resolution, especially in laptops and flat monitors. And I don't find any solution anywhere else : |

Thanks

---

