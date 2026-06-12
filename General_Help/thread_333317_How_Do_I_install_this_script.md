---
title: "How Do I install this script?"
date: 2007-01-07
forum: General Help
---

### Post by Duffy on 2007-01-07
I have instructions for installing a script to start and stop a server application. The problem is that the instructions call for a command used in RedHat and the command is not available in Ubuntu/Kubuntu.  I tried the update-rc.d command and cannot get it to work.  Here are the instructions for the script install:

>>>There is a 'sambar-inetd' init-script in the config directory that can be used to automatically start and stop the server when the machine boots/shuts down. Alternatively, from a shell window, 'cd' to the 'bin' directory and start the server using the command: ./server. Traditionally on UNIX type systems, init-scripts are copied to the /etc/init.d/ directory, and then to configure the init-script to run as a service when the machine boots, one executes the following commands, once each:

/sbin/chkconfig --add sambar-inetd
/sbin/chkconfig --level35 sambar-inetd on

The first command instructs the system to install the script that was placed in /etc/init.d/ to be installed as a service; the second command tells the system that the service should be automatically started when the system is in run levels 3 (non-graphical, multiuser, networking enabled) and 5 (graphical, multiuser, networking enabled). (run level 5 is the default on most Linux distros).<<<

I have placed the script (sambar-inetd) into the /etc/init.d/ directory and that's as far as I have been able to get.

Thanks,

Duffy

---

### Post by Koybe on 2007-01-07
```
update-rc.d sambar-inetd default 35
``` should do the work.

---

### Post by Jussi Kukkonen on 2007-01-07
First, may I suggest you look once again if the software you look for is available as a Ubuntu or Debian package (preferably in a repository), that will make life easier. If that's not an option, update-rc.d is what you are looking for, but you can also do this manually...

**update-rc.d sambar-inetd defaults** should do what you want, see man *update-rc.d* if you want to change the runlevels (but be aware that the info you had on runlevels is not correct on Ubuntu or Debian).

If you want to things by hand, add symlinks to your script in /etc/rcX.d, where X is the runlevel, there should be plenty of examples there (and READMEs).


EDIT: as a combination koybes and my suggestions, this is probably closest to the command you want:
```
update-rc.d sambar-inetd defaults 35
```

---

### Post by Duffy on 2007-01-07
It does not seem to be working. This is what I am getting in the terminal window:

