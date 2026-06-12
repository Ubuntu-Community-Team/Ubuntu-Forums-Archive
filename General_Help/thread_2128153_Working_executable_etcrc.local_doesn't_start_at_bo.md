---
title: "Working executable /etc/rc.local doesn't start at boot"
date: 2013-03-22
forum: General Help
---

### Post by Kotrfa on 2013-03-22
Hi. 

Here is my /etc/rc.local
```
#!/bin/sh -e#
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
xbacklight -set 10
rfkill block bluetooth
exit 0
```


And it is executable:

```
dan@dan530ubu ~ $ ls -l /etc/rc.local-rwxrwxrwx 1 root root 352 Mar 22 12:08 /etc/rc.local

```

and the script is working - when I run it manually by "/etc/rc.local" it does sets backlight at 10% and turn off bluetooth. But the script does not start at boot. Any ideas? Thanks

---

### Post by TheFu on 2013-03-22
a) having /etc/rc.local as 777 permissions is EXTREMELY dangerous.  chmod 755 would be better.
b) in a shell, your environment is shared.  rc.local doesn't have much, if any, environment, so those programs are probably not found.  Fully specify the path to the exact program.
c) I don't know those programs, but is having root modify user settings like that a good idea? Would having those settings handled per-user be a better option?

---

### Post by Kotrfa on 2013-03-22
Hi. Thanks for reply.

a) I edited to 755 - you're right
b) I wasn't sure what you mean, but I edited as this:
```
#!/bin/sh -e
/usr/bin/xbacklight -set 10
/usr/sbin/rfkill block bluetooth
exit 0
``` 
But nothing changed. Still same problem.
c) I can't find any other solutions. rfkill sets bluetooth off and xbacklight sets brightness of display. They are even not "root" tools, user can run them by default without sudo. I used them a very long time.

---

### Post by Toz on 2013-03-22
xbacklight won't work in /etc/rc.local because it requires an active X environment which is not yet available when /etc/rc.local is run. You have two options:

1. Add the xbacklight command to your Desktop Environment startup files when you login. This will delay the brightness change until you log in.

2. Directly manipulate the backlight interface through /etc/rc.local which should affect the brightness right at startup. See [here]("https://wiki.ubuntu.com/Kernel/Debugging/Backlight#The_.2BAC8-sys.2BAC8-class.2BAC8-backlight_interface") for more information on the backlight interface. After you identify your active interface, you can manipulate the brightness by echoing a value to the brightness file like this (as a user logged in):
```
echo <value> | sudo tee /sys/class/backlight/<interface>/brightess
```
...where <value> is a numeric value between 0 and the contents of /sys/class/backlight/<interface>/max_brightness
.....and <interface> is the directory name of the valid interface

Once tested and working, you can add it to /etc/rc.local, but since /etc/rc.local is run as root, there is no need for sudo. The command to enter in /etc/rc.local would look something like this:
```
echo <value> /sys/class/backlight/interface/brighntess
```

Running the following command will identify your backlight interfaces and the current brightness values:
```
for interface in /sys/class/backlight/*; do echo $interface; cat $interface/brightness; cat $interface/max_brightness; done
```

---

### Post by Kotrfa on 2013-03-23
Thanks for reply.
First option I used to use. I just thought that rc.local is designed for this type of commands and I could run short starting scripts through that. So my "sudo rfkill bluetooth" is stored as a script at /usr/local/bin and I added to startup app at GNOME. And for brightness I used your variant and it work great, thank you. Solved

---

