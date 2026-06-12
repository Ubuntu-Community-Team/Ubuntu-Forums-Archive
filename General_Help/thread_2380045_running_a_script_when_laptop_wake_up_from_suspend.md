---
title: "running a script when laptop wake up from suspend"
date: 2017-12-12
forum: General Help
---

### Post by monkeybrain20122 on 2017-12-12
Hi, I have a script that enables both edge scrolling and two finger scrolling on my touchpad (system settings' mouse and touchpad gui doesn't have option for edge) I put in it startup applications and it works as expected if I reboot or logout and then login. But it doesn't activate when laptop wakes from suspend in one of my laptops (on the other it works) Is there a way to make Ubuntu run it automatically when wakes from sleep?

Ubuntu 16.04.3 with the Unity desktop

Thanks.

P.S I remember settings used to have both edge and two finger as options but either edge doesn't work or only one is allowed (enable one disable the other), seems to be something inherited from gnome, whereas I can enable both from KDE's settings without extra work.

---

### Post by ajgreeny on 2017-12-12
Copy and save that script (for this suggestion I have called it scroll.sh) as **/lib/systemd/system-sleep/scroll.sh** and see if it is run after wakeup.

It is possible that you may need to add a sleep time with ```
#!/bin/bash
sleep 5;
your script command here
```
to allow the desktop to fully start, and the 5 seconds I show may be shortened, or not even needed, but you will have to test that yourself.

I have to run a similar kind of script on one system I use to get the network running after wakeup from suspend so that is where this idea comes from.
Give it a try and let us know if it works please.

---

### Post by monkeybrain20122 on 2017-12-12
> **ajgreeny said:**
> Copy and save that script (for this suggestion I have called it scroll.sh) as /lib/systemd/system-sleep/scroll.sh and see if it is run after wakeup.

It is possible that you may need to add a sleep time with ```
#!/bin/bash
sleep 5;
your script command here
```
to allow the desktop to fully start, and the 5 seconds I show may be shortened, or not even needed, but you will have to test that yourself.

I have to run a similar kind of script on one system I use to get the network running after wakeup from suspend so that is where this idea comes from.
Give it a try and let us know if it works please.

Hi, 

my script is 
```
#!/bin/bash
sleep 6
synclient VertEdgeScroll=1
synclient VertTwoFingerScroll=1
synclient HorizTwoFingerScroll=1
synclient HorizEdgeScroll=1
```

So I just copied it to /lib/systemd/system-sleep/, but it didn't work.

But in /lib/systemd/system-sleep/ I found a file called system76-nm-restart, it may address your problem of getting network to wake up
```
#!/bin/sh

# system76-driver: Universal driver for System76 computers
# Copyright (C) 2005-2016 System76, Inc.
#
# This file is part of `system76-driver`.
#
# `system76-driver` is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# `system76-driver` is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License along
# with `system76-driver`; if not, write to the Free Software Foundation, Inc.,
# 51 Franklin Street, Fifth Floor, Boston, MA 02110-1301 USA.

# Starting with 16.04, there are WiFi reliability issues when resuming from
# suspend, at least with certain WiFi cards.  In particular, this problem seems
# to effect Haswell generation cards like the 7260.  It does not seem to effect
# Skylake generation cards like the 3165, 8260.
#
# This seems fundamentally a user-space issue, not a kernel issue.
#
# This script is installed at /lib/systemd/system-sleep/system76-nm-restart.

set -e

if [ "$2" = "suspend" ] || [ "$2" = "hybrid-sleep" ]; then
    case "$1" in
        pre) true ;;
        post) sleep 1 && service network-manager restart ;;
    esac
fi

```

I tried to modify this by replacing  "service network-manager restart", with /home/monkeybrain/Scripts/touchpad.sh which is the path to my script, didn't work. Replacing it with the block
```
synclient VertEdgeScroll=1 &&
synclient VertTwoFingerScroll=1 &&
synclient HorizTwoFingerScroll=1 &&
synclient HorizEdgeScroll=1

```

didn't work either. Maybe some kind of user/permission thing?  Any idea?

Thanks.

---

### Post by monkeybrain20122 on 2017-12-16
bump

---

### Post by &amp;KyT$0P# on 2017-12-16
Does [this]("https://ubuntuforums.org/showthread.php?t=2372519&p=13690740&viewfull=1#post13690740") do what you want?

