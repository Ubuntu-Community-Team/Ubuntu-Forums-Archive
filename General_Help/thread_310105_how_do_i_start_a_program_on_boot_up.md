---
title: "how do i start a program on boot up?"
date: 2006-11-30
forum: General Help
---

### Post by bored_coder_ca on 2006-11-30
Hi all,

How do i get a program to autostart at boot up in 6.10. I've tried update-rc.d but that didnt work. I need this because I want a database to be started before any user logs in.

thanks

---

### Post by 5-HT on 2006-11-30
What about */etc/rc.local*?

---

### Post by bernied on 2006-11-30
An easy way - put the command in /etc/rc.local
You'll find it looks like this. Put your command before the exit command.
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

exit 0
```
A harder way - find the rc script and add it to the runlevel. I think there should be a nice GUI for this. In KDE it's in System Settings and it's called System Services. If there isn't a script, you could write one. Use one of those in /etc/init.d as a basis - find a short one.

---

### Post by bernied on 2006-11-30
got to learn to type faster...

---

### Post by bored_coder_ca on 2006-11-30
hi, ive put it into the rc.local file but it doesnt seem to work heres the contents of it:
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

cd /home/jordan/Desktop/Woosh/Database
java org.apache.derby.drda.NetworkServerControl start -h 0.0.0.0 &

sleep 4

cd /opt/tomcat/bin
./startup.sh

exit 0
```

I have never really written shell scripts before so I could be doing it wrong, any pointers would be appreciated

thanks

---

### Post by bernied on 2006-12-01
I know nothing about java, so can't help you much, but have a couple of suggestions:
- copy/paste all that stuff that you put into rc.local into a script, call it say /usr/local/bin/dbstart
- make the first line of the script like this:
```
#!/bin/sh
```
(this tells the shell what to use to run the script, in this case the sh shell itself)

- within the script, remove the cd commands, instead add the path to the executeable command so:
```
java /home/jordan/Desktop/Woosh/Database/org.apache.derby.drda.NetworkServerControl start -h 0.0.0.0 &
sleep 4
/opt/tomcat/bin/startup.sh
```
(not really sure that this bit is necessary, but I have a funny feeling...)

- make the script executable: ```
chmod 775 /usr/local/bin/dbstart
```
- test the script - does it do what you want?
```
/usr/local/bin/dbstart
```
(you might get away with just dbstart if your path is set up nicely)

- test the script from a text terminal that you log into when there are no X-sessions running (log out to close down your X-session, then use Ctrl-Alt-F1 to get a terminal, then login there and test the script). This is because your script may be dependent on some java magic that might only start with a X-session (someone tell me I'm talking bollocks here?)

- then add the script to /etc/rc.local, with a comment so that you know what it's for when you find it in a year's time
```
# starting woosh(??) database
/usr/local/bin/dbstart
```

There are quite a few other refinements you could make, but this will do for now.

---

### Post by frodon on 2006-12-01
The right method is to put the script your want to run under /etc/init.d/ and give it execute rights, then run the update-rc command like this :
```
sudo update-rc.d *name_of_the_script* defaults
```It will create all the needed symbolic links in the rc directories.

---

### Post by bernied on 2006-12-01
I thought that scripts run through the rc system needed to have certain standards, like at least defined start and stop parameters. Sounds to me like that might be a couple of steps further down the road for the OP.

---

### Post by frodon on 2006-12-01
Here is a standard body for a init.d script for example : ```
#!/bin/bash

RETVAL=0

# What you want to do when you start the script
start() {
  # put your commands here
  RETVAL=0
}

# What you want to do when you stop the script
stop() {
  # put your commands here
  RETVAL=0
}

case $1 in
  start)
    start
    ;;
  stop)
    stop
    ;;
  restart)
    stop
    start
    ;;
  status)
    # put here what you want to display on status command
    RETVAL=0
    ;;
  *)
    echo "Usage: *name of script* {start|stop|restart|status}"
    RETVAL=1
esac
```

---

### Post by bernied on 2006-12-01
Ah, thank you. I've always wanted one of those. Easier than trying to adapt another one.

Should there be an exit $RETVAL at the end, or something like it?

---

### Post by frodon on 2006-12-01
I think you can just put your commands where i noticed it and go, it's the body i use for iptables firewall script, however you may not need the status command so you may want to remove this part.
I'm not an init.d guru but it worked just well for me and my firewall script, hope it will for you as well ;)

---

### Post by superami on 2007-03-15
I found this great explanation just today.  And it half worked for me.  
The script mounts and dismount a truecrypt volume.  This requires entering a password.  The script is able to run and echo into the log file, BUT it won't let me enter a password, which defeats the purpose of the script.  Does anyone have a way around this?

---

