---
title: "xmodmap giving errors"
date: 2013-02-09
forum: General Help
---

### Post by ankt90138 on 2013-02-09
how should i make these permanent keymaps in ubuntu 12.04

xmodmap -e "Keycode 135 = comma"


ubuntu 12.04

rooted cron jobs not working

---

### Post by tgalati4 on 2013-02-09
I normally put keymappings in /etc/init.d/rc.local or in bootmisc.sh.  Because the comma key is pretty common, it's possible that another application is overwriting your keymap.  My keyboard is showing comma as keycode 48.  What is normally defined as 135?  Do you have multiple languages defined?

Normally keyboard errors, or undefined keys show up in dmesg:

```
dmesg | more
```

---

### Post by rnerwein on 2013-02-09
> **ankt90138 said:**
> how should i make these permanent keymaps in ubuntu 12.04

xmodmap -e "Keycode 135 = comma"


ubuntu 12.04

rooted cron jobs not working
hi
i see you already got the solution.
the cron-job isn't running because there is no tty in the cron-job !
cheers

---

### Post by ankt90138 on 2013-02-11
should i keep my keymappings as it is in the end of rc.local ????

---

### Post by ankt90138 on 2013-02-11
should i keep them in end of rc.local

---

### Post by ankt90138 on 2013-02-11
the cron not working o..k..

but modifications made to rc.local should my file:---

#! /bin/sh
### BEGIN INIT INFO
# Provides:          rc.local
# Required-Start:    $remote_fs $syslog $all
# Required-Stop:
# Default-Start:     2 3 4 5
# Default-Stop:
# Short-Description: Run /etc/rc.local if it exist
### END INIT INFO


PATH=/sbin:/usr/sbin:/bin:/usr/bin

. /lib/init/vars.sh
. /lib/lsb/init-functions

do_start() {
    if [ -x /etc/rc.local ]; then
            [ "$VERBOSE" != no ] && log_begin_msg "Running local boot scripts (/etc/rc.local)"
        /etc/rc.local
        ES=$?
        [ "$VERBOSE" != no ] && log_end_msg $ES
        return $ES
    fi
}

case "$1" in
    start)
    do_start
        ;;
    restart|reload|force-reload)
        echo "Error: argument '$1' not supported" >&2
        exit 3
        ;;
    stop)
        ;;
    *)
        echo "Usage: $0 start|stop" >&2
        exit 3
        ;;
esac

@reboot  xmodmap -e "Keycode 108 = comma"
@reboot xmodmap -e "Keycode 135 = period"
@reboot xmodmap -e "Keycode 107 = bracketleft"
@reboot xmodmap -e 'Keycode 127 = bracketright"

---

### Post by ankt90138 on 2013-02-11
dmesg is too long >>>>i mean its output

---

### Post by ankt90138 on 2013-02-11
and thats my cron job

@reboot  xmodmap -e "Keycode 108 = comma"
@reboot xmodmap -e "Keycode 135 = period"
@reboot xmodmap -e "Keycode 107 = bracketleft"
@reboot xmodmap -e 'Keycode 127 = bracketright"

---

### Post by tgalati4 on 2013-02-11
You need to put the commands in /etc/rc.local.  Mine looks like:

tgalati4@Mint14-Extensa /etc $ cat rc.local
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

------------------

Put the commands above the *exit 0* line.

You don't need the @reboot.  Remove the commands from /etc/init.d/rc.local.  That file should be left alone.

---

### Post by ankt90138 on 2013-02-11
ok

now how should i set values for normal key press and with shift pressed ?????

like

default=comma   
shift pressed=less than sigh..

i know its default but i have some error on keymap  so have to change them manually..

---

### Post by ankt90138 on 2013-02-11
doesn't work>>my rc.local

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

xmodmap -e "Keycode 108 = comma"
xmodmap -e "Keycode 135 = period"
xmodmap -e "Keycode 107 = bracketleft"
xmodmap -e 'Keycode 127 = bracketright"



exit 0

---

### Post by tgalati4 on 2013-02-11
keycode not Keycode.  Linux gets severly annoyed when you don't use the correct syntax.  Also check for your single quote in the last line.

---

### Post by ankt90138 on 2013-02-12
its very dissappointing still not working>>>i have send these commands thru terminal they work fine

rc.local


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

xmodmap -e "keycode 108 = comma"
xmodmap -e "keycode 135 = period"
xmodmap -e "keycode 107 = bracketleft"
xmodmap -e "keycode 127 = bracketright"



exit 0

---

### Post by matt_symes on 2013-02-12
Hi 
 
Create a file in your home directory called .xinitrc and add the xmodmap commands there.
 
Open a terminal and type
 
```
 
echo "xmodmap ~/.keymapfile" > ~/.xinitrc

```
 
Make it executable.
 
```
chmod 755 ~/.xinitrc
```
 
Then type
 
```
nano ~/.keymapfile
```
 
and add these lines to it.
 
 ```
 

keycode 108 = comma
keycode 135 = period
keycode 107 = bracketleft
keycode 127 = bracketright

```
 
This uses the format
 
```
keycode X = Y
```
 
Where X and Y are the two keycodes to swap.
 
I pretty sure that will work. 
 
I also don't think adding those commands to rc.local will work for xmodmap, although, if i am wrong, i am open to correction.
 
Kind regards

---

### Post by ankt90138 on 2013-02-12
thats right rc>local doesnt work for me

---

### Post by ankt90138 on 2013-02-12
how to use web chat

---

### Post by matt_symes on 2013-02-12
Hi
 
Did you try my instructions in post #14 ?
 
Kind regards

---

### Post by ankt90138 on 2013-02-15
how do i create a file in /home??

---

### Post by tgalati4 on 2013-02-15
```
cd
```

That puts you in your home directory.

```
nano .keymapfile
```

Brings up an editor with the name of .keymapfile.  It is a hidden file since it starts with a period.  Add your key definitions, then Control-O to write (output) the file.  To exit from the editor, Control-X.

You don't put files in /home.  That is for users directories.

---

### Post by ankt90138 on 2013-02-16
its not working >>provide a working solution

---

### Post by ankt90138 on 2013-02-18
i have done it here is my keymap

xmodmap -e "keycode 108 = comma"
xmodmap -e "keycode 135 = period"
xmodmap -e "keycode 107 = bracketleft"
xmodmap -e "keycode 127 = bracketright"


but its not working

---

