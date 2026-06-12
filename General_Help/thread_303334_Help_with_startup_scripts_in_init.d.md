---
title: "Help with startup scripts in init.d"
date: 2006-11-20
forum: General Help
---

### Post by speedsix on 2006-11-20
I've placed a script in /etc/init.d which works when I execute it manually. I've run the command update-rc.d myscript defaults which creates the symlinks but the program isn't running when I reboot, any ideas?

Thanks

---

### Post by koenn on 2006-11-20
just checking :
- can you see the symlinks in /etc/rc1.d, rc2.d and so on ? In all runlevels ? with a suitable S-number ?
- does the script have all executable (x) permissions ?
- how do you run it from 'manually' clicking in file browser or executing from a command line / terminal ?
- does the script start with an indication of which shell should execute it (like #!/bin/bash) ? which shell ?

---

### Post by druhboruch on 2006-11-20
In Dapper my apcupsd runs just great.  In Edgy it does not start during boot.
All the startup scripts are in place and links are OK too.  I can run it from the terminal 
```
sudo /etc/init.d/apcupsd start
```

It just does not run during startup.  

I think that there is a problem with startup in Edgy, but I cannot confirm it.

---

### Post by koenn on 2006-11-20
what you've tested here is that the script itself runs. 
Now, try running it from the symlink. that should be something like
```
sudo /etc/rc2.d/Sxxapcupsd start
```
you need to replace xx by a number. Look in /etc/rc2.d for the correct name. 

You can also do this by typing
```
sudo /etc/rc2.d/S       
```
and hitting tab (once or twice). This will show all filenames that start with S

also run
```
sudo /etc/rc2.d/Sxxapcupsd
```
if the link works correctly it should tell you you need to add 'start' or 'stop'

Look in the results of these commands for something that confirms that apcupsd is really running, or for something that might indicate what the problem is.

---

### Post by druhboruch on 2006-11-20
Thank you for the hint.  I will test it tonight and post the results.
.
I already checked the symlinks.  They are created by apt: S41apcupsd and they  look OK.

EDIT:

It requires now /etc/default/apcupsd

isconfigured = yes

It works now.

---

### Post by speedsix on 2006-11-21
Hi, my script is a very basic one with just the /bin/bash line at the top and the name of the command 'mtd' underneath. No start or stop sections, is this the problem? The links are created and the script does run ok when invoked from a command prompt.

Does anyone have a template of a script I could add my command to?


Many thanks

Dom.

---

