---
title: "Fix For Kubuntu Boot Logging... Ubuntu Can Come Too"
date: 2008-05-28
forum: General Help
---

### Post by Big Pick on 2008-05-28
[COLOR=Blue]Astute readers will note that this is indeed my first post on these shiny Ubuntu Forums. Consider this the first step in reforming my "take without recompense" ways.[/COLOR]

**Abstract:**
In days gone by, a pet peeve with my Ubuntu install was the total inability to log the output of init.d scripts (those messages that scroll by really fast during boot and report either "OK" or "failed!"). A simple thing, but an indispensable tool for troubleshooting and system maintenance. Don't be stuck wondering if those "failed!" messages that flash past you are important, sometimes they are, but more often than not they are sure sign of a useless daemon that is just causing trouble and sucking up valuable resources and boot time; in other words, a perfect candidate for removal. Well, I have a solution, and I am finally getting up off my lazy ***--metaphorically speaking, I'm still quite sedentary at the moment--to donate this information back to the community from which I have leeched so much.
[COLOR=Red]
WARNING: I am crazy like a fox and a college student, which makes for high volatility. I am also an engineer, hence the layout of this post. Finally, I am illiterate, so the well educated among you will immediately spot all of my literary failings including the above abstract, which is more of a sales pitch.[/COLOR]

**Introduction:**
Things weren't always so dysfunctional in boot-land, they were a little less dysfunctional. Back in "the-day" (i.e. pre-Edgy 6.10) Ubuntu was a strictly 'sysvinit' affair and, therefore, had all the nice little 'sysvinit' tools installed by default. Boot logging still didn't really work--for reasons we will cover in a bit--but at least we had a homogeneous boot environment.

In Edgy 6.10, the 'upstart' system started to be installed by default. 'upstart' is one of those fun little programs that improves upon the *status quo*, adds lots of shiny features, cures cancer, and doesn't yet work. Instead, we have been using it in "compat-mode" with 'sysvinit'. Under 'upstart', boot logging was originally handled by a program called 'logd', however, this is no longer the case and 'logd' doesn't actually do much of anything as far as I can tell. Its all very mystical and nebulous and if I wasn't so lazy I would find the links to the launchpad bug entries that explain why these things don't do anything and why they are superior to 'sysvinit' and are included in Ubuntu.
[COLOR=Red]
WARNING: I am prone to endless ranting on issues which I have no experience or authroity.[/COLOR]

The 'sysvinit' logging program, which 'logd' was supposed to replace, 'bootlogd', has its own set of problems. Among them is an inability to handle any but the most basic terminal control sequences such as *newline* and *tab*. Perfectly sufficient for logging the basic script *echo* or program *printf* but totally incapable of interpreting the advanced *tput* generated control sequences used by the overwhelming majority of init.d scripts to make their output fancier. Whatever 'bootlogd' can't handle on its own, it dumps directly to the log file, creating a nigh unreadable mess that does little to assist in the troubleshooting of boot problems. It is for this reason that 'bootlogd' is disabled by default in most distributions. 

Despite its shortcomings, 'bootlogd' can be made to work perfectly with a few lines of script and without reinventing the wheel--something I do enough of already normally so I am grateful for the respite.

[COLOR=DarkOrange]P[/COLOR][COLOR=Yellow]R[/COLOR][COLOR=DarkOrchid]E[/COLOR][COLOR=Cyan]T[/COLOR][COLOR=DarkRed]T[/COLOR][COLOR=Lime]Y[/COLOR] [COLOR=Red]C[/COLOR][COLOR=DimGray]O[/COLOR][COLOR=Sienna]L[/COLOR][COLOR=Blue]O[/COLOR][COLOR=PaleGreen]R[/COLOR][COLOR=Olive]S[/COLOR]

[COLOR=Red]WARNING: Did I mention I was ADHD?[/COLOR]

**Step 1: Getting 'bootlogd'**
One extra little annoyance blocking our path is 'bootlogd' being contained in the 'sysvinit' package. This packaged just so happens to conflict with the 'upstart' package, which is a dependency of several other important packages including 'ubuntu-minimal'. And there was great rejoicing and dancing in the streets! As useless as upstart currently is, I was unwilling to unleash the ****-storm of breakage that would result from trying to completely regress back to 'sysvinit'. 

The far easier option--and therefore more attractive to the chronically lazy such  as myself--is to just compile it directly from source. (Version may vary from the example of course.)

```
apt-get source sysvinit
cd sysvinit-2.86.ds1/src/ 
make
sudo make install
```You can be more selective with your make targets if you so choose but it isn't necessary and there are some cross-dependencies. 

