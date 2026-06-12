---
title: "Ventrilo Server On Boot"
date: 2007-08-03
forum: General Help
---

### Post by Cable on 2007-08-03
I have a Ventrilo server set up on my computer (which works perfectly fine when started manually) and would like to have it start on boot.  I found a script (on the Ventrilo website) that appears to be for this purpose but I have no idea what to do with it.  I've found a couple of other threads about this sort of thing but they lost me (such as [this one]("http://ubuntuforums.org/showthread.php?t=229652")).  If someone could guide me through this that would be amazing.  The script I found looks like this (same script as in the linked thread), and is simply called "ventrilo."
```

#!/bin/sh
#Ventrilo Script v2.1.0_02 written by Crypt Keeper
#For ventrilo server v2.x

#Replace the values of VENPATH and VENSRV with your ventrilo path and server name. 
#Replace the value of VENUSER with the account name that ventrilo runs under.
VENPATH=/home/ventrilo
VENSRV=$VENPATH/ventrilo_srv
VENUSER=ventrilo

if [ "$UID" -ne 0 ]
then
        echo "You must be root to run this script"
        exit 64
fi

check_pid ()
{
if [ -e $VENPATH/$1.pid ]
then
	PID=`cat $VENPATH/$1.pid`
else
	PID=0
fi
}

start ()
{
echo ""
su $VENUSER -c "$VENSRV -f$VENPATH/$1 -d"
check_pid $1
if [ $PID -ne 0 ]
then
	renice -20 $PID
        echo ""
        echo "Ventrilo server on Port:"$1" Started."
        echo ""
else
        echo ""
        echo "ERROR Ventrilo server on Port:"$1" Failed to Start"
        echo ""
        exit 66
fi
}

stop ()
{
check_pid $1
if [ $PID -ne 0 ]
then
        kill $PID
        echo ""
        echo "Ventrilo server on Port:"$1" with PID:"$PID" Stopped."
        echo ""
else
        echo ""
        echo "ERROR Ventrilo server on Port:"$1" Not Running."
        echo ""
        exit 67
fi
}

noport ()
{
echo ""
echo "Invalid argument string"
echo "Please specify a port number"
echo "-h|--help for usage"
echo ""
exit 68
}

case $1 in
-h|--help)
        echo ""
        echo "Ventrilo Script by Crypt Keeper"
        echo "       start port#"
        echo "       stop port#"
        echo "       restart port#"
	echo "       status port#"
	echo ""
        ;;
start)
        if [ $# -eq 2 ]
        then
		start $2
	else
        	noport
        fi
        ;;
stop)
        if [ $# -eq 2 ]
        then
		stop $2
	else
        	noport
        fi
        ;;
restart)
        if [ $# -eq 2 ]
        then
		stop $2
		start $2
	else
		noport
        fi
	;;
status)
        if [ $# -eq 2 ]
        then
		check_pid $2
		if [ $PID -ne 0 ]
		then
			echo ""		
			echo "Ventrilo server on Port:"$2" -Running- with PID:"$PID
			echo ""
		else
			echo ""
			echo "Ventrilo server on Port:"$2" -Not Running-"
			echo ""
		fi
        else
                noport
        fi
        ;;

* )
        echo ""
        echo "Invalid Argument $1"
        echo "-h|--help for usage"
        echo ""
        exit 69
        ;;
esac
exit 0

```
There was also another file included called "S99ventrilo."  It looks like this...
```

#!/bin/sh
#Ventrilo script v2.1.0_02 written by Crypt Keeper
#For ventrilo server v2.x

#Path to ventrilo script
VENSCRIPT=/root/bin/ventrilo

$VENSCRIPT start 3784
#$VENSCRIPT start 4000
#$VENSCRIPT stop 3784

```
What do I change in these files and where do I put them?  I just need a guiding hand here to get this server to start on boot.  I would greatly appreciate it!

---

### Post by prodezigner on 2007-08-03
I'll try to help ya out the best I can... for the low one-time payment of... NOTHING!

Alright, first things first, you need to copy that ventrilo script (not the s99 one) to a directory... I'd recommend ~/bin for ease of usage.

Also make sure you have the server installed to /home/ventrilo (make a user for it) user System and Preferences and then goto Users and groups.

edit the s99 file's path instead of VENPATH=/root/bin/blahblahblah to read VENPATH=/bin/ventrilo

COPY the saved s99 file to /etc/rc3.d

Reboot and in a terminal type in ventrilo -h to see if ya rollin'.

