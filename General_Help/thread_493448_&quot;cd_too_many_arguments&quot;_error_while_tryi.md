---
title: "&quot;cd: too many arguments&quot; error while trying to run Proe Wildfire!! Please Help!!"
date: 2007-07-05
forum: General Help
---

### Post by cyanide on 2007-07-05
Hi everyone,
                      I have installed Proe Wildfire 2 on Ubuntu Feisty Fawn along with Beryl Compositing Manager. The installation went without a hitch and the software was installed. When I try to run the proe1 or proe script, I get this error message,

> 
    cd: too many arguments

movie
This the content of my proe script:

> 
    #!/bin/csh -f

    set rundir="$cwd"
    set fullscrname="$0"

    set fullscrname="ls -l $fullscrname | awk '{print $NF}'"
    set scrname="$fullscrname:t"
    set fullscrpath=$fullscrname:h
    if ($fullscrpath $fullscrname) then
    set fullscrpath=$cwd
    else
    cd $fullscrpath
    set fullscrpath=$cwd
    endif
    cd $rundir
    set prodir="$fullscrpath:h"
    set mc="$prodir/install/unix/getpmt"
    setenv PRODIR $prodir

    if ( $mc "hpux_pa64" ) then
    if ( ! -d $prodir/hpux_pa64/obj ) then
    set mc="hpux11_pa32"
    endif
    endif
    if ( $mc "hpux11_pa32" ) then
    if ( ! -d $prodir/hpux11_pa32/obj ) then
    set mc="hp8k"
    endif
    endif
    if ( $mc "hp8k" ) then
    if ( ! -d $prodir/hp8k/obj ) then
    if ( -d $prodir/hp700 ) set mc="hp700"
    endif
    endif
    if ( $mc "sgi_elf4" ) then
    if ( ! -d $prodir/sgi_elf4/obj ) then
    set mc="sgi_mips4"
    endif
    endif
    if ( $mc "sgi_mips4" ) then
    if ( ! -d $prodir/sgi_mips4/obj ) then
    if ( -d $prodir/sgi_elf2 ) set mc="sgi_elf2"
    endif
    endif
    if ( $mc "sun4_solaris_64" )then
    if ( ! -d $prodir/sun4_solaris_64/obj ) then
    if ( -d $prodir/sun4_solaris ) set mc="sun4_solaris"
    endif
    endif

    set libset="$prodir/$mc/obj/ps_libset"
    if ( ! -x $libset ) unset libset

    setenv MC $mc
    setenv PRO_MACHINE_TYPE $mc

    setenv PRO_DIRECTORY $prodir

    setenv FORCE_PMT $MC
    $PRO_DIRECTORY/$MC/obj/proe.exe $*
    exit $status


This is the output of my "env" command,

> 
:~$ env
SSH_AGENT_PIDV92
SHELL=/bin/bash
DESKTOP_STARTUP_ID=
TERM=xterm
GTK_RC_FILES=/etc/gtk/gtkrc:/home/cyanide/.gtkrc-1.2-gnome2
WINDOWIDe011807
USER=cyanide
LS_COLORS=no
SESSION_MANAGER=local/cyanide-laptop:/tmp/.ICE-unix/5651
USERNAME=cyanide
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
DESKTOP_SESSION=xgl
GDM_XSERVER_LOCATION=local
PWD=/home/cyanide
LANG=en_US.UTF-8
GDMSESSION=xgl
HISTCONTROL=ignoreboth
SHLVL=1
HOME=/home/cyanide
GNOME_DESKTOP_SESSION_IDÞfault
LOGNAME=cyanide
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-
PhEZNDZB1z,guidî1f81210669f509dd8fd300468c1996
LESSOPEN=| /usr/bin/lesspipe %s
DISPLAY=:1.0
LESSCLOSE=/usr/bin/lesspipe %s %s
COLORTERM=gnome-terminal
XAUTHORITY=/home/cyanide/.Xauthority
_=/usr/bin/env


Can any one help me with this problem???

---

### Post by cyanide on 2007-07-06
Can anyone help me with this problem please?? 

I really need to run this program!!

Any help is appreciated!!

---

### Post by cyanide on 2007-07-14
Can any one please help me work this problem out??

Any help is appreciated.

---

### Post by jyba on 2007-07-14
If you're sure that script is where the problem lies you could try the -x flag to get more information on what's going on.

Put "x" at the end of the first line of the script like this: "**#!/bin/csh -fx**", and then run it. It will print out some information that may help to diagnose the problem that is causing cd to choke.

---