**Step 2: Scriptage**
Like everything on our systems, despite the valiant efforts of the 'upstart' devs, 'bootlogd' starts and ends with init scripts. I sat down and rewrote the scripts for 'bootlogd' during my attempts to resolve this issue--and out of the belief that I could do it better of course--but ended up with something very similar to original anyway with one or two minor improvements. It is important to note the use of the plural "scripts", 'bootlogd' does indeed require two scripts rather than just one like every other program because it is a "special case", a programmer's favorite term. The two scripts are as follows:

**/etc/init.d/bootlogd:**
```
#! /bin/sh
### BEGIN INIT INFO
# Provides:          bootlogd
# Required-Start:    mountdevsubfs
# Required-Stop:
# Default-Start:     S
# Default-Stop:
# Short-Description: Boot logger
### END INIT INFO
PATH=/sbin:/bin:/usr/sbin:/usr/bin
NAME=bootlogd
DESC="boot log daemon"
DAEMON=/sbin/bootlogd
PID_FILE=/var/run/bootlogd.pid
LOG_FILE=/var/log/boot.log
LOG_GROUP=adm

if [ ! -x "$DAEMON" ] ; then
    exit 0
fi

# Custom options are specified in '/etc/default/bootlogd'.
if [ -r /etc/default/bootlogd ] ; then
    . /etc/default/bootlogd
fi

# Having a 'BOOTLOGD_ENABLE' variable goes against Debian style for init.d
# scripts, however, it is included because fancy log output must be disabled
# for bootlogd to create readable logs. The 'log_use_fancy_output' function in
# '/etc/lsb-base-logging.sh' must also reference this variable.
case "${BOOTLOGD_ENABLE:-n}" in
[Nn]*)
    exit 0
    ;;
esac

. /lib/lsb/init-functions

# The '-r' option must be included because the '/var/log' directory may not be
# writable at the time of execution, precluding us from backing up existing logs
# within the context of this init.d script. bootlogd takes care of this for us
# by storing the new log in a buffer until '/var/log' becomes writable.
# Including the '-r' option instructs bootlogd to backup an existing log rather
# than overwriting it, which is the default behavior.
OPTIONS=" -r -l ${LOG_FILE} -p ${PID_FILE}"

case "$1" in
start)
    # Launch the bootlogd executable. It should be noted that if bootlogd
    # is required to fork itself into the background, the parent process
    # will always return a status of '1'. This will also cause
    # 'start-stop-daemon' to erroneously report an error. For simplicity, we
    # forego a 'log_end_msg' call and ignore the return status.
    log_daemon_msg "Starting ${DESC}" $NAME
    start-stop-daemon --start --quiet --pidfile $PID_FILE --name $NAME --startas $DAEMON --group $LOG_GROUP -- $OPTIONS
    ;;
stop)
    log_action_begin_msg "Stopping ${DESC}" $NAME
    start-stop-daemon --stop --quiet --oknodo --pidfile $PID_FILE --name $NAME
    log_action_end_msg $?

    # This wonderful, and somewhat daunting mess, is another result of the
    # '/var/log' directory not being writable when bootlogd is started. As a
    # result, we cannot backup existing logs during the 'start' case.
    # Instead, we use bootlogd's '-r' option (see above) and call 'savelog'
    # here in the 'stop' case. All the move commands are purely to ensure
    # naming continuity.
    if [ -f "${LOG_FILE}~" ] && [ -f $LOG_FILE ] ; then
        [ "x$VERBOSE" != "xno" ] && log_action_begin_msg "Backing up existing boot log" $LOG_FILE
        mv $LOG_FILE "${LOG_FILE}.bak" && \
        mv "${LOG_FILE}~" $LOG_FILE && \
        savelog -q -p -c 5 $LOG_FILE && \
        mv "${LOG_FILE}.bak" $LOG_FILE
        STATUS=$?
        [ "x$VERBOSE" != "xno" ] && log_action_end_msg $STATUS
    fi
    ;;
restart|force-reload)
    /etc/init.d/bootlogd stop
    /etc/init.d/bootlogd start
    ;;
*)
    echo "Usage: $SCRIPTNAME {start|stop|restart|force-reload}" >&2
    exit 3
    ;;
esac

:


```**/etc/init.d/stop-bootlogd:**
```
#! /bin/sh
### BEGIN INIT INFO
# Provides:          stop-bootlogd
# Required-Start:    $remote_fs
# Required-Stop:
# Default-Start:     1 2 3 4 5
# Default-Stop:
# Short-Description: Stop bootlogd
# Description:       See the bootlogd script
### END INIT INFO

NAME=stop-bootlogd
DAEMON=/sbin/bootlogd

[ -x "$DAEMON" ] || exit 0

case "$1" in
  start)
    /etc/init.d/bootlogd stop
    ;;
  stop|restart|force-reload)
    # No-op
    ;;
  *)
    echo "Usage: $NAME {start|stop|restart|force-reload}" >&2
    exit 3
    ;;
esac

:


```Both of these files need to be in the '/etc/init.d/' directory. Both of these files may already exist and are probably perfectly suitable. '/etc/init.d/stop-bootlogd' above is actually just the script that was left behind on my laptop by whatever last installed it. As I stated above,  I set out to write a "bigger, faster, better" version of '/etc/init.d/bootlogd' with great hubris, but ended up with something very similar to the original. 

