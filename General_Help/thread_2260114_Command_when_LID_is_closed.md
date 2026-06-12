---
title: "Command when LID is closed"
date: 2015-01-09
forum: General Help
---

### Post by mrat2 on 2015-01-09
I have my laptop with this:
[http://ubuntuforums.org/showthread.php?t=2258471](http://ubuntuforums.org/showthread.php?t=2258471)

I posted it like 2 weeks ago, now i want, to use a command when i close LID, something like
apt-get update

To put that everytime that i close the lid, but without ignoring the another config

---

### Post by kalehrl on 2015-01-09
It can be achieved by using acpid.

---

### Post by mrat2 on 2015-01-09
> **kalehrl said:**
> It can be achieved by using acpid.
How can i do that?

---

### Post by Holger_Gehrke on 2015-01-09
> **mrat2 said:**
> How can i do that?

That answer was a bit of a test. If you knew enough to just run "man acpid", then you passed ...

Take my answer **with a big boulder of salt**, I'm still on Ubuntu 12.04 and I don't know what - if anything - has changed since then.

In the directory '/etc/acpid/events' are files with rules for the handling of various acpi events, among them the file '/etc/acpi/lidbtn'. That rule makes acpid call the script '/etc/acpi/lid.sh'. This script does various things. Among these things are tests for the existence of two other scripts: '/etc/acpi/local/lid.sh.pre' and '/etc/acpi/local/lid.sh.post'. If they exist they are called before or after the actions in the script. So you should take a look at that script, decide if your action should get called before or after the stuff in there and write your own 'pre' or 'post' script.

---

### Post by kalehrl on 2015-01-10
I use Debian Jessie but things should be the same in Lubuntu 14.10 you are using.
Make sure acpi is installed.
Create a file in /etc/acpi/events named lidbtn with these contents:
```
# /etc/acpi/events/lidbtn
# Called when the user closes or opens the lid

event=button[ /]lid
action=/etc/acpi/lid.sh
```

Create a file in /etc/acpi named lid.sh (make it executable!) with these contents:
```
#!/bin/sh

case $(awk '{print $2}' /proc/acpi/button/lid/LID/state) in
    closed)    /usr/sbin/vbetool dpms off    ;;
    open)    /usr/sbin/vbetool dpms on    ;;
esac
```
In my case, when lid is closed '/usr/sbin/vbetool dpms off' command is executed.
In my case, when lid is opened '/usr/sbin/vbetool dpms on' command is executed.
Put your commands instead of mine in these places.
Also, you may need to edit /proc/acpi/button/lid/LID/state because some laptops have LID0 instead of LID.
Also, make sure systemd is not handling your lid events but you already did this in your previous thread.

---

### Post by mrat2 on 2015-01-10
> **kalehrl said:**
> I use Debian Jessie but things should be the same in Lubuntu 14.10 you are using.
Make sure acpi is installed.
Create a file in /etc/acpi/events named lidbtn with these contents:
```
# /etc/acpi/events/lidbtn
# Called when the user closes or opens the lid

event=button[ /]lid
action=/etc/acpi/lid.sh
```

Create a file in /etc/acpi named lid.sh (make it executable!) with these contents:
```
#!/bin/sh

case $(awk '{print $2}' /proc/acpi/button/lid/LID/state) in
    closed)    /usr/sbin/vbetool dpms off    ;;
    open)    /usr/sbin/vbetool dpms on    ;;
esac
```
In my case, when lid is closed '/usr/sbin/vbetool dpms off' command is executed.
In my case, when lid is opened '/usr/sbin/vbetool dpms on' command is executed.
Put your commands instead of mine in these places.
Also, you may need to edit /proc/acpi/button/lid/LID/state because some laptops have LID0 instead of LID.
Also, make sure systemd is not handling your lid events but you already did this in your previous thread.

I tried, and using "acpi_listen" it works, and say this: "button/lid LID close".

My lidbtn file is like this:
> # /etc/acpi/events/lidbtn# Called when the user closes or opens the lid


event=button/lid LID close
action=/etc/acpi/lid.sh

And lid.sh is like this:
> !/bin/sh# /etc/acpi/lid.sh


/usr/bin/i3lock -i ~/.lockscreen.png


Now: The script works if i run it manually, but, when i close the lid it doesn't work

---

### Post by kalehrl on 2015-01-10
Event line is in the wrong format.
It should be like this:
```
 event=button[ /]lid
```
Notice the parenthesis and the slash.

---

### Post by mrat2 on 2015-01-10
> **kalehrl said:**
> Event line is in the wrong format.
It should be like this:
```
 event=button[ /]lid
```
Notice the parenthesis and the slash.
I changed it, and still without changes.

I mean, the script works, but the acpid doesn't do anything

---

### Post by kalehrl on 2015-01-11
The scripts you posted are all jumbled up.
Post your exact scripts properly in code tags here.

---

### Post by mrat2 on 2015-01-11
lid.sh
```
#!/bin/sh

case $(awk '{print $2}' /proc/acpi/button/lid/LID/state) in
    close)    i3lock -i ~/.lockscreen.png    ;;
    open)    i3lock -i ~/.lockscreen.png    ;;
esac
```

lidbtn
```
# /etc/acpi/events/lidbtn# Called when the user closes or opens the lid


event=button[ /]lid
action=/etc/acpi/lid.sh "%e"
```

---

### Post by kalehrl on 2015-01-11
Post the output of:
```
 cat /proc/acpi/button/lid/LID/state
```

---

### Post by mrat2 on 2015-01-11
```
state:      open

```

---

### Post by kalehrl on 2015-01-12
I'm running out of ideas.
Try using full paths in your script.
Instead of:
```
 i3lock -i ~/.lockscreen.png
```
use something like:
```
/usr/bin/i3lock -i /home/username/.lockscreen.png
```

---