duffy@linux:~$ update-rc.d sambar-inetd default 35
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults|multiuser [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force

So I tried the same thing with -n after rc.d as above and it returned the same thing.

---

### Post by Koybe on 2007-01-07
defaults... not default.... my mistake. Jussi is right.

---

### Post by Duffy on 2007-01-07
Thanks for the correction. Well it appears to have installed the script into all the rc*.d directories, but the script does not appear to be working.  Plus, once the script is installed, I should be able to start the server via /etc/init.d/sambar-inetd start and it will not work. If I CD to /etc/init.d and then try to start the script it tells me I do not have permission even though I am at the SU level (root).

Anyone out there available to take a look at the script and figure this out? I would be more than happy to reimburse you for your time via a Paypal payment.

BTW, since the script is not working as it is, is there a way to remove it similar to the way it was installed?

Thanks,

Duffy

---

### Post by Duffy on 2007-01-07
Here's what the script looks like:

#! /bin/sh
#
# sambar          Start/Stop Sambar Server.
#
# chkconfig: - 95 15
# description: Sambar Server ([www.sambar.com](www.sambar.com))
# processname: server
# config: <SambarInstDir>/config/*

INITD=/etc/rc.d/init.d
. $INITD/functions

. /etc/sysconfig/network

# Check that networking is up.
# Pretty much need it for postmaster.
[ "${NETWORKING}" = "no" ] && exit 0
  
RETVAL=0
PROGDIR=/usr/local/sambar/bin

start() {
	setenv
	echo -n $"Starting $PROGDIR: server"
	cd $PROGDIR; ./server &
	RETVAL=$?
	echo
	[ $RETVAL -eq 0 ] && touch /var/lock/subsys/sambar
	return $RETVAL
}

stop() {
	echo -n $"Stopping $PROGDIR: server"
	killproc watcher
	killproc server
	RETVAL=$?
	echo
	[ $RETVAL -eq 0 ] && rm -f /var/lock/subsys/sambar
	return $RETVAL
}

restart() {
	stop
	start
}

setenv() {
        if [ ! -z "$JAVA_HOME" ]; then
                BASE=$JAVA_HOME
                PATH="$PATH:$BASE/bin:$BASE/jre/bin/"
                CLASSPATH=.:$BASE/rt:$BASE/jre/lib:/usr/local/sambar/lib
                LD_LIBRARY_PATH="$LD_LIBRARY_PATH:/usr/X11R6/lib:$BASE/jre/lib/i386:$BASE/jre/lib/i386/server"

                echo "Using $BASE"
                export PATH CLASSPATH LD_LIBRARY_PATH

        elif [ -x "/usr/java/" ]; then
                BASE="/usr/java"
                PATH="$PATH:$BASE/bin:$BASE/jre/bin/"
                CLASSPATH=.:$BASE/rt:$BASE/jre/lib:/usr/local/sambar/lib
                LD_LIBRARY_PATH="$LD_LIBRARY_PATH:/usr/X11R6/lib:$BASE/jre/lib/i386:$BASE/jre/lib/i386/server"

                echo "Using $BASE"
                export PATH CLASSPATH LD_LIBRARY_PATH

		elif [ -x "/usr/local/java/" ]; then
                BASE="/usr/local/java"
                PATH="$PATH:$BASE/bin:$BASE/jre/bin/"
                CLASSPATH=.:$BASE/rt:$BASE/jre/lib:/usr/local/sambar/lib
                LD_LIBRARY_PATH="$LD_LIBRARY_PATH:/usr/X11R6/lib:$BASE/jre/lib/i386:$BASE/jre/lib/i386/server"

                echo "Using $BASE"
                export PATH CLASSPATH LD_LIBRARY_PATH
        else
                echo "JAVA_HOME NOT SET; JAVA NOT LOADING"
        fi
}

# See how we were called.
case "$1" in
  start)
        start
        ;;
  stop)
        stop
        ;;
  status)
        status postmaster
        ;;
  restart)
        restart
        ;;
  *)
        echo $"Usage: $0 {start|stop|restart}"
        exit 1
esac

exit 0

---

### Post by koenn on 2007-01-07
> f I  .. try to start the script it tells me I do not have permission even though I am at the SU level (root)

That's probably because you did not set the 'execute' permission. 
do 
```

chmod 770 /etc/init.d/sambar-inetd

```
and see if it works. 

