---
title: "Parallels"
date: 2006-11-18
forum: General Help
---

### Post by rcg on 2006-11-18
Cannot config Parallels on Edgy 6.10 - 386, any ideas ?

msi@msi-laptop:~/downloads$ sudo parallels-config


[: 141: ==: unexpected operator
     Compiling Parallels Workstation 2.2 drivers...
     Drivers have been compiled successfully.
/usr/bin/parallels-config: 175: pushd: not found
/usr/bin/parallels-config: 186: popd: not found
     Installing drivers...
     Starting drivers...
/usr/lib/parallels/autostart/drivers_start: 19: Syntax error: "(" unexpected
Parallels Workstation drivers were successfully configured
and compiled but cannot be started (insmod command failed).
Run 'dmesg' command for more information.
exit: 3: Illegal number: -1

---

### Post by rcg on 2006-11-20
I got it !

#!/bin/sh to #!/bin/bash. You'll need to do this for a couple more I recall, like some networking scripts.


The files you need to edit are:

/usr/bin/parallels-configure
/usr/lib/parallels/autostart/drivers_start
/usr/lib/parallels/autostart/drivers_stop

---

### Post by gjtoth on 2006-11-22
You sure saved MY butt!  Thanks, dood.

---

### Post by xela321 on 2006-11-23
What all did you do exactly?  I'm running the 2.6.18 kernel, and parallels-config craps out when i try to insmod the hyperviso.ko module.  Exactly what script did change the shell interpreter for?

---

### Post by gjtoth on 2006-11-23
I did just what the other guy did.  I went into all the directories and files in /usr/lib/parallels and edited all the scripts from  #!/bin/sh to #!/bin/bash.  The parallels-config still gives that goofy error but it will run just fine.

---

### Post by Scottty on 2006-12-02
Sorry I'm a really newbie and I don't understand?

I have found the /usr/lib/parallels directory but where exactly do I do the modifying? Where exactly are the scripts? and how do I modify them. I would really like to have parallels running on my system.

thanks
Scott

---

### Post by jcrum on 2006-12-07
> **Scottty said:**
> Sorry I'm a really newbie and I don't understand?

I have found the /usr/lib/parallels directory but where exactly do I do the modifying? Where exactly are the scripts? and how do I modify them. I would really like to have parallels running on my system.

thanks
Scott

hey - basically you open up the shell scripts in your favorite editor and change the first line from

   #! /bin/sh
   to
   #! /bin/bash

This shows the exact set of commands that I issued in order to get parallels working. You can substitute nano for gedit, kate, or any other GUI editor.

jcrum@neumonic:~$ sudo parallels-config 
Password:

[: 141: ==: unexpected operator
     Compiling Parallels Workstation 2.2 drivers...
     Drivers have been compiled successfully.
/usr/bin/parallels-config: 175: pushd: not found
/usr/bin/parallels-config: 186: popd: not found
     Installing drivers...
     Starting drivers...
/usr/lib/parallels/autostart/drivers_start: 19: Syntax error: "(" unexpected
Parallels Workstation drivers were successfully configured
and compiled but cannot be started (insmod command failed).
Run 'dmesg' command for more information.
exit: 3: Illegal number: -1
jcrum@neumonic:~$ 
jcrum@neumonic:~$ sudo nano /usr/bin/parallels-config 
jcrum@neumonic:~$ sudo nano /usr/lib/parallels/autostart/drivers_start 
jcrum@neumonic:~$ sudo nano /usr/lib/parallels/autostart/drivers_stop 
jcrum@neumonic:~$ sudo parallels-config 


     Compiling Parallels Workstation 2.2 drivers...
     Drivers have been compiled successfully.
     Installing drivers...
     Starting drivers...
Loading Parallels Workstation 2.2 hypervisor ... 
Loading Parallels Workstation 2.2 vm-main ... 
Loading Parallels Workstation 2.2 vm-bridge ... 
Loading Parallels Workstation 2.2 vmvirtualnic ... 
Parallels Workstation has been successfully configured

Now you can run Parallels Workstation 2.2
    Issue parallels command

---

### Post by pentium0 on 2006-12-22
thank you; worked great for my Parallels install on Edgy.

---

### Post by thechanklybore on 2007-01-05
The reason for all this is because the link to /bin/sh is from the dash shell in edgy, not bash as it is on the vast majority of linux systems. There are some small speed benefits for this, but I still think it's a bad idea overall. If you want it back the way it was just do:

sudo rm /bin/sh

sudo ln -s /bin/bash /bin/sh


And you'll be Dapper style again :-)

---

### Post by bretticus on 2007-06-04
> **rcg said:**
> I got it !

#!/bin/sh to #!/bin/bash. You'll need to do this for a couple more I recall, like some networking scripts.


The files you need to edit are:

/usr/bin/parallels-configure
/usr/lib/parallels/autostart/drivers_start
/usr/lib/parallels/autostart/drivers_stop

or you can just revert bash back to dash (since dash seems to have issues more often than not.)

```
sudo dpkg-reconfigure dash
```

---

