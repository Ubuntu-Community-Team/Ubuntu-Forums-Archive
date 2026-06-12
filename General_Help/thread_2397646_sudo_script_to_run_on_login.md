---
title: "sudo script to run on login"
date: 2018-08-01
forum: General Help
---

### Post by Robbyx on 2018-08-01
I need to run the following script automatically on startup:

sudo /usr/local/xxx.ac/bin/run_ubuntu.s

Hoping to use crontab to run it just after login I created a file called robin (ie  my username)  in /etc/cron.d which contained:


@reboot root /usr/local/xxx.ac/bin/run_ubuntu.sh

I restarted Ubuntu 16.04. The script was not run. 

Note that I also tried @reboot robins  /usr/local/xxx.ac/bin/run_ubuntu.sh

Could you please suggest what I have done wrongly.

---

### Post by TheFu on 2018-08-01
You cannot run any GUI programs at reboot.  Those must wait until an end-user has a login GUI session.
If you post the script, we might see other things.

---

### Post by 0xd3bugd on 2018-08-02
You can always add a program to start by adding the following on your crontab. [COLOR=#242729][FONT=Consolas]@reboot perl /path/script[/FONT][/COLOR]
Start up applications is another option on Ubuntu.

---

### Post by TheFu on 2018-08-02
> **0xd3bugd said:**
> You can always add a program to start by adding the following on your crontab. [COLOR=#242729][FONT=Consolas]@reboot perl /path/script[/FONT][/COLOR]
Start up applications is another option on Ubuntu.

Assuming it is a perl script, as opposed to python, bash, ruby, tk, tcl, or 20 others.

---

### Post by Robbyx on 2018-08-04
> **TheFu said:**
> You cannot run any GUI programs at reboot.  Those must wait until an end-user has a login GUI session.
If you post the script, we might see other things.
Here is the script. It would be great if the script could be run automatically, so that the app loaded on startup and I then filled in the fields in  the app manually.

#!/bin/sh
thisscript=`basename "$0"`
appname=`basename $0 | sed s,\.sh$,,`
#echo appname: $appname
#echo thisscript: $thisscript

dirname=`dirname $0`
tmp="${dirname#?}"

if [ "${dirname%$tmp}" != "/" ]; then
    dirname=$PWD/$dirname
fi
LD_LIBRARY_PATH=$dirname

#
xhost si:localuser:root

# make sure only root can run our script
#echo "id:""$(id -u)"
if [ "$(id -u)" != "0" ]; then
   echo "id:""$(id -u)"" this script must be run as root" 1>&2
   echo "  try gksu + "$thisscript 

   #for ubuntu 17.10 - not help
   #xhost +

   # gksu - not all good / not for all linux?
   sudo $dirname/$thisscript "$@"
   #gksu $dirname/$thisscript "$@"
   echo "  "
   echo "  " "id:""$(id -u)" " completed"
   exit 1
fi


echo "id:""$(id -u)"" user is root => can start app"


#openssl libs
if [ `getconf LONG_BIT` = "64" ]
then
    echo "64-bit os => openssl64 dir"
    LD_LIBRARY_PATH="$LD_LIBRARY_PATH/openssl64:$LD_LIBRARY_PATH"
else
    echo "32-bit os => openssl32 dir"
    LD_LIBRARY_PATH="$LD_LIBRARY_PATH/openssl32:$LD_LIBRARY_PATH"
fi


echo LD_LIBRARY_PATH: $LD_LIBRARY_PATH

export LD_LIBRARY_PATH

# fix bug "Could not connect to any X Display" 
#xhost +

#
$dirname/vst.com "$@"

xhost -

---

### Post by TheFu on 2018-08-04
Whenever posting code here, please, please, use "code tags" so formatting is maintained. Things line up that way. The harder stuff is to read the more likely problems will be missed or people just won't look at it.   Adv Reply (#) or Go Advanced does it.  Please edit that post.

No need to use sudo in this script if it is run from the root contrab or the system crontab.  Those already run with root permissions.
Running **any** GUI program as root is a terrible, terrible, terrible, terrible idea.  It is bad for security because anyone that hacks it gains root and X11 isn't exactly known for security.  Be certain you lock down all X11 networking from all outside interference.

gksu is deprecated.

You are clearing the LD_LIBRARY_PATH at the beginning when you set it to a single directory.  That probably isn't what you want.  I suspect you really mean to prepend or append that directory to the base LD_.... path.

You can set and export variables in 1 command.

If the GUI program isn't interactive, you can run it using the xvfb tool.  I've had to use it for some Oracle software, but really using a non-GUI mode program would be 1000x better.

17.10 support ended last month and the default display wasn't X11, it was Wayland which would cause problems.

I'm not certain, but it looks like you are mixing bash-only commands with Bourne shell commands. Probably best to just use bash for the interpreter.

Whenever running scripts, especially from cron, it is a best practice to exactly specify the programs - each of them - with the full path.  Never trust the PATH environment if you don't fully control it.

The formatting really isn't helping me.

---

### Post by Robbyx on 2018-08-05
As requested I now submit the actual script as in quotes. This is a commercially provided but beta script for the loading of a vpn service. What I want at this stage is to be have a reminder that I should load the vpn service when I have started my computer in the morning. In due course the vpn company will change their script.

The company's original comments when I complained that an aspect was not working if I started the script from the start applications menu was that it was not designed to work from the start apps because it does not have sufficient permissions when started that way. They told me that the right way was to start it was via the terminal as quoted above. I felt the support department was not understanding what I wanted as I found discussions that indicated that a script can be run with root permissions  from startup  When I pushed further I was informed:

> 
The log shows that you don't have permissions. You must run at as root with sudo. 

it isn't meant to be started automatically at this time. It's still in beta, requires improvements. Once some more important issues will be addressed, we'll look into adding a working option to start it automatically.

...it isn't about rights, is about a TTY that's required.
This is something that our devs will implement in a new version in the near future. As it is now, we can't provide support for it. It wasn't intended by design yet to be used on auto-start.



```
#!/bin/sh
thisscript=`basename "$0"`
appname=`basename $0 | sed s,\.sh$,,`
#echo appname: $appname
#echo thisscript: $thisscript

dirname=`dirname $0`
tmp="${dirname#?}"

if [ "${dirname%$tmp}" != "/" ]; then
    dirname=$PWD/$dirname
fi
LD_LIBRARY_PATH=$dirname

#
xhost si:localuser:root

# make sure only root can run our script
#echo "id:""$(id -u)"
if [ "$(id -u)" != "0" ]; then
   echo "id:""$(id -u)"" this script must be run as root" 1>&2
   echo "  try gksu + "$thisscript 

   #for ubuntu 17.10 - not help
   #xhost +
#!/bin/sh
thisscript=`basename "$0"`
appname=`basename $0 | sed s,\.sh$,,`
#echo appname: $appname
#echo thisscript: $thisscript

dirname=`dirname $0`
tmp="${dirname#?}"

if [ "${dirname%$tmp}" != "/" ]; then
    dirname=$PWD/$dirname
fi
LD_LIBRARY_PATH=$dirname

#
xhost si:localuser:root

# make sure only root can run our script
#echo "id:""$(id -u)"
if [ "$(id -u)" != "0" ]; then
   echo "id:""$(id -u)"" this script must be run as root" 1>&2
   echo "  try gksu + "$thisscript 

   #for ubuntu 17.10 - not help
   #xhost +

   # gksu - not all good / not for all linux?
   sudo $dirname/$thisscript "$@"
   #gksu $dirname/$thisscript "$@"
   echo "  "
   echo "  " "id:""$(id -u)" " completed"
   exit 1
fi


echo "id:""$(id -u)"" user is root => can start app"


#openssl libs
if [ `getconf LONG_BIT` = "64" ]
then
    echo "64-bit os => openssl64 dir"
    LD_LIBRARY_PATH="$LD_LIBRARY_PATH/openssl64:$LD_LIBRARY_PATH"
else
    echo "32-bit os => openssl32 dir"
    LD_LIBRARY_PATH="$LD_LIBRARY_PATH/openssl32:$LD_LIBRARY_PATH"
fi


echo LD_LIBRARY_PATH: $LD_LIBRARY_PATH

export LD_LIBRARY_PATH

# fix bug "Could not connect to any X Display" 
#xhost +

#
$dirname/xxx.com "$@"

xhost -

echo ""
echo "id:""$(id -u)" " completed"
   # gksu - not all good / not for all linux?
   sudo $dirname/$thisscript "$@"
   #gksu $dirname/$thisscript "$@"
   echo "  "
   echo "  " "id:""$(id -u)" " completed"
   exit 1
fi


echo "id:""$(id -u)"" user is root => can start app"


#openssl libs
if [ `getconf LONG_BIT` = "64" ]
then
    echo "64-bit os => openssl64 dir"
    LD_LIBRARY_PATH="$LD_LIBRARY_PATH/openssl64:$LD_LIBRARY_PATH"
else
    echo "32-bit os => openssl32 dir"
    LD_LIBRARY_PATH="$LD_LIBRARY_PATH/openssl32:$LD_LIBRARY_PATH"
fi


echo LD_LIBRARY_PATH: $LD_LIBRARY_PATH

export LD_LIBRARY_PATH

# fix bug "Could not connect to any X Display" 
#xhost +

#
$dirname/xxx.com "$@"

xhost -

echo ""
echo "id:""$(id -u)" " completed"
```

---

### Post by Robbyx on 2018-08-06
> **TheFu said:**
> You cannot run any GUI programs at reboot.  Those must wait until an end-user has a login GUI session.
If you post the script, we might see other things.

I have added more comments to the thread arising from TheFu's last comments.

---