Also note that these scripts do need to executable, they are not just sourced. So if you are creating them for the first time make sure to: 

```
sudo chmod +x {/etc/init.d/bootlogd,/etc/init.d/stop-bootlogd}
```[COLOR=Red]
WARNING: I did forget something first time around, linking instructions. DOH![/COLOR]

**Step 3: Linkage**
Now that the init scripts are resting comfortably in their new home, its time to knock some of their walls down and build superhighways. I don't know what kind of metaphor for rc linking that is but there you go. 

There are three primary ways to make the necessary links in the '/etc/rc*.d/' directories; some are considered to be more administratively "correct" than others.

[INDENT]**1. sysv-rc-conf:** The best way to configure the 'sysvinit' rc directories. Unfortunately, it is also part of the aforementioned 'sysvinit' package that conflicts with 'upstart', so I'm going to skip the usage example.

**2. update-rc.d:** This Debian "package maintainer" script can get the job done just as well but isn't really recommended for serious system administration use (Man page's words). ```
(as root)
update-rc.d bootlogd start 03 S
update-rc.d stop-bootlogd start 99 2
```

**3. ln -s:** The simplest, and most straight forward way. ```
(as root)
ln -s /etc/init.d/bootlogd /etc/rcS.d/S03bootlogd
ln -s /etc/init.d/stop-bootlogd /etc/rc2.d/S99stop-bootlogd
```[/INDENT] 

**Step 4: Fixage**
Nothing I have written heretofore is all that exciting, nor is something that you wouldn't find in any other guide to compiling and installing a package manually. This last, very simple step is the only really interesting part of this entire post. All it does, is let the rest of init scripts know when we are using 'bootlogd' so they can turn off their fancy terminal control sequences. 

The following needs to be added at the beginning of the file '/etc/lsb-base-logging.sh':
```
log_use_fancy_output () {
    TPUT=/usr/bin/tput
    EXPR=/usr/bin/expr

    # Check for bootlogd daemon. If enabled, fancy terminal output is
    # disabled because bootlogd can only interpret the most basic terminal
    # control sequences (such as newline) and dumps the rest directly to the
    # log. This creates a very ugly, and unreadable log.
    if [ -r /etc/default/bootlogd ] ; then
        . /etc/default/bootlogd
    fi

    case "${BOOTLOGD_ENABLE:-n}" in
      [Yy]*)
        return 1
        ;;
    esac
    
    if [ "x$TERM" != "xdumb" ] && [ -x $TPUT ] && [ -x $EXPR ] && $TPUT hpa 60 >/dev/null 2>&1 && $TPUT setaf 1 >/dev/null 2>&1; then
        [ -z $FANCYTTY ] && FANCYTTY=1 || true
    else
        FANCYTTY=0
    fi
    case "$FANCYTTY" in
    1|Y|yes|true)   true;;
    *)              false;;
    esac
}
```This simple shell function overrides an existing function declaration in '/lib/lsb/init-functions' and is identical except that it checks for "BOOTLOGD_ENABLED=y" in '/etc/default/bootlogd'. Which brings me to the final step.

**Final Step: Create '/etc/default/bootlogd'**
If it does not already exist, create the file '/etc/default/bootlogd' and add the line, ```
BOOTLOGD_ENABLED=y
``` although any string beginning with 'y' will do. If you decided to use my init script, other options you can put in '/etc/default/bootlogd' include "LOG_FILE" to specify the name of your boot log. (My init script defaults to '/var/log/boot.log' instead of '/var/log/boot'.)

**Conclusion:**
Well, that's all I can think of right now. There are probably a host of errors in this that I need to fix. Questions, comments and concerns are welcome. I feel like I'm forgetting something...
**[COLOR="Blue"]GORAMIT! I did forget something. Linkage instructions are now included as Step 3.[/COLOR]**

---

### Post by aijeitpipol on 2010-12-27
Wow man, good efford, I hope is usefull to somebody :)

---

