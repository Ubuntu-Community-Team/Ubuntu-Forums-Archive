---
title: "DPMS control via cron"
date: 2013-02-22
forum: General Help
---

### Post by demontager on 2013-02-22
I got two displays connected to PC. I want to disable automatic screen blanking. It's working fine when i use this command from terminal:
```

xset dpms 0 0 0

```but not working in crontab. I have created small script
```

#!/bin/bash
xset dpms 0 0 0
exit 0

```and pasted in crontab
```

*/10      *      * * *   snich             /usr/bin/disable-screenblanking.sh >> /home/snich/script.log 2>&1

```script runs every 10 mins, but doesn't make any changes because of this error -
```

xset:  unable to open display ""

```

---

### Post by albandy on 2013-02-22
you need to allow remote display
In your session run an script with xhost localhost or xhost +

And in your xset script you have to add something like: export DISPLAY=:0

But I recommend you to run the script in your session this way:

while :
do
xset ........... and all the stuff
sleep 600
done

---

### Post by demontager on 2013-02-22
And what have to be after **while** ?
```

 /usr/bin/disable-screenblanking.sh 
/usr/bin/disable-screenblanking.sh: line 2: while:: command not found
/usr/bin/disable-screenblanking.sh: line 3: syntax error near unexpected token `do'
/usr/bin/disable-screenblanking.sh: line 3: `do'

```

Script:
```

#!/bin/bash
while:
do
xset dpms 0 0 0
sleep 600
done

```

---

### Post by albandy on 2013-02-22
there is a space between while and : 

```

while :
do
xset ........... and all the stuff
sleep 600
done

```

See the screenshot attached

---

### Post by demontager on 2013-02-22
Now it's running fine, but same error from cron
```

xset:  unable to open display ""

```
My base system is Lubuntu, if I put script to startup here /etc/xdg/lxsession as
@disable-screenblanking.sh
do i need do  export DISPLAY ?
 
Lubuntu keeps some startup scripts there, I put Skype, pidgin, thunderbird scripts to run in auto when system started
```

@lxpanel --profile Lubuntu
@xscreensaver -no-splash
@xfce4-power-manager
@pcmanfm --desktop --profile lubuntu
@/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
@x0vncserver -nowin
@pidgin
@skype_delay.sh
@thunderbird_delay.sh

```

---

### Post by albandy on 2013-02-22
If these applications are opened automatically when you log in trough the graphical environment, you don't need to put export DISPLAY nor xhost.

---

### Post by demontager on 2013-02-23
Seems working fine, but DPMS looks too picky to disable it.
When system started all has zeros, but when i leave system idle it back to 
```

DPMS (Energy Star):
  Standby: 7200    Suspend: 7200    Off: 14400
  DPMS is Disabled


```
So after 10 mins monitors off again.

---

