---
title: "running /usr/bin's with cron..."
date: 2007-05-25
forum: General Help
---

### Post by kr0w on 2007-05-25
Hi there...

I was wandering how to schedule a binary, so it can be run with cron...
My cron works: if I add a line to run a script, it works fine...
But if I just replace the /path/to/script with a /path/to/binary (i.e. /usr/bin/nautilus) it doesn't work...
I think I need to add the display in which it should run, but I dunno how to do it... besides, I'm not sure if that's the real problem...
Any ideas?...

Thanks

p.s.: sorry for my english... :s

---

### Post by kr0w on 2007-05-25
Here's an example... this is my crontab...


# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

#m   h  dom mon dow user     command
   1    *   *        *       *       root      cd / && run-parts --report /etc/cron.hourly
   53  *   *        *       *        root     /home/kr0w/cp-backup-script


'/home/kr0w/cp-backup-script' works fine, but if I replace it with /usr/bin/nautilus or any other bin, it doesn't run in the specified moment (53th minute of every hour)...

:( :( :(

---

### Post by etank on 2007-05-25
Just a thought here but did you set the cron as root? Try doing a ```
sudo crontab -e
```and then specify the /usr/bin commands to run that way.

---

### Post by JBull on 2007-05-25
Try creating a bash script that opens nautilus and test it out at the command line.  then put that script in your cron.  For example call the script open_nautilus.sh and put this:

#!/bin/bash

nautilus



Then chmod a+x open_nautilus.sh    And test it from the command line.  Then put open_nautilus.sh in your cron.  
I've only ever put scripts in my cron.  Unsure if a binary is allowed.

---

### Post by kr0w on 2007-05-25
mmm... didn't work...

I don't get it... the file is fine (because the script runs) but there must be something special with the binaries...

I'm gonna try with other kind of files to see what happens...

Thanks anyway...

---

### Post by kr0w on 2007-05-25
> **JBull said:**
> Try creating a bash script that opens nautilus and test it out at the command line.  then put that script in your cron.  For example call the script open_nautilus.sh and put this:

#!/bin/bash

nautilus



Then chmod a+x open_nautilus.sh    And test it from the command line.  Then put open_nautilus.sh in your cron.  
I've only ever put scripts in my cron.  Unsure if a binary is allowed.

It doesn'y work either....maybe is just that binaries are not allowed as you said...
Maybe it runs the script fine, but nothing happens because it must execute a binary which is (hipotetically [?] ) not allowed to run...

---

### Post by JBull on 2007-05-26
No, my scripts open binaries every day.  I'll test it out on my system and see what happens.

---

### Post by JBull on 2007-05-26
I tried it on my system and it didn't work either.  I tried to open nautilus and firefox but no go.  Normally a cron job doesn't send any ouput to the display.  Maybe there is some environmental variable that you must pass in the cron command so that it puts the ouput of the command to an active window on the display.  I'm not sure about this.

In any event, binaries are able to be run.  For example you could cron a script with this wget line:

wget [http://www.cnet.com/downloads/somefiles.zip](http://www.cnet.com/downloads/somefiles.zip)

and it would work.  Apparently the problem comes when you try to get the output of binary execution to an active window.  I can't figure out how to do that.

---

### Post by kr0w on 2007-05-26
I can see the script is being executed, as It appears in /var/log/syslog:

....
....
May 26 21:37:01 krubuntu /usr/sbin/cron[4878]: (*system*) RELOAD (/etc/crontab)
May 26 21:37:01 krubuntu /USR/SBIN/CRON[31736]: (root) CMD (    /home/kr0w/Desktop/qwe.sh)


These lines are the same that it shows me when the script is executed correctly (not containing a binary), so, it seems that it's being executed...
But for some reason, is not launching nautilus ... :S

---

### Post by kr0w on 2007-05-26
> **JBull said:**
> I tried it on my system and it didn't work either.  I tried to open nautilus and firefox but no go.  Normally a cron job doesn't send any ouput to the display.  Maybe there is some environmental variable that you must pass in the cron command so that it puts the ouput of the command to an active window on the display.  I'm not sure about this.

Yep, I think I need to add the display...
Something like DISPLAY :0 or so... I'm gonna do some researchs after dinner :P
brb

---

### Post by Beefeater on 2007-05-26
DISPLAY=:0.0
# m h  dom mon dow   command
53 * * * * /usr/bin/nautilus

---

### Post by kr0w on 2007-05-26
It works, thanks!
Just that in my case, it was DISPLAY=:1.0... dunno why... 

Now I have to think a good use for this... :P

---

