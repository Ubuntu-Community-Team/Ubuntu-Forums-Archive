---
title: "Make a command run with root privileges at startup"
date: 2008-02-09
forum: General Help
---

### Post by steve196 on 2008-02-09
How do i make a command run with root privileges at every startup?

---

### Post by eggdeng on 2008-02-09
Paste the command (with a trailing ampersand) into /etc/init.d/rc.local just after the #!/bin/sh, as follows
```
#!/bin/sh 
my_command_here &
```
It will automatically run as root.

---

### Post by steve196 on 2008-02-09
No, that didt't work.

---

### Post by olejorgen on 2008-02-09
Remember that the command must be in *roots* path. ie. if you placed it in your own bin folder (bad idea since it will be run as root) that might be the reason. If you didn't do it in the first place, try using the absolute path

---

### Post by eggdeng on 2008-02-09
Run
```
which my_command
```
to see if it is located in the system path. If you get no output, run
```
updatedb
```
then
```
locate my_command
```
to pin down the location.Then do as suggested above giving the complete path with the command
```
#!/bin/sh 
/path_to_command/my_command_here &
```
What command are you trying to run?

---

### Post by steve196 on 2008-02-09
The command is: dhcpcd eth0
The program is /sbin/dhcpcd

---

### Post by bwhite82 on 2008-02-09
I believe you need to make the script executable:

> sudo chmod +x /sbin/dhcpd

---

### Post by steve196 on 2008-02-09
It is an executable. It is installed via .deb file from an official repository and i can run it from the command line.

---

### Post by eggdeng on 2008-02-09
```
#!/bin/sh 
/sbin/dhcpcd eth0 &
```
*should* work. If not, the only thing that occurs to me is to prefix ```
ifup eth0;
``` to this to make sure the interface is up when you issue the command. Like so
```
#!/bin/sh
ifup eth0; /sbin/dhcpcd eth0 &
```

---

### Post by steve196 on 2008-02-09
Nope, still no luck.
I don't know, if it is just not executed or if it fails to run. Anyway i still have no internet until i type the command by hand. Only then it works.

---

