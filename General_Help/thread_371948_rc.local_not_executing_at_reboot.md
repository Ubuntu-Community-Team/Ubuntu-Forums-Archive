---
title: "rc.local not executing at reboot"
date: 2007-02-27
forum: General Help
---

### Post by tbeld on 2007-02-27
I tried to search the forums but didn't have any luck. I have been trying to run two scripts (need to run as root) at boot. I have tried various methods that I found through Google and also here in the forums. Here's where I am now...

I have lines in /etc/rc.local linking to my two scripts:
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
/usr/local/bin/jakarta/bin/startup.sh
/usr/local/gong/startit.sh
exit 0
```
From several postings it seems as though this should work and after reboot, if I run:```
sudo /etc/rc.local
```, all goes well and both Tomcat and the Gong server startup.

Could someone help me out?

Things I've tried: 
putting the scripts in /etc/init.d and chmoding +x and sudo update-rc.d gong defaults
creating /etc/rc.boot and putting the scripts in there
symlinking to the scripts from /etc/init.d and running update-rc.d etc...

---

### Post by caldevil on 2007-02-27
My guess is the programs need something which hasn't been started by that time. Try putting 
sleep 20

in the script.

---

### Post by tbeld on 2007-02-27
I put sleep 20 on it's own line at the start of the script .and it didn't do it for me. Thanks though. Would it help to test a greater increment? Is there a way to check to see any error messages?

---

### Post by johnc4510 on 2007-02-27
Did you make the two scripts executable?

chmod a+x /plus/the/file/path

---

### Post by tbeld on 2007-02-27
Yep...
-rwxr-xr-x  1 tbeld tbeld     710 2007-02-27 16:21 startit.sh

---

### Post by lamego on 2007-02-27
To be sure rc.local is being called just append to it a line for debugging:
```
echo $(date) - Running >> /var/test.run
```
Reboot and check /var/test.run

To check your scripts errors just use:
```
/path/to/script > /var/myscript.log 2>&1
```

This will make sure the output and errors will be written to /var/myscript.log

---

### Post by tbeld on 2007-02-27
> **lamego said:**
> To be sure rc.local is being called just append to it a line for debugging:
```
echo $(date) - Running >> /var/test.run
```
Reboot and check /var/test.run

To check your scripts errors just use:
```
/path/to/script > /var/myscript.log 2>&1
```

This will make sure the output and errors will be written to /var/myscript.log

This is exactly what I needed. Thank you so much. After adding the above to rc.local, I was able to find out what was going on. The JAVA_HOME variable was not defined at boot since it is in ~/.bashrc and so all I needed was to export the path in the script- a stupid mistake but I missed it.

Thanks for schooling me on how to send script output to a file!

---

