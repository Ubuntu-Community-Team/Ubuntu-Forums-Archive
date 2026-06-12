---
title: "PATH is not seting up in expected"
date: 2013-08-09
forum: General Help
---

### Post by benjaH1 on 2013-08-09
Hi everyone,

I don't know if I had done anything wrong, but now, the PATH is now mess up. Important path like '/sbin' is missing.
```
$ echo $PATH
/home/xxxxxx/bin:/usr/local/bin:/usr/bin:/bin:/usr/games

$ ifconfig
Command 'ifconfig' is available in '/sbin/ifconfig'
The command could not be located because '/sbin' is not included in the PATH environment variable.
This is most likely caused by the lack of administrative privileges associated with your user account.
ifconfig: command not found

$ cat ~/.profile 
# ~/.profile: executed by the command interpreter for login shells.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/profile; for setting the umask
# for ssh logins, install and configure the libpam-umask package.
#umask 022

# if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f "$HOME/.bashrc" ]; then
    . "$HOME/.bashrc"
    fi
fi

# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi

$ cat /etc/environment 
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
$ cat /etc/init.d/rc.local 
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

ABC="abc"
export ABC

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
        echo "Error: argument '(' not supported" >&2
        exit 3
    ;;
    stop)
    ;;
    *)
        echo "Usage: $0 start|stop" >&2
        exit 3
    ;;
esac
```

 I know that setting the right one could fix this, but I need to know why this happens and fix it. Please let me know if I need to post more information. Not sure if this is relative, the /etc/init.d/rc.local doesn't seems to work at boot as well.

Thanks

---

### Post by steeldriver on 2013-08-09
In Ubuntu, the /sbin and /usr/sbin paths should be included from /etc/environment

```
$ cat /etc/environment
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"

```

Other distributions don't necessarily include them by default (my LMDE box doesn't for example)

---

### Post by benjaH1 on 2013-08-09
Hi steeldriver,

I am using Ubuntu 12.04. /sbin and /usr/sbin are in the /etc/environment. However, they are disappeared in the final PATH. I am wondering if the PATH is reset somewhere, but I don't know how to track.

---

### Post by steeldriver on 2013-08-09
Perhaps in your ~/.bashrc file?

The PATH defined in /etc/init.d/rc.local only applies within that script - it doesn't get exported. Or do you have other reasons to believe the script isn't working?

---

### Post by benjaH1 on 2013-08-09
> **steeldriver said:**
> Perhaps in your ~/.bashrc file?

The PATH defined in /etc/init.d/rc.local only applies within that script - it doesn't get exported. Or do you have other reasons to believe the script isn't working?

Checked ~/.bashrc, ~/.bash_profile. There is no PATH reference.
I did try export the PATH in rc.local before, or even export ABC="abc". No luck.
Furthermore, I use to have a mount script in the rc.local. It was executing perfectly, but doesn't work anymore. Can't remember what exactly I had done. Perhaps Installing the video driver.

---