---

### Post by untrustytahr on 2017-12-16
> **monkeybrain20122 said:**
>  Maybe some kind of user/permission thing?  Any idea?



synclient needs an X server to connect to.

Make this your script and make it executable (substitute your user):

```
#!/bin/bash     

#title          :touchpad.sh
#description    :Hook script to enable edge and two finger scrolling when waking from suspend 
#author         :monkeybrain20122  
#date           :20171216
#version        :1      
#usage          :./touchpad.sh
#notes          :Script gets called from /lib/systemd/system-sleep
#============================================================================================================================================================


sleep 5
declare -x DISPLAY=":0.0"
declare -x XAUTHORITY="/home/<[COLOR=#ff0000]**your user**[/COLOR]>/.Xauthority"


synclient VertEdgeScroll=1 VertTwoFingerScroll=1 HorizTwoFingerScroll=1 HorizEdgeScroll=1
```

then you can call it from that system76 nm wakeup.

```
post) /path/to/your/script/touchpad.sh;;
```

---

### Post by monkeybrain20122 on 2017-12-17
> **untrustytahr said:**
> synclient needs an X server to connect to.

Make this your script and make it executable (substitute your user): ...




Hi, it works!. Thanks a lot!

---

### Post by vkapas on 2018-09-18
First, sorry for necroposting. But [**[COLOR=#000000]untrustytahr[/COLOR]**]("https://ubuntuforums.org/member.php?u=1895014")'s script did not work in my case.

I've create **touchpad.sh** file in **~/.config/autostart/**
```
user@pc:~/.config/autostart$ ll touchpad.sh
-rwxrwxr-x 1 user user 412 &#1089;&#1077;&#1085; 18 21:32 touchpad.sh*

user@pc:~/.config/autostart$ cat touchpad.sh

sleep 5

declare -x DISPLAY=":0.0"
declare -x XAUTHORITY="/home/user/.Xauthority"

synclient TapButton2=0
```

and create **touchpad** script in **/lib/systemd/system-sleep/**
```
root@pc:/lib/systemd/system-sleep# ll touchpad 
-rwxr-xr-x 1 root root 325 &#1089;&#1077;&#1085; 18 21:29 touchpad*

root@pc:/lib/systemd/system-sleep# cat touchpad 
#!/bin/sh
case $1 in
  pre)
    # Place your pre suspend commands here, or `exit 0` 
    # if no pre suspend action required
    exit 0
    ;;
  post)
    # Place your post suspend (resume) commands here, or 
    # `exit 0` if no post suspend action required
    /home/user/.config/autostart/touchpad.sh
    exit 0
    ;;

```

Script must disable right click on two finger click. It works fine if I run it directly but doesn't work *after suspend*. I really cant understart why.

---

### Post by Llewen on 2019-03-20
I realize this is an old thread, but I am also experiencing a similar issue.  I've googled how to run a script on resume and I've placed the script in /lib/systemd/system-sleep.  The script calls another script, and that script runs perfectly.  But when the system resumes, the script doesn't complete.  The reason why I've posted to this thread is that it appears to be some kind of permissions issue, as was the case in the op, however the declare lines don't do the trick.  What I'm trying to do is reload my g13d service because the lcd display reverts to default on resume.

In past attempts to get this to work I've tried running the scripts from ~/.local/bin (yes added to PATH), with and without the full path, if/then instead of case, sudo as my user, etc.  The best result I've been able to get is to get the g13d service to reload, but the scripts are supposed to use parameters to load configs for the device, but the configs won't load.  The g13 is a usb hid peripheral.  The exact same scripts perform flawlessly on boot using kde plasma autostart and I can run them from kde shortcuts or from the command line without issue.  I just can't get them to run on resume.  I've also tried the old systemd method for running commands on resume, with the same results.

Again, my guess is it is a really simple permissions issue, similar to the issue in the op.

/lib/systemd/system-sleep/g13_restart
```
#!/bin/bash

case $1 in
  post)
    /usr/local/bin/g13_start
    ;;
esac
```

/usr/local/bin/g13_start
```
#!/bin/bash

sleep 5
declare -x DISPLAY=":0.0"
declare -x XAUTHORITY="~/.Xauthority"

killall g13d
sleep 5 && /usr/local/bin/g13_config_last
sleep 5 && /usr/local/bin/g13_lcd_date
```

---

