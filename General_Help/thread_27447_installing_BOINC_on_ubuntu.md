---
title: "installing BOINC on ubuntu"
date: 2005-04-16
forum: General Help
---

### Post by Brad wilkinson on 2005-04-16
ok, I'm an utter noob when it comes to linux, i havn't used command line since the days of dos 6.whatever.

anyway, so I've got ubuntu 4.10 loaded on my pIII-800 with no problems, I've even got the smp-aware kernel running.

Now I'm trying to install the BOINC client, so I can run seti@home. I've downloaded the file required into brad/BOINC/ and gunzip'd it.

Then in a terminal window, (as root@dual-ubuntu /home/brad/BOINC/ ) i've tried to "chmod +x the executable" like the install instructions say (chmod +x boinc_.....) which doesn't return an error message, but doesn't return any sort of confirmation either. WTF is this supposed to be doing?

Anyway.

So next you need to run the executable. So I type in boinc_client -attach...(the rest), and hit return. Then I get the error message "bash: boinc_client: command not found". So it didn't work, by the look of it.

Can someone humor a newb and point me in the right direction?

(the instructions I'm following are from the berkeley website where you d/l the client from).

P.S. i've already got the client for windows XP up and running on my other machine, so it's not a network issue.

---

### Post by joshmachine on 2005-04-16
[QUOTE=Brad wilkinson]ok, I'm an utter noob when it comes to linux, i havn't used command line since the days of dos 6.whatever.

anyway, so I've got ubuntu 4.10 loaded on my pIII-800 with no problems, I've even got the smp-aware kernel running.

Now I'm trying to install the BOINC client, so I can run seti@home. I've downloaded the file required into brad/BOINC/ and gunzip'd it.

Then in a terminal window, (as root@dual-ubuntu /home/brad/BOINC/ ) i've tried to "chmod +x the executable" like the install instructions say (chmod +x boinc_.....) which doesn't return an error message, but doesn't return any sort of confirmation either. WTF is this supposed to be doing?

Anyway.

So next you need to run the executable. So I type in boinc_client -attach...(the rest), and hit return. Then I get the error message "bash: boinc_client: command not found". So it didn't work, by the look of it.

Can someone humor a newb and point me in the right direction?

(the instructions I'm following are from the berkeley website where you d/l the client from).

P.S. i've already got the client for windows XP up and running on my other machine, so it's not a network issue.[/QUOTE]
 Hello Brad,

Quick answer:

When you are in the directory where the "boinc_client" executable is type the following:

$ ./boinc_client -attach ..

If you interested in knowing the why of it, you can read further.

1.  The name of the "shell interpreter" (the thing which takes the commands you type on the command line and actually runs programs) is named "bash".  I will refer to it as bash from here on in. some commands (like 'ls' and 'cd' aren't even excecutables, they are 'shell commands' -- this is also the case for dos etc.

2. In order to run an program, the os has to be told that it is "executable" this is what the "chmod" command does.  This is a property of the file itself, and only has to be done once.

3. The error that you are getting is because you are typing a command that bash doesn't know about.  If you type a command at the prompt, bash has to look for it.  where does it look? this is where the "PATH" variable comes in.  this PATH variable is basically a list of directories seperated by a colon ":" . When you invoke a command bash looks in all of these directories. If it doesn find the command it gives you the error that you were seeing.
It doesn't look in the current directory you are in.  You can make it do this by prefixing the command by "./"  "." means the direcotry I'm in.  This says "Hey yo 'bash' don't look anywhere else you idiot.  the command is right here"

If you want to be able to run it on the command line without all this hullabaloo, you can tell bash where to look for it.  add the following like in your "~/.bashrc" file (open it in any text editor)

export PATH=~/boinc_dir:$PATH

launch a new command prompt and you should be able to run it from anywhere.

Cheers,
Josh

---

### Post by Brad wilkinson on 2005-04-16
t.y.v.m.

running cpu benchmarks a.t.m.

cheers,
Brad

(edit)

OK, i thought I read somewhere that BOINC was smp-aware, but now I've got it running, when I watch on the system resource monitor, only one cpu is running @ 100%, the other runs @ 3% (which is just the background stuff/OS i suppose). So did I miss a switch to run on the client or something?

Or do I need to run two "instances" of the client?

When I ran the benchmarks, it spotted both processors.

:confused:

(edit 2)

now its maxed out both processors. I suppose it was just downloading a second work unit.

yep.

(edit 3)

so is someone going to make BOINC into a package that we can add/remove from our build, like all the APACHE/DHCP and so on?

---

### Post by veehell on 2005-12-03
[my post from another thread]("http://ubuntuforums.org/showpost.php?p=541110&postcount=2")

ad_2cpu: it depends on project you are assigned and how you set your computing preferencies. It is really important. there are options for 2cpu machines, for sure (check your seti or "project" account first )

ad_manager: if you install the lates official one, 
it will create three executables and two short scripts
**run_client** (which run the process which really work on project)
**run_manager** (to manage your project/client behaving actually and how it progress)

client:include:>  **&& exec ./boinc &@**
manager:inclued:> **&& exec ./boincmng &@**

I set my project to participate 200 for SETI 100 for Einstein
max 75CPU time, max 75RAM, no more then 50% of free space
compute only at specified times (usually during day, when i am at work)
and in rest act as "nice" procces. (those setting get the client after attaching to project...so it is important to feed him with correct information)
Good luck.

---

### Post by bursto22 on 2005-12-03
Dont forget BOINC has a seperate Control Client so in order to run and view your activaties you will have two seperate things running

---

### Post by jeffdano on 2005-12-06
Don't forget to join up with the Ubuntu effort at SETI@home as well... we would sure appreciate some new recruits (or seasoned veterans).

[http://setiathome.berkeley.edu/team_display.php?teamid=116723](http://setiathome.berkeley.edu/team_display.php?teamid=116723)

---

### Post by tsbardella on 2005-12-06
I would like to know how to run Boinc from startup.  Also is there a benefit to having it run as daemon I found this page [service]("http://www.spy-hill.net/~myers/help/boinc/init.d-boinc")  - but I am clueless as to how to adapt it to Ubuntu or if I really need to.  

Thanks

---

### Post by veehell on 2005-12-06
Check Boinc official page, there are several tools, clients and so on in download section. Some of the guys from 3rdparty section, have written and posted inet.d script for boinc >[http://interreality.org/~reed/sw/boinc/]("http://interreality.org/~reed/sw/boinc/")

---

### Post by CybaCowboy on 2006-05-13
[QUOTE=joshmachine]When you are in the directory where the "boinc_client" executable is type the following:

$ ./boinc_client -attach ..[/QUOTE]

After typing in:
[i]cowboy@kubuntu:~$ chmod +x boinc_5.4.9_i686-pc-linux-gnu.sh
cowboy@kubuntu:~$ sudo ./boinc_client -attach ..[/i]

I am told:
*sudo: ./boinc_client: command not found*

Can anyone help me out?

---

### Post by dcstar on 2006-05-17
[QUOTE=tsbardella]I would like to know how to run Boinc from startup.  Also is there a benefit to having it run as daemon I found this page [service]("http://www.spy-hill.net/~myers/help/boinc/init.d-boinc")  - but I am clueless as to how to adapt it to Ubuntu or if I really need to.  

Thanks[/QUOTE]
I have just gone through the whole process of re-installing a new BOINC client (optimised for my AMD Athlon CPU) and just finished sorting out the way to get it to start up on boot (and also be able to run the GUI BOINC Manager!).

[LIST=1]
[*]Firstly the directory you run BOINC in should be owned by your account, make sure of this by the following terminal commands:
```
cd <Your BOINC directory>
sudo chown -R *
```
[*]Then you need the following file saved as "boinc.sh" in /etc/init.d (permissions 755):
```
#!/bin/sh

# boinc.sh - Control boinc.  Stop it/Start it/Restart it.  Originally 
#            meant to be used as a boot time script so that boinc starts
#            at boot time, but can be used any time.  For a boot time script
#            put this in /etc/init.d and make the appropriate links from
#            the appropriate run level areas (ie. /etc/rc3.d).  (This was
#            developed on RedHat 9 so I know what the boot areas are there.
#            It should also work on Solaris,  I'm not familiar with other
#            flavors of Linix/UNIX.)

# Author:    Charles Dennett/Rochester, NY USA.
# Email:     dennett@rochester.rr.com
# Date:      December 12, 2003.
# Version:   1.0
#
# History:   Version 1.1.  May 20. 2004.
#            Update stop function to use SIGTERM (15).
#            Version 1.2.  September 18, 2004
#
#            Comments about functions.
#	     Version 1.2   May 18 2006 - D.Clayton
#	     Modify for Ubuntu (Breezy) and add in a few minor changes (as well as rename to boinc.sh)
#
# Comment:   Copyright by the author.  Feel free to make modifications.
#            However, please keep these comments intact.

# Use:       To start:   boinc.sh start
#            To stop:    boinc.sh stop
#            To restart: boinc.sh restart
#            Status:     boinc.sh status

#
# Variables that will need to be configured.
#
#  BOINC_HOME:  The directory where boinc will run.  It should be run
#               in its own directory to keep its files and subdirectories
#               separate form others.
#
#  BOINC_BIN:   The full path to the boinc executable.
#
#  RUN_AS:      Username that boinc is to run as.
#
#  BOINC_OUT:   File to direct output from boinc.  If you don't want this,
#               set it to /dev/null.
#
#  BOINC_PARMS: Any command line parameters for boinc you wish to pass to 
#               it.  If you don't want any, simply use a null list ("").

BOINC_HOME=Your directory where the BOINC stuff is!
BOINC_BIN=Directory above/boinc
RUN_AS=Your User name
BOINC_OUT=/var/log/boinc.log
BOINC_ERR=error.log
BOINC_PARMS=""
#BOINC_PARMS="-allow_remote_gui_rpc"
#BOINC_PARMS="-return_results_immediately"
#BOINC_PARMS="-return_results_immediately -allow_remote_gui_rpc"

# Functions  This is for RedHat 9.  Don't know if it exists in other
# flavors of *nix.  If this does not work for you, simply comment it out
# and fix the stop function below so that it does not use the killproc
# function since killproc is defined in the functions file.  pkill might
# be a good choice.  Examine other boot scripts to see how they do it.

#. /etc/init.d/functions

# Init script function library.   This stuff is Red Hat specific,
# but if the functions are not found we create our own simple replacements.
# (The idea for replacing the functions comes from OpenAFS.  Thanks guys!)

if [ -f /etc/rc.d/init.d/functions ] ; then
        . /etc/rc.d/init.d/functions
else
        export PATH=/sbin:/bin:/usr/sbin:/usr/bin
        function echo_success () { echo -n "	[  OK  ]  " ; }
        function echo_failure () { echo -n "	[FAILED]  " ; }
        function echo_warning () { echo -n "	[WARNING] " ; }
	function killproc() {
	     PID=`pidof -s -x -o $$ -o $PPID -o %PPID $1` 
	     [ $PID ] && kill $PID ; }
fi

# su on Linux seems to need this to be set to work properly
export TERM dumb

# No other changes needed below this, most likely.

start()
{
   echo -n "Starting BOINC client daemon"
   eval $SU_CMD
        sleep 1 
        PID=`pidof -s -x -o $$ -o $PPID -o %PPID $BOINC_BIN`
	echo -n $PID
        if [ $PID ]; then
          echo_success
        else
          echo_failure
        fi
        echo 
}

stop()
{
          echo -n "Stopping BOINC client daemon:  "    
	  killproc $BOINC_BIN  && echo_success  || echo_failure
	  # clean up in any case
	  rm -f $BOINC_HOME/lockfile
	  echo
}

restart()
{
   stop
   echo  "Be patient.  Waiting 5 seconds for all to stop."
   sleep 5
   start
}

#----------------------------------------------------------------------------
#
# Start of mainline code
#

# If the user running this script is not the user we want boinc to run as, set
# up the su command so that we can become that user.  Note, we will have to 
# know this user's password.  If this script is run at boot time, it is root
# that is running this script and no password is required.

WHO_AM_I=`whoami`
CMD="$BOINC_BIN $BOINC_PARMS >> $BOINC_OUT 2>> $BOINC_ERR &"

if [ "$WHO_AM_I" != "$RUN_AS" ]; then
   SU_CMD="su $RUN_AS -c \"$CMD\""
else
   SU_CMD=$CMD
fi



# Go to where we want boinc to run

cd $BOINC_HOME

case "$1" in
  start)
         start
         ;;
  stop)
         stop
         ;;
  restart)
         restart
         ;;
  status)
         echo "What do I do here for status?"
         tail -20 $BOINC_OUT
         ;;
  *)
         echo "Usage:     `basename $0` start|stop|restart|status"
         exit 1
         ;;
esac
```
[*]Make a link of /etc/init.d/boinc.sh and move the link to /etc/rc2.d, rename the link as "S99boinc.sh" so it runs late in your boot-up process.
[*]Copy the link into /etc/rc0.d and rename it "K20boinc.sh", now also copy this new link into /etc.rc6.d (this will end BOINC cleanly when doing a shut down or reboot).
[*]Make the log file writeable by your account with:
```
sudo chmod 664 /var/log/boinc.log
```
[*]Create a desktop Launcher to the Manager with the following:
<Your directory where the BOINC stuff is>/run_manager
[/LIST]
Now (in theory), when you boot up your machine the BOINC Client should be run as your user, and the Manager should also function (with all the graphics working!).

---

### Post by dmizer on 2006-05-18
thanks david, but i run into nothing but problems with that script.

i've edited the script according to my setup but i am not sure about one setting ... the BOINC_BIN variable indicates it should be "Directory above/boinc", but i don't know what you mean by "above"

so my boinc directory is /home/dmizer/BOINC ... directory above would be /home/dimzer ... ?

also i have this problem:
```
$ sudo chmod 664 /var/log/boinc.log
$ sh boinc.sh start
Starting BOINC client daemonboinc.sh: line 92: /var/log/boinc.log: Permission denied
        [FAILED]  

```

---

### Post by dcstar on 2006-05-19
[QUOTE=dmizer]thanks david, but i run into nothing but problems with that script.

i've edited the script according to my setup but i am not sure about one setting ... the BOINC_BIN variable indicates it should be "Directory above/boinc", but i don't know what you mean by "above"

so my boinc directory is /home/dmizer/BOINC ... directory above would be /home/dimzer ... ?

also i have this problem:
```
$ sudo chmod 664 /var/log/boinc.log
$ sh boinc.sh start
Starting BOINC client daemonboinc.sh: line 92: /var/log/boinc.log: Permission denied
        [FAILED]  

```[/QUOTE]
Depending on the BOINC install program, it would probably be /home/dmizer/BOINC in your case.

As for the second problem, try:
```
sudo chmod 666 /var/log/boinc.log
```

---

### Post by dmizer on 2006-05-23
heh ... just saw this:
> #  BOINC_HOME:  The directory where boinc will run.  It should be run
#               in its own directory to keep its files and subdirectories
#               separate form others.
#
#  BOINC_BIN:   The full path to the boinc executable.
i need to pay attention more.  gonna give this a run through again when i get home.

---

### Post by dmizer on 2006-05-23
okay ... have everything edited as well as i can figure it.  had some issues with confusing bonic with boinc.

still can't get it to start though:
```
$ sh boinc.sh start
Starting BOINC client daemon    [FAILED]  
```
at least it doesn't fail with permissions now.  lol

how can i get this thing to run in gui so i can download new projects?  i don't care anymore if it starts on boot, just that i can run the thing in gui AND download projects.

as of right now, i have a work project pending, but it can't download it.

edit:  well, i got it to start.  i have no idea what i did exactly, but messing around in the gui commands menu got it to begin the download.

---

### Post by dcstar on 2006-05-23
[QUOTE=dmizer]okay ... have everything edited as well as i can figure it.  had some issues with confusing bonic with boinc.

still can't get it to start though:
```
$ sh boinc.sh start
Starting BOINC client daemon    [FAILED]  
```
at least it doesn't fail with permissions now.  lol

how can i get this thing to run in gui so i can download new projects?  i don't care anymore if it starts on boot, just that i can run the thing in gui AND download projects.

as of right now, i have a work project pending, but it can't download it.

edit:  well, i got it to start.  i have no idea what i did exactly, but messing around in the gui commands menu got it to begin the download.[/QUOTE]

The GUI will start it anyway, and so will:

/etc/init.d/boinc.sh start

---

### Post by Skip Da Shu on 2008-02-25
> **Brad wilkinson said:**
> 
so is someone going to make BOINC into a package that we can add/remove from our build, like all the APACHE/DHCP and so on?

Done... v5.10.8 is not out there as boinc-client and boinc-manager.

---