Hope this helps, if not I'll help further if needed.

---

### Post by Cable on 2007-08-03
When I create the user, it wants me to make a password for the user as well.  As far as I can tell, there is no way to create a user without a password.  What shall I do here?  Also, there is a drop down menu called "Profile" with Desktop User, Administrator, and Unprivileged as choices.  What do I choose?  Last, should I change anything under the User Privileges tab?

---

### Post by xarmian on 2007-08-04
While I've never used ventrilo, this is likely to be the same as any other service.. so since ventrilo will be started as a service, don't worry about the password, make it something random.. Also, set it to an unprivileged account, and i'd assume you can leave the privileges as-is.  Then change to the "Advanced" tab and change the shell to "/bin/false"

In reality you should set it to no password.. this would mean editing the shadow file (/etc/shadow) with sudo (such as 'sudo pico /etc/shadow' or 'sudo gedit /etc/shadow'), find the line starting with 'ventrilo' and remove the random sequence of characters between the following colon and the next colon and replace it with an "!".. for example it might look like:
> 
ventrilo:$1$mPe38urhfkjhf84yiuhfdnfcDFKDFdfdk:13727:0:99999:7:::

change it to:
> 
ventrilo:!:13727:0:99999:7:::

Good luck.

-Dave

Edit: the forum software replaced the important section with an icon.  in place of that icon it should look like:

: ! :   <--- with no spaces

---

### Post by Cable on 2007-08-04
Alrighty...

The user "ventrilo" is set up with no password.
All Ventrilo server files are located at /home/ventrilo.
The file "S99ventrilo" is located at /etc/rc3.d with VENSCRIPT=/bin/ventrilo.
The file "ventrilo" is located at /bin.

My server is configured to use port 3784, so in the S99ventrilo file the default line ($VENSCRIPT start 3784) should work, correct?

When I rebooted my computer, Ventrilo was not running.  I ran "ventrilo -h" and got
```

Ventrilo Script by Crypt Keeper
       start port#
       stop port#
       restart port#
       status port#

```so then i typed "ventrilo status 3784" and got
```

Ventrilo server on Port:3784 -Not Running-

```so then I typed "ventrilo start 3784" and got
```

ERROR Ventrilo server on Port:3784 Failed to Start

```So this means that the script file is accessible and working, but for some reason it can't start the server.  Am I correct?  Just for reference, here is what the readme file included with the script says, just in case it would help at all.
```

Ventrilo Script v2.1.0_02 written by Crypt Keeper
For ventrilo server v2.x

How to use these scripts:

1. Edit the ventrilo script and change VENPATH,
VENSRV, and VENUSER to match your setup (it is
currently setup for linux and the install path
and user account specified in the ventrilo_srv.htm)

2. Copy the ventrilo script to /root/bin
If you decide to put the ventrilo script somewhere
else there are two things to note: 1. Placing
the ventrilo script in the path makes life easier
and 2. You will need to change the VENSCRIPT
variable in S99ventrilo to the path where you
installed the ventrilo script if you use it to
start at ventrilo at boot/runlevel

3. Edit S99ventrilo to start or stop the servers
that you want and then copy it to the runlevel you
would like those actions to occur on (ie /etc/rc.d/rc3.d/
for startup at boot)

4. If you copied S99ventrilo to the rc3.d directory you 
can safely remove the ventrilo startup commands from your
rc.local

5. As long as root bin is in you path you can now type
ventrilo -h to get the usage of ventrilo script

Have Fun
  Crypt Keeper

```I have no idea what to do next.  Help?  :-)

---

### Post by xarmian on 2007-08-04
hmmm.. try starting it with sudo (sudo ventrilo start 3784) and see if the service starts that way?

---

### Post by Cable on 2007-08-04
Just tried with sudo and got the same result.  :-(

---

### Post by Cable on 2007-08-06
*Bump*
Any more ideas?

---

### Post by Cable on 2007-08-17
Nothing?  Anything at all?

---

### Post by godlike on 2007-12-20
I dont know if this would matter or not but did ya chmod the vent files so that the ventrillo user is allowed to execute them?

---

### Post by godlike on 2007-12-20
Also I found this howto on how to have it load chroot on a x64 system but im sure u could skip the 64 bit parts and use the script to get it to load easy enough  

[http://www.howtoforge.com/ventrilo_voice_communication_server_ubuntu_feisty_amd64](http://www.howtoforge.com/ventrilo_voice_communication_server_ubuntu_feisty_amd64)

---

