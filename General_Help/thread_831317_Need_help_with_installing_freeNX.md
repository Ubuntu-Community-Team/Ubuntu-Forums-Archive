---
title: "Need help with installing freeNX"
date: 2008-06-16
forum: General Help
---

### Post by jon64 on 2008-06-16
__As the title says i need help installing freenx on my kubuntu 8.04 machine. Ive tried a couple of guides throughout the forum + google and at this point im stuck with a Session startup failed. 

This is the main guide i used during the installation:
[http://www.drtek.ca/freenx-server-ubuntu-hardy](http://www.drtek.ca/freenx-server-ubuntu-hardy)

Here is the log that i get when i try to use NX client on my windows xp machine:

NX> 203 NXSSH running with pid: 2668
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 71.197.216.193 on port: 22
 NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 2.1.0-72 OS (GPL, using backend: not detected)
NX> 105 hello NXCLIENT - Version 2.1.0
NX> 134 Accepted protocol: 2.1.0
 NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: jon64
NX> 102 Password: 
NX> 103 Welcome to: jon64-linux user: jon64
NX> 105 listsession --user="jon64" --status="suspended,running" --geometry="1280x1024x32+render" --type="unix-kde"
 NX> 127 Sessions list of user 'jon64' for reconnect:
 
Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------
 

NX> 148 Server capacity: not reached for user: jon64
NX> 105 startsession  --link="lan" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="linux" --type="unix-kde" --geometry="1280x994" --client="winnt" --keyboard="pc102/en_US" --screeninfo="1280x994x32+render" 
 
NX> 1000 NXNODE - Version 2.1.0-72 OS (GPL, using backend: not detected)
NX> 700 Session id: jon64-linux-1001-003EC6DEF586150EAC5FF9F589AE873E
NX> 705 Session display: 1001
NX> 703 Session type: unix-kde
 NX> 701 Proxy cookie: e1c738877c459fa7a317eed4a2833207
NX> 702 Proxy IP: 127.0.0.1
NX> 706 Agent cookie: e1c738877c459fa7a317eed4a2833207
NX> 704 Session cache: unix-kde
 NX> 707 SSL tunneling: 1
NX> 105 /usr/lib/nx/nxserver: line 1370: 28488 Terminated              sleep $AGENT_STARTUP_TIMEOUT
NX> 596 Session startup failed.
NX> 1004 Error: NX Agent exited with exit status 1. To troubleshoot set SESSION_LOG_CLEAN=0 in node.conf and investigate "/home/jon64/.nx/F-C-jon64-linux-1001-003EC6DEF586150EAC5FF9F589AE873E/session". You might also want to try: ssh -X myserver; /usr/lib/nx/nxnode --agent to test the basic functionality. Session log follows:
 Can't open /var/lib/nxserver/db/running/sessionId{003EC6DEF586150EAC5FF9F589AE873E}: No such file or directory.
NX> 1006 Session status: closed
mv: cannot stat `/var/lib/nxserver/db/running/sessionId{003EC6DEF586150EAC5FF9F589AE873E}': No such file or directory
 NX> 1001 Bye.
NX> 280 Exiting on signal: 15

And heres my **node.conf**:

# node.conf
#
# This file is provided by FreeNX. It should be placed either into
# /etc/nxserver/node.conf (FreeNX style) or /usr/NX/etc/node.conf
# (NoMachine NX style).
#
# It is mostly compatible with NoMachine node.conf. The most important 
# difference is that no spaces are allowed when assigning values (eg 
# "A=value" is allowed, "A = value" is NOT).
#
# This file is sourced by bash, so you can do some fancy stuff here if you
# want to, but be aware that it is sourced 3 times per connection. If you 
# want autostart stuff, set NODE_AUTOSTART instead!
# 
#
# You surely are aware that FreeNX is based on the fantastic results that
# the hard work by NoMachine.com has achieved. NoMachine.com released the
# core NX libraries under the GPL. The installation of these libs are the
# precondition for all FreeNX scripts to work. If you are installing this
# software with the help of one of the package management tools of your
# Linux distribution, you can assume that this dependency is taken care of
# by the tool.
#
# You have questions about the inner workings of the NX technology?
#
# Then you are recommended to first check out the rich and very detailed
# NoMachine documentation and their online Knowledge Base at 
#
#           [http://www.nomachine.com/kb/](http://www.nomachine.com/kb/)
#
# Other sources of information are the NoMachine mailing lists 
# (nxusers@nomachine.com and [email]nxdevelopers@nomachine.com[/email]):
#
#           [http://www.nomachine.com/mailinglists.php](http://www.nomachine.com/mailinglists.php)
#
# The FreeNX (freenx-knx@kde.org) list is here:
#
#           [https://mail.kde.org/mailman/listinfo/freenx-knx](https://mail.kde.org/mailman/listinfo/freenx-knx)
#
# SVN: $Id: node.conf.sample 533 2008-03-14 21:47:47Z fabianx $

#########################################################################
# General FreeNX directives
#########################################################################

# The host name which is used by NX server. It's should be used if it's
# different than the default hostname (as returned by `hostname`)
#SERVER_NAME="$(hostname)"

# The port number where local 'sshd' is listening.
#SSHD_PORT=22


#########################################################################
# Authentication / Security directives
#########################################################################

# Authentication directives

# This adds the usermode to the possible authentication methods
# Usermode means that a user can start the nxserver as his shell
# and connect directly to the right server via a custom client.
#ENABLE_USERMODE_AUTHENTICATION="0"

# This adds the passdb to the possible authentication methods
#ENABLE_PASSDB_AUTHENTICATION="1"

# This adds SSH to the possible authentication methods. For it to work sshd
# must be set up at localhost accepting password authentication.
#ENABLE_SSH_AUTHENTICATION="1"

# This adds SU to the possible authentication methods. For it to work the 
# "nx" user must be in the wheel (RedHat, Fedora) or the users group (SUSE)
# and the user logging in must have a valid shell that accepts the -c
# parameter.
#ENABLE_SU_AUTHENTICATION="0"

# Require all users to be in the passdb, regardless of authentication method
#ENABLE_USER_DB="0"


# If enabled forces the user to use encryption. This will bail out
# if the user does not have encryption enabled.
#ENABLE_FORCE_ENCRYPTION="0"

# Refuse the NX client connection if SSHD does not export the
# SSH_CONNECTION and SSH_CLIENT variables in the environment
# passed to the NX server.
# 1: Will check the remote IP and will not accept the
#    connection if it can't be determined.
# 0: Will accept the connection even if the remote IP
#    is not provided.
#SSHD_CHECK_IP="0"

# If ENABLE_SLAVE_MODE="1" the user will be just logged in _once_ and the 
# communication is done via nxnode slave mode.
#
# This is useful for one time passwords or to have less traffic in utmp 
# and wtmp.
#
# Also session startup times are much faster in slave mode. This is true especially 
# if many printers or shares have to be added.
#
# For this to work the binary nxserver-helper has to be installed in 
# PATH_BIN.
#
#ENABLE_SLAVE_MODE="0"

#########################################################################
# Restriction directives
#########################################################################

# The base display number from which sessions are started.
#DISPLAY_BASE=1000

# The maximum number of contemporary sessions that can be run on FreeNX
#SESSION_LIMIT=200

# The maximum number of contemporary sessions that a single user can run
# on FreeNX. Defaults to the value of SESSION_LIMIT.
#SESSION_USER_LIMIT=200

# The number of displays reserved for sessions, it has to be greater or equal
# to the maximum number of contemporary sessions that a server can run.
#DISPLAY_LIMIT=200


# User for which sessions should be persistent. Either the keyword "all" or a
# comma-separated list of usernames or groups in the @groupname syntax.
#ENABLE_PERSISTENT_SESSION="all"

# Users and groups for whom persistent sessions should be disabled.
# Especially useful if ENABLE_PERSISTENT_SESSION="all"
#DISABLE_PERSISTENT_SESSION=""

# This enables the mirroring of running sessions via VNC feature.
# 
# Session is marked as resumable and type is vnc-mirrored.
# 
#ENABLE_MIRROR_VIA_VNC=1

# This enables the sharing of :0 via VNC feature.
# 
# Session is marked as resumable and type is vnc-local.
# 
# Note: You need to have the rights to access the display
#       else it does not work.
#
#ENABLE_DESKTOP_SHARING=1

#
# Enable or disable clipboard:
#
# client:  The content copied on the client can be pasted inside the
#            NX session.
#
# server: The content copied inside the NX session can be pasted
#             on the client.
#
# both:    The copy&paste operations are allowed both between the
#             client and the NX session and vice-versa.
#
# none:   The copy&paste operations between the client and the NX
#            session are never allowed.
#
#ENABLE_CLIPBOARD="both"


#
# Enable or disable the pulldown dialog, which provides a graphical
# way to suspend or terminate the rootless session:
#
# 1: Enabled. The pulldown menu is shown when the mouse pointer
#     moves near the middle of the top boundary of a window and
#     allows the user to suspend or terminate the session by means
#     of an icon-click.
#
# 0: Disabled. The ctrl+alt+T key combination has to be issued
#     to get the dialog for suspending or terminating the session.
#
#ENABLE_PULLDOWN_MENU="1"


# The option USE_PROCESSOR_TASKSET is for setting the CPU affinity of all
# nx related processes.
#
# Note: To have for example startkde run on even another core, just specify:
#
# COMMAND_STARTKDE="taskset -c 2 -- startkde"
#
# FreeNX runs this option like: $COMMAND_TASKSET -cp "$USE_PROCESSOR_TASKSET" $$
# 
# So with $USE_PROCESSOR_TASKSET set to 3,4 it would balance the tasks to cores
# 3 and 4.
#
# If this option is empty, no balance to cores is done.
#
#USE_PROCESSOR_TASKSET=""

# If you set ENABLE_ADVANCED_SESSION_CONTROL="1" you can start a new application in an already
# running rootless session by using "add <rest of name>" as session name.
#
# Note: The client will return a message on that.
#
#ENABLE_ADVANCED_SESSION_CONTROL="0"

# If you set ENABLE_SHOW_RUNNING_SESSIONS="0" then nxserver will only show
# suspended sessions and you will not be able to resume or terminate a running 
# session.
#
#ENABLE_SHOW_RUNNING_SESSIONS="1"

#########################################################################
# Logging directives
#########################################################################

# This directives controls the verbosity of the server-wide log.
# 0: No Logging
# 1: Errors
# 2: Warnings
# 3: Important information
# 4: Server - Client communication
# 5: Information
# 6: Debugging information
# 7: stderror of some applications
#NX_LOG_LEVEL=0

# By setting this to 0 the nxserver might be a bit faster, but passwords can be found in the log files.
#NX_LOG_SECURE=1

# Before turning logging on, please make sure that NX_LOGFILE is
# writeable for the "nx" user
#NX_LOGFILE=/var/log/nxserver.log

# This directive controls if the temporary session directory
# ($HOME/.nx/C-<hostname>-<display>-<session_id>) should be kept after a
# session has ended. A successfully terminated session will be saved as
# T-C-<hostname>-<display>-<session_id> while a failed session will be saved
# as F-C-<hostname>-<display>-<session_id>.
# The default is to cleanup the directories.
#SESSION_LOG_CLEAN=1

# Amount of seconds nxserver is to keep session history. The default of 2592000
# is equivalent to 30 days. If this is 0 no session history will be kept
# and a negative value denotes infinity.
#SESSION_HISTORY=2592000


#########################################################################
# Forwarding directives
#########################################################################

# FreeNX with ENABLE_SERVER_FORWARD="1" will automatically forward all
# connections to the host specified in SERVER_FORWARD_HOST with the
# secret key SERVER_FORWARD_KEY.
#
# This allows to have a "chain" of NX Servers. Note that you will need to
# use "SSL encryption" for all connections.

#ENABLE_SERVER_FORWARD="0"
#SERVER_FORWARD_HOST=""
#SERVER_FORWARD_PORT=22
#SERVER_FORWARD_KEY="/usr/NX/share/client.id_dsa.key"


# FreeNX with ENABLE_NOMACHINE_FORWARD_PORT="1" will automatically forward all
# connections to the commercial NoMachine nxserver installed on the same
# machine, which go in by port NOMACHINE_FORWARD_PORT. This feature is introduced
# to enable the usage of FreeNX and NoMachine NX side by side on the same machine
# without conflicts.
#
# Note: You need to let SSHD listen to several ports to make use of this
#       directive.

#ENABLE_NOMACHINE_FORWARD_PORT="0"
#NOMACHINE_FORWARD_PORT="22"

#NOMACHINE_SERVER="/usr/NX/bin/nxserver"
#NOMACHINE_NX_HOME_DIR="/usr/NX/home/nx"


# LOAD BALANCING
# ==============
#
# To do load balancing setup some hosts in LOAD_BALANCE_SERVERS and
# make:
#
#   - either sure that all incoming connections are sent to the master
#     server by using forwarding directives on the "slave" servers.
#
#   - or share the session database space via NFS between the servers.
#     (not recommended at the moment as race conditions for DISPLAYs can 
#      occur)
#

#LOAD_BALANCE_SERVERS=""

# The following load_balance_algorithms are available at the moment:
#
# "load", "round-robin", "random"
#
# For "load" you need a script called nxcheckload in PATH_BIN.
# 
# A sample script, which you can change to your needs it shipped with
# FreeNX under the name nxcheckload.sample.

#LOAD_BALANCE_ALGORITHM="random"

# By setting ENABLE_LOADBALANCE="1" you can let users choose their
# preferred host, while being forwarded to another server. Of course
# this is just a preference. The loadbalancing algorithm can completely
# choose to ignore the users choice.

#ENABLE_LOAD_BALANCE_PREFERENCE="0"

#########################################################################
# Services directives
#########################################################################

# FreeNX with ENABLE_ESD_PRELOAD="1" will automatically try to setup
# the sound with the help of the esd media helper.
#
# Currently ESD will be used just by the Windows NX Client.
#
# Be sure that $ESD_BIN_PRELOAD is in your path, does exist and work
# before enabling this directive.

#ENABLE_ESD_PRELOAD="0"
#ESD_BIN_PRELOAD="esddsp"

# FreeNX with ENABLE_ARTSD_PRELOAD="1" will automatically try to setup
# the sound with the help of the artsd media helper.
#
# Currently ARTSD will be used just by the Linux NX Client.
#
# Be sure that $ARTSD_BIN_PRELOAD is in your path, does exist and work
# before enabling this directive.

#ENABLE_ARTSD_PRELOAD="0"
#ARTSD_BIN_PRELOAD="artsdsp"

# FreeNX with ENABLE_KDE_CUPS="1" will automatically write 
# $KDE_PRINTRC and put the current used socket into it.
#
# If you additionally enable ENABLE_KDE_CUPS_DYNAMIC it will set the 
# Host entry to the script nxcups-gethost, which dynamically tries all 
# possible entries to find the current printing host.
#
# The order is: CUPS_SERVER (env var), ~/.cups/client.conf, $KDE_PRINTRC,
#               $CUPS_DEFAULT_SOCK, localhost
#
# So this option is most useful with ENABLE_CUPS_SERVER_EXPORT="1".
# 
# $KDE_PRINTRC is automatically calculated if its not set.

#ENABLE_KDE_CUPS="0"
#ENABLE_KDE_CUPS_DYNAMIC="0"
#KDE_PRINTRC="$KDEHOME/share/config/kdeprintrc"

# FreeNX with ENABLE_CUPS_SERVER_EXPORT="1" will automatically
# export the environment variable CUPS_SERVER.

#ENABLE_CUPS_SERVER_EXPORT="1"

# FreeNX with ENABLE_CUPS_SEAMLESS will automatically try to download the 
# necessary ppds from the client.
# 
# As the forwarding is just active as soon as nxagent is started,
# we need a small delay of $CUPS_SEAMLESS_DELAY.
#
# Note: You need to use a patched cupsd on client side.

#ENABLE_CUPS_SEAMLESS="0"
#CUPS_SEAMLESS_DELAY="10"

# FreeNX with ENABLE_FOOMATIC will integrate the foomatic db to the list
# of available ppd drivers via the $COMMAND_FOOMATIC command.

#ENABLE_FOOMATIC="1"
#COMMAND_FOOMATIC="/usr/lib/cups/driver/foomatic-ppdfile"

# CUPS_BACKEND and CUPS_ETC are the corresponding paths of your CUPS 
# installation.

#CUPS_BACKEND="/usr/lib/cups/backend"
#CUPS_IPP_BACKEND="$CUPS_BACKEND/nxipp"
#CUPS_DEFAULT_SOCK="/var/run/cups/cups.sock"
#CUPS_ETC="/etc/cups"

# SAMBA_MOUNT_SHARE_PROTOCOL is a key to configure the supported 
# protocols for mounting shares.
#
# This key can be set to the following values:
#
# both, either SMB and CIFS protocol are supported, this is the default value.
# smbfs, only SMB protocol is supported.
# cifs, only CIFS protocol is supported.
# none, no network file-sharing protocol is supported.

#SAMBA_MOUNT_SHARE_PROTOCOL="both"

# FreeNX with ENABLE_SAMBA_PRELOAD="1" will automatically setup
# port 445 and 139 and forward them to the used samba port.
#
# This enables samba browsing to the local subnet in for example 
# konqueror.
#
#ENABLE_SAMBA_PRELOAD="0"

#########################################################################
# Path directives
#########################################################################

# USER_FAKE_HOME is the base directory for the .nx directory. Use this
# parameter instead of the users home directory if $HOME is on a NFS share.
# Note that this directory must be unique for every user! To accomplish this
# it is recommended to include $USER in the path.
#USER_FAKE_HOME=$HOME

# Add the nx libraries to LD_LIBRARY_PATH before starting nx agents.
# WARNING: This will NOT (and should not) affect applications. ONLY Disable
# this if the nx libraries are in a standard system path (such as /usr/lib)!
#SET_LD_LIBRARY_PATH="1"


# The command binary for the default window manager. If set it is run when a
# 'unix-custom' session is requested by the NX Client and an application
# to run is specified. It defaults to empty (ie no WM is run).
# If KILL_DEFAULT_X_WM is set the WM is terminated after the started 
# application finishes. Else FreeNX will wait for the WM to complete.
#DEFAULT_X_WM=""
#KILL_DEFAULT_X_WM="1"

# When a 'unix-default' session is requested by the client the user's X startup
# script will be run if pressent and executable, otherwise the default X
# session will be run.
# Depending on distribution USER_X_STARTUP_SCRIPT might be .Xclients, .xinitrc
# and .Xsession
# Depending on distribution DEFAULT_X_SESSION might be /etc/X11/xdm/Xsession,
# /etc/X11/Sessions/Xsession or /etc/X11/xinit/xinitrc
#USER_X_STARTUP_SCRIPT=.Xclients
#DEFAULT_X_SESSION=/etc/X11/xdm/Xsession

# The key that contains the name of the script that starts a KDE session.
# It's run when a 'unix-kde' session is requested by the client.
#COMMAND_START_KDE=startkde

# The key that contains the name of the script that starts a gnome session.
# It's run when a 'unix-gnome' session is requested by the client.
#COMMAND_START_GNOME=gnome-session

# The key that contains the name of the script that starts a CDE session.
# It's run when a 'unix-cde' session is requested by the client.
#COMMAND_START_CDE=cdwm

# The key that contains the name of the complete path of command name
# 'xterm'. It is run when a unix "xterm" session is requested by the
# client.
#COMMAND_XTERM=xterm

# The key that contains the name of the complete path of command name
# 'xauth'.
#COMMAND_XAUTH=/usr/X11R6/bin/xauth

# The key that contains the name of the complete path of command name
# 'smbmount'.
#COMMAND_SMBMOUNT=smbmount

# The key that contains the name of the complete path of command name
# 'smbumount'.
#COMMAND_SMBUMOUNT=smbumount

# The key that contains the name of the complete path of command name
# 'mount.cifs'.
#COMMAND_SMBMOUNT_CIFS=/sbin/mount.cifs

# The key that contains the name of the complete path of command name
# 'umount.cifs'.
#COMMAND_SMBUMOUNT_CIFS=/sbin/umount.cifs

# The key that contains the name of the complete path of the 'netcat' command.
#COMMAND_NETCAT=netcat

# The key that contains the name of the complete path of the 'ssh' and
# 'ssh-keygen' command.
#COMMAND_SSH=ssh
#COMMAND_SSH_KEYGEN=ssh-keygen

# The key that contains the name of the complete path of the 'cupsd' command.
#COMMAND_CUPSD=/usr/sbin/cupsd

# The tool to generate md5sums with
#COMMAND_MD5SUM="openssl md5"

# The key that contains the name of the complete path of the 'rdesktop' command.
#COMMAND_RDESKTOP=rdesktop

# The key that contains the name of the complete path of the 'vncviewer' command.
#COMMAND_VNCVIEWER=vncviewer

# The key that contains the name of the complete path of the 'vncpasswd' command.
# By default the builtin nxpasswd is used.
#COMMAND_VNCPASSWD="$PATH_BIN/nxpasswd"

# The key that contains the name of the complete path of the 'x11vnc' command.
#COMMAND_X11VNC=x11vnc

# The key that contains the name of the complete path of the 'taskset' command.
#COMMAND_TASKSET=taskset

#########################################################################
# Misc directives
#########################################################################

# When you installed an old 1.5.0 NX Backend, set this to 1.
#ENABLE_1_5_0_BACKEND="0"

# When set to 1 this will automatically resume started sessions
#ENABLE_AUTORECONNECT="0"

# When set to 1 this will automatically resume started sessions
# but only if an older client version is used
#ENABLE_AUTORECONNECT_BEFORE_140="1"

# When set to 1 exports NXUSERIP / NXSESSIONID in nxnode
#EXPORT_USERIP="0"
#EXPORT_SESSIONID="1"

# This can be set to any executable, which is started after session startup
# like: $NODE_AUTOSTART {start|restore}
#NODE_AUTOSTART=""

# When set to 1 will start nxagent in rootless mode.
#ENABLE_ROOTLESS_MODE="1"

# If enabled writes entries via the COMMAND_SESSREG program
# into utmp/wtmp/lastlog database.
# Note: You have to make sure that you add the nx user to the
#       utmp or tty group or how its called on your system
#       before this directive works.
#ENABLE_USESSION="1"
#COMMAND_SESSREG="sessreg"

# Extra options sent to the different nx agents. See !M documentation
# for examples of useful parameters.
#AGENT_EXTRA_OPTIONS_RFB=""
#AGENT_EXTRA_OPTIONS_RDP=""
#AGENT_EXTRA_OPTIONS_X=""

# The number of seconds we wait for the nxagent to start before
# deciding startup has failed
#AGENT_STARTUP_TIMEOUT="60"

# The font server the agent will use. If set to "" no font server is used.
# For this to do any good, the client has to have the same font server set
# in /etc/X11/XF86Config
#AGENT_FONT_SERVER=""

# Disable or enable use of 'tcp nodelay' on proxy. Old versions of Linux
# kernels have problems using this option on sockets that will cause a loss
# of TCP connections. This option is not set by default to allow clients to
# specify whether to enable or disable TCP nodelay. Setting this option to
# the value of "0" NX proxy avoids using 'tcp nodelay' but it will cause a
# loss of interaction in sessions.
#PROXY_TCP_NODELAY=""

# Extra options to nxproxy. See !M documentation for useful parameters.
#PROXY_EXTRA_OPTIONS=""

# In case you want to use an external 'rdesktop' command
# set this to "1".
# 
# If nxdesktop cannot be found this is set automatically to "1".
#ENABLE_EXTERNAL_NXDESKTOP="0"

# This configuration variable determines if 'rdesktop' command should be run with -k keyboard option
# or if the keyboard should be autodetected.
#
#ENABLE_EXTERNAL_NXDESKTOP_KEYBOARD="1"

# In case you want to use an external 'nxviewer' command
# set this to "1".
# 
# If nxviewer cannot be found this is set automatically to "1".
#ENABLE_EXTERNAL_NXVIEWER="0"

---

### Post by jon64 on 2008-06-17
can someone please help me :(

---

### Post by CaptSaltyJack on 2008-08-30
Forget that guide.  Uninstall all freeNX stuff you installed, remove all its config files, wipe it clean, we're starting over.

Go here:
[http://www.nomachine.com/download-package.php?Prod_Id=6](http://www.nomachine.com/download-package.php?Prod_Id=6)

Or if you're on 64-bit:
[http://www.nomachine.com/download-package.php?Prod_Id=3](http://www.nomachine.com/download-package.php?Prod_Id=3)

Download all three deb packages: client, node, and server.

Follow the instructions on that page.  Just run these three commands:

sudo dpkg -i nxclient_3.2.0-14_i386.deb
sudo dpkg -i nxnode_3.2.0-13_i386.deb
sudo dpkg -i nxserver_3.2.0-16_i386.deb
(or x86_64.deb if you're 64-bit)

And you're done.  It's that easy.

---

### Post by linux5uper on 2008-09-18
> **CaptSaltyJack said:**
> Forget that guide.  Uninstall all freeNX stuff you installed, remove all its config files, wipe it clean, we're starting over.

Go here:
[http://www.nomachine.com/download-package.php?Prod_Id=6](http://www.nomachine.com/download-package.php?Prod_Id=6)

Or if you're on 64-bit:
[http://www.nomachine.com/download-package.php?Prod_Id=3](http://www.nomachine.com/download-package.php?Prod_Id=3)

Download all three deb packages: client, node, and server.

Follow the instructions on that page.  Just run these three commands:

sudo dpkg -i nxclient_3.2.0-14_i386.deb
sudo dpkg -i nxnode_3.2.0-13_i386.deb
sudo dpkg -i nxserver_3.2.0-16_i386.deb
(or x86_64.deb if you're 64-bit)

And you're done.  It's that easy.

Thanks for this update. The problem is that I still cannot figure out what is wrong with my setup. After performing these steps, I added my local user to the nxserver, I started the server and I started the openbsd ssh server too. I'm confused about how nxserver interacts with the ssh server, and what exactly needs to be done with the authentication keys. There are a few contradictory posts on these forums.:confused:

---

### Post by CaptSaltyJack on 2008-09-18
I'm not clear on how NX works either, but I do know I didn't have to add any users to the nxserver.  Nothing.  Just the dpkg installations, and it was done.  Anyone who can ssh into your box can use NX to connect, as far as I'm aware.  NX also follows the rules in /etc/ssh/sshd_config (e.g. AllowUsers).  Make sure your AllowUsers line has "nx" on it.  e.g. if your username is steve, your /etc/ssh/sshd_config should contain this line:

```
AllowUsers steve nx
```

I would recommend uninstalling the NX stuff, in this order:

```

sudo dpkg -r nxserver
sudo dpkg -r nxnode
sudo dpkg -r nxclient

```

Then reinstalling per my post above.  After that, NX should be up and running and you should not have to add any users or do anything else.  Every time I've set up NX, it was ready to go as soon as I installed the packages.

Let me know how that turns out.

---