---
```
I would be more than happy to reimburse you for your time via a Paypal payment.
```
you can make a donation to MSF ( [http://www.msf.org/msfinternational/donations/](http://www.msf.org/msfinternational/donations/) ), or to any FOSS project you like. 
I spend about 30 seconds on it - I leave the amount to your discretion.

---

### Post by Duffy on 2007-01-07
Thanks for that suggestion, but it still does not work. I wonder if the script has other "errors" or differences since it was written for a RedHat system. For instance, at the beginning it checks for a network connection. The directory etc/sysconfig cannot be found in Ubuntu/Kubuntu.  So maybe that causes it to fail.

This autostart is one area Windoz has it over Linux. On Windoz I just drop the program icon into the startup folder and it's done. This is a major pain trying to figure this out. I have spent too many hours over four + weeks trying to get this to work on Linux.

I'll be happy to pay or make a donation if someone with a heck of a lot more knowledge than me can come up with the answer.

Thanks,

Duffy

---

### Post by koenn on 2007-01-07
> This autostart is one area Windoz has it over Linux. On Windoz I just drop the program icon into the startup folder and it's done. This is a major pain trying to figure this out. I have spent too many hours over four + weeks trying to get this to work on Linux.
you're trying to install a package that is obviously made for Redhat, and you expect it to work on Ubuntu. Try installing the MS Internet Information Server that comes with Windows 2003 server on Windows XP or 2000 Pro, and see how well that works - and that's all software from the *same* firm. 

fist things first: 
I assume the script runs after you made it executable ?

If so, just run it - if anything returns an error, post it, then we'll see how bad it actually is.

---

### Post by Duffy on 2007-01-07
No, Sambar Server was not meant to run only on RedHat. It was developed to run on any Linux platform. When I start the server manually (cd /usr/local/sambar/bin then giving the command ./server), it runs just fine and without any issues. The autostart script was the only thing written for RedHat and because of the differences between rpm and Debian, I have having issues with the script and the installation of the script since all directions for this procedure were written for the RedHat system.

To the question you asked, when I try to run the script manually, it does not work even after changing the permissions as you outlined. It gives me back the same error telling me I don't have permission.

I need the autostart to work so if I am not around, and someone else needs to restart the server, then Sambar will start after the server is rebooted without any intervention by the person performing the reboot.

---

### Post by Jussi Kukkonen on 2007-01-07
The script seems to have several non-debian things (or at least stuff I don't recognise), so you are correct the problem is there.

You should probably write your own init.d-script (or modify the provided one) -- a very simple one might be fine.

---

### Post by koenn on 2007-01-07
I never said Samba Server was meant to run on Redheat only. I said the **package** (i.e. the rpm, containing the binaries + whatever scripts and config files needed to get it to work) are clearly designed for a Redhat (or RedHat-like) system. These subtle differences actually matter. 

Where did you get it anyway ? from the website, it looks as if  the guy is currently only developing a Windows version. And to be obnoxious : these startup scripts are closer to the Windows Registry run, runexec, runservice, .. keys than to 'just drop it in the startup folder'.

> 
It gives me back the same error telling me I don't have permission.
Could you be a bit more precise?  **post** they actual error ?  e.g. copy and paste it  ?
Assuming you have execute permission, the error may be coming from a command within the script, and then it would be helpfull to actually see what's going on. 

what does it say when you run
```
sudo /usr/local/sambar/bin/server
```

---

### Post by Duffy on 2007-01-07
Here's what I get when I try to start if from the script:

root@linux:/home/duffy# /etc/init.d/sambar-inetd start
.: 11: Can't open /etc/rc.d/init.d/functions

When I try and start it manually as outlined in Sambar's linux documentation, it works just fine:

root@linux:/home/duffy# cd /usr/local/sambar/bin
root@linux:/usr/local/sambar/bin# ./server
Sambar Server INFO:  Server root directory set to: /usr/local/sambar
Sambar Server V7.0X running on 'linux' [port 80]
(c) Copyright Tod Sambar 1995-2006
All rights reserved.
Commercial distribution of this software prohibited.
mailto: [email]support@sambar.com[/email] for product information

I am not getting the same permissions error I got before so I cannot duplicate it.  The current error message I am getting tells me the script may be starting to run as the /etc/rc.d is from the script and rc.d does not appear in Ubuntu/Kubuntu as I can find - so it must be coming from the script.

If I want to play around with the script, is there a way to uninstall the script that I just installed so I can change the "base" script and then reinstall?

I was thinking of deleting the network check from the script and the "rc.d" should be changed to something but I am not sure what.

Thanks,

Duffy

---

### Post by koenn on 2007-01-07
yep, it's running, and i was also thinking you could remove that whole "check network" thing - assuming you're network is OK you don't really need it. So just remove from the INITD line to the {NETWORKING} line (both included),

The rest is rather basic stuff to start stuff, then see if it actually started, so if there are too many redhat-specific commands there, we can leave thise out as well or replace them with debian / ubuntu statements. 

It's just a script, a text file with commands for the shell to execute, so you can add and delete    with a text editor, you don't need to install or uninstall. Just edit, save, and run it

best make a copy first - always a good idea. 

It's way past bedtime here so ..
Have fun. .

---

### Post by Duffy on 2007-01-07
Thanks, it finally works!  Not sure if it will do the autoshutdown, but deleting the script as you advised allowed Sambar to start when the system restarted, and that was the most important thing at this point. 

I would like to donate to FOSS - is there a link where you can donate via Paypal?

Thanks,

Duffy

---

