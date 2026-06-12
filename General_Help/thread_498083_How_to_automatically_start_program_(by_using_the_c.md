---
title: "How to automatically start program (by using the command line)"
date: 2007-07-10
forum: General Help
---

### Post by snakyjake on 2007-07-10
How do I automatically start a program at startup?  

I want to attempt implement this the GNU Linux way, using the command line.  This way I can do it for any flavor, any version, any time.

I think I need the application to start before the login screen.  The specific application to start is "vmware-toolbox".  My current work-around is to simply execute the command from the console after I login.

Thank you,

Jake

---

### Post by dfreer on 2007-07-10
Not much experience with this myself, although this might help you get started:
[https://help.ubuntu.com/community/UbuntuBootupHowto](https://help.ubuntu.com/community/UbuntuBootupHowto)
[http://packages.ubuntu.com/warty/admin/sysv-rc-conf](http://packages.ubuntu.com/warty/admin/sysv-rc-conf)

To install and use:
```
sudo apt-get install sysv-rc-conf
sudo sysv-rc-conf
```

---

### Post by pointone on 2007-07-11
There are two ways to go about this...

1) The best solution would be to add the command to the end of /etc/rc.local, in my opinion. That is, before the exit statement.

2) Slightly more complicated, but possibly more GNUJ/Linux-ish: 
- Create a shell script to start the application.
- Copy the script to "/etc/init.d/".
- Run the command "update-rc.d <scriptname> defaults" to start the script on runlevels 2, 3, 4, 5 and stop the script on runlevels 0, 6. The reason this method is more complicated is because technically, you should format your script according to the Debian policy manual to accept start | stop | restart | force-reload. Take a look at /etc/init.d/skeleton for an example.

---

