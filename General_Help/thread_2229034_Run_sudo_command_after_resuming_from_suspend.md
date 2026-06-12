---
title: "Run sudo command after resuming from suspend"
date: 2014-06-10
forum: General Help
---

### Post by dannyboy79 on 2014-06-10
I want to run a command which requires root priveleges after a laptop is opened and it's resumed from suspend. how would i do this? the command is the following
```
sudo logkeys -s -m en_GB.map -o ~/.secret/info.txt
```
any help would be appreciated

---

### Post by TheFu on 2014-06-11
1. Put that command into a script.
2. make the script executable - may want to locate it inside your PATH.
3. Run the script - though you may want to change the sudo into a **gksudo** to popup a GUI for your password to be entered again.


Might want to connect the script to a keyboard chord for easy access. How to do that depends on the DE and WM running.

---

### Post by dannyboy79 on 2014-06-11
i need this command to run without any user intervention, so there definitely can't be a GUI that pops up. so i want the command to be run once the computer is done resuming from a suspend.

---

### Post by dannyboy79 on 2014-06-11
i need this command to run without any user intervention, so there definitely can't be a GUI that pops up. so i want the command to be run once the computer is done resuming from a suspend.

---

### Post by steeldriver on 2014-06-11
It's been a while since I played with this stuff (so it may all have changed) but wouldn't the right place for something like this be an /etc/pm/sleep.d script?

---

### Post by Toz on 2014-06-11
Something like this should work:

/etc/pm/sleep.d/loadkeys (make sure file is executable)
```
#!/bin/bash
case $1 in
    resume)
      logkeys -s -m en_GB.map -o /home/<USER>/.secret/info.txt
      ;;
   *)
      ;;
esac
```
...replace <USER> with the actual username (~ won't work here). sudo is not required because the script is run as root.

---

### Post by dannyboy79 on 2014-06-11
i had found something similar because my USB3.0 mouse wasn't coming back after resuming so I created a script named 20_custom-xhci_hcd and within that file i have:
```
#!/bin/sh
# File: "/etc/pm/sleep.d/20_custom-xhci_hcd".

case "${1}" in
  hibernate|suspend)
    # Unbind xhci_hcd devices
    echo -n "0000:00:14.0" | tee /sys/bus/pci/drivers/xhci_hcd/unbind
  ;;
  resume|thaw)
    # Bind xhci_hcd devices
    echo -n "0000:00:14.0" | tee /sys/bus/pci/drivers/xhci_hcd/bind
  ;;
esac

```
so I thought I would try this
```
#!/bin/sh

case "${1}" in
  hibernate|suspend)
    # logkeys --kill
    logkeys --kill
  ;;
  resume|thaw)
    # logkeys
    logkeys -s -m /home/ubu/en_GB.map -o /home/ubu/.secret/log
  ;;
esac

```
don't i need the logkeys --kill when i suspends? also, how come your command doesn't have ```
"${1}"
``` but only ```
$1
``` Does that make a difference? Also I am curious about the number in the front of the file name, the guide i used made it 20, can my new file be named with 20 as well or shall i choose 19?

---

### Post by Toz on 2014-06-12
> **dannyboy79 said:**
> 
so I thought I would try this
```
#!/bin/sh

case "${1}" in
  hibernate|suspend)
    # logkeys --kill
    logkeys --kill
  ;;
  resume|thaw)
    # logkeys
    logkeys -s -m /home/ubu/en_GB.map -o /home/ubu/.secret/log
  ;;
esac

```
Did it work?

> don't i need the logkeys --kill when i suspends?
Only if you want to kill the process during suspend. From your original post, it sounded like you just wanted it started up again.
>  also, how come your command doesn't have ```
"${1}"
``` but only ```
$1
``` Does that make a difference? 
I've seen this done a number of ways. $1 refers to the parameter being passed to the script. This will usually be one of suspend, hibernate, thaw, or resume. In this case $1 will do. It __is__ possible I guess that something else can get passed, something with a space in it, but this would be a bug and not a normal occurrence. I've always used just $1 and its worked fine.
> Also I am curious about the number in the front of the file name, the guide i used made it 20, can my new file be named with 20 as well or shall i choose 19?
The scripts are executed in alphabetical order on suspend and in reverse alphabetical order during resume. Using numbers can help set that order in case you need it. It probably should of started with a number between 00 and 50 which is generally reserved for user-based scripts.

---

### Post by dannyboy79 on 2014-06-13
putting the 20_logkeys within /usr/bin and adding it to rc.local makes it run when the computer first starts and then adding a file called 20_logkeys, making it executable, and storing it within /etc/pm/sleep.d/
```
#!/bin/sh

case $1 in
  hibernate|suspend)
    # logkeys --kill
    logkeys --kill
  ;;
  resume|thaw)
    # logkeys
    logkeys -s -m /home/ubu/en_GB.map -o /home/ubu/.secret/log
  ;;
  *) 
  ;;
esac
```
it DOES work. notice the "*)" and extra ";;", i saw that within a blog post I found. thanks for everyones help

---

