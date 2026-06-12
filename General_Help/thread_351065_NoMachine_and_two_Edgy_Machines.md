---
title: "NoMachine and two Edgy Machines"
date: 2007-02-01
forum: General Help
---

### Post by tannedin on 2007-02-01
DLed lasted nxclient, nxserver, and nxnode off of nomachine.com
ran nxclient, nxnode, nxserver installs (in that order)
ran /usr/NX/scripts/setup nxnode & nxserver (in that order)

changed SSHD listen ports to reflect port change due to router and it matches /etc/ssh/ssd_config

I'm authenticating, but I'm getting a "server not set up properly error"
posting node.cfg, server.cfg, nxclient 'detail', and /var/log/messages with a grep search on the error
-----

node.cfg
```

#
# Set config file format version.
#
CONFIG_FILE_VERSION = "1.0"

#
# Set the log level of NX node. NX node logs to the syslog all the
# events that are <= to the level specified below, according to the
# following convention:
#
# KERN_ERR         3: Error condition.
# KERN_INFO        6: Informational.
# KERN_DEBUG       7: Debug messages.
#
# Note, anyway, that NX node uses level 6 in the syslog to log the 
# event. This is intended to override any setting on the local sys-
# log configuration that would prevent the event from being actually
# logged.
#
# The suggested values are:
#
# 6: This is the default value. Only the important events
#    are logged.
#
# 7: Set the log level to debug.
#
#SESSION_LOG_LEVEL = "6"

#
# Enable or disable the automatic clean-up of NX session directories
# at the time sessions are terminated:
#
# 1: Enabled. This is the default value.
#
# 0: Disabled. Directories are prefixed by 'T-' and left
#    for further reference.
#
#SESSION_LOG_CLEAN = "1"

#
# Enable or disable NX node to log the X client stderr.
#
# 1: Enabled. The standard error of the X clients is redirected to
#    the 'clients' file in the session directory. 
#
# 0: Disabled. The standard error of the X clients is redirected to
#    /dev/null.
#
#CLIENT_LOG = "1"

#
# Set the maximum size allowed for the log of the X clients. The node
# will terminate the session if this limit is exceeded. The default 
# value is 4194304 bytes (4MB).
#
#CLIENT_LOG_LIMIT = "4194304"

#
# Set the maximum size allowed for the session log. The node will
# terminate the session if this limit is exceeded. The default value
# is 4194304 bytes (4MB).
#
#SESSION_LOG_LIMIT = "4194304"

#
# Enable or disable SSL encryption of all traffic between server and
# node.
#
# 1: Enabled. Unencrypted connections between the server and
#    the node will be allowed.                       
#
# 0: Disabled. Forbid the use of unencrypted connections. The
#    node will force the server to tunnel the proxy connections
#    over the encrypted channel.
#
# Session negotiation always happens across an encrypted channel.
# Normally the user can specify if the subsequent communication
# must take place through a direct connection between the proxies
# or by tunneling it through SSH. You may uncomment the following
# line and set the value to 0 to increase the security of the node
# host or if NX node is behind a firewall preventing the access to
# the set of ports used by the NX node.
#
# Unencrypted sessions require that the firewall lets the proxies
# communicate over the TCP ports ranging from:
#
# DISPLAY_BASE + 4000
#
# to:
#
# DISPLAY_BASE + 4000 + DISPLAY_LIMIT
#
# By default the user is allowed to specify if a session will run
# unencrypted, for example when running the session across the same
# LAN or when performance is an issue.
#
ENABLE_UNENCRYPTED_SESSION = "0"

#
# Specify path and name of the command 'fuser' to identify processes
# using files or sockets.
#
COMMAND_FUSER = "/bin/fuser"

#
# Specify path and name of the command 'lsof' to list open files.
#
#COMMAND_LSOF = "/usr/sbin/lsof"

#
# Specify path and name of the command 'xauth' to edit and display
# the authorization information used when connecting to the X server.
#
#COMMAND_XAUTH = "xauth"

#
# Specify path and name of the command 'xmodmap' to edit and display
# the keyboard modifier map and keymap table.
#
#COMMAND_XMODMAP = "xmodmap"

#
# Specify path and name of the command starting 'CDE'.
#
#COMMAND_START_CDE = "cdwm"

#
# Enable or disable use of 'xkbcomp' command:
#
# 1: Enabled. Use 'xkbcomp' command.
#
# 0: Disabled.
#
#ENABLE_COMMAND_XKBCOMP = "1"

#
# Specify path and name of the command 'xkbcomp' to compile XKB key-
# board description.
#
#COMMAND_XKBCOMP = "xkbcomp"

#
# Specify location and file name of the keymap file used by 'xkbcomp'.
#
#XKBCOMP_KEYMAP_FILE = "/etc/X11/xkb/keymap/xfree86"

#
# Specify the location and file name of the SSH authorized keys.
#
#SSH_AUTHORIZED_KEYS = "authorized_keys2"

#
# Specify the font server to be used by NX agent. By default the NX
# agent only uses the X11 system fonts. Uncomment the following line
# to enable use of an X Font Server.
#
#AGENT_FONT_SERVER = "unix/:7100"

#
# Specify the path of default X window system startup script.
#
#DEFAULT_X_SESSION = "/etc/X11/xdm/Xsession"

#
# Set the default DPI of the X server to the specified value. This
# should normally not be required, but some desktop applications fail
# to set an appropriate value and fall back to 75 DPI, which is the
# value reported by default by the X server.
#
#DEFAULT_X_DPI = "96"

#
# Specify the path of libraries to be added to the agents environment.
# Be sure that NX libraries are listed first.
#
#AGENT_LIBRARY_PATH = "/usr/NX/lib"

#
# Specify the path of libraries to be added to NX proxy environment.
#
#PROXY_LIBRARY_PATH = "/usr/NX/lib"

#
# Specify a list of libraries to be preloaded in X applications. This key
# is only used when running sessions in single application mode without NX 
# agent encoding. Starting from version 1.5.0, the node doesn't preload the
# NX X11 libraries.
#
# The default is an empty list.
#
# APPLICATION_LIBRARY_PRELOAD = "/usr/NX/lib/libX11.so.6.2:/usr/NX/lib/libXext.so.6.4:/usr/NX/lib/libXcomp.so.1:/usr/NX/lib/libXcompext.so.1:/usr/NX/lib/libXrender.so.1.2"
#
#APPLICATION_LIBRARY_PRELOAD = ""

#
# Specify a list of directories to be added to the library path of X
# clients when run inside a session in single application mode without
# NX agent encoding.
#
# The default is an empty list.
#
# APPLICATION_LIBRARY_PATH = "/usr/NX/lib" 
#
#APPLICATION_LIBRARY_PATH = ""

#
# Enable or disable TCP_NODELAY setting in NX proxy.
#
# 1: Enabled. Let NX client choose whether to enable or not TCP_NODELAY
#    on proxy socket.
#
# 0: Disabled. Disable TCP_NODELAY.
#
# Due to a bug in old Linux kernels, enabling TCP_NODELAY when running
# sessions over PPP links can cause sessions to fail if a serious net-
# work congestion is encountered.
#
PROXY_TCP_NODELAY = "1"

#
# Specify a list of comma-separated options to be added to the
# NX proxy transport. Look at the NX proxy documentation for more
# information about the available options. Options specified in 
# 'PROXY_EXTRA_OPTIONS' override the parameters set by NX client.
#
#PROXY_EXTRA_OPTIONS = "limit=256k,link=modem"

#
# Append arguments to the command line used to run the NX agent for
# RFB (VNC sessions).
#
# Mutiple parameters can be specified by separating them with a blank
# character. Note that, for security reasons, no shell interpretation
# is made.
#
#AGENT_EXTRA_OPTIONS_RFB = "-viewonly"

#
# Append arguments to the command line used to run the NX agent for
# RDP (Windows sessions).
#
# Mutiple parameters can be specified by separating them with a blank
# character. Note that, for security reasons, no shell interpretation
# is made.
#
#AGENT_EXTRA_OPTIONS_RDP = "-m"

#
# Append arguments to the command line used to run the NX agent for
# X (Unix sessions).
#
# Mutiple parameters can be specified by separating them with a blank
# character. Note that, for security reasons, no shell interpretation
# is made.
#
#AGENT_EXTRA_OPTIONS_X = "-nocomposite -noshpix"

#
# Specify the default Window Manager to be used when running single
# applications in a virtual desktop.
#
#DEFAULT_X_WM = "twm"

#
# Specify the domain of the Windows Terminal Server.
#
#DEFAULT_RDP_DOMAIN = ""

#
# Specify the path of base directory where the NX node has to mount
# shares exported by the user. The default value is $(HOME)/MyShares.
#
#SHARE_BASE_PATH = "$(HOME)/MyShares"

#
# Allow the node to use privileged scripts to manage the shares:
# 
# 1: Enabled. The node will use the suid scripts to mount and 
#    unmount the client shares using the SMB or the CIFS file-
#    sharing protocol depending on which protocol is available
#    on both client and server side.
#
# 0: Disabled. The node will forbid any attempt to mount the
#    client shares.
#
#ENABLE_FILE_SHARING = "1"

#
# Specify the path of the directory holding CUPS binaries (f.e. the
# 'lpoptions' program).
#
CUPS_BIN_PATH = "/usr/bin"

#
# Specify the path of the directory holding CUPS programs and reserved
# for administrative purposes (f.e. 'cupsd' or 'lpadmin').
#
CUPS_SBIN_PATH = "/usr/sbin"

#
# Enable or disable CUPS support:
#
# 1: Enabled. Enable CUPS support.
#
# 0: Disabled. Disable CUPS support.
#
ENABLE_CUPS_SUPPORT = "1"

#
# Specify the file-sharing protocol to be used for attaching the
# filesystem to the target directory set by the SHARE_BASE_PATH
# key. The possible values are both,smbfs,cifs or none. 
#
MOUNT_SHARE_PROTOCOL = "none"

#
# Specify the TCP port where the NX node SSHD daemon is running.
#
SSHD_PORT = "3838"

#
# Accept or refuse the NX client connection if SSHD does not export
# the 'SSH_CONNECTION' and 'SSH_CLIENT' variables in the environment
# passed to the NX node.
#
# 1: Refuse. Check the remote IP and don't accept the connection if it
#    can't be determined.
#
# 0: Accept. Check the remote IP and accept the connection even if the
#    remote IP is not provided.
#
#SSHD_CHECK_IP = "0"

#
# Enable or disable running nxsensor:
#
# 1: Enabled.
#
# 0: Disabled.
# 
# Run the nxsensor daemon in the background. This daemon can be used
# to produce statistics about the node machine. Produced data is to
# be queried and elaborated by the nxstat daemon.
#
ENABLE_SENSOR = "1"

#
# The hostname or IP address where the NX server will contact the
# nxsensor daemon to connect the statistics data. The key is also
# used by the nxsensor daemon to find out the network interface
# where it will listen for incoming connections.
#
NODE_SENSOR_HOST = "127.0.0.1"

#
# The port where the NX server will contact the nxsensor daemon to
# collect the statistics data. The key is also used by nxsensor to
# find out the network interface where it will listen for incoming
# connections.
#
NODE_SENSOR_PORT = "19250"

#
# If set, the specified message will be provided to the user if this 
# is the first time the user starts a session on this node. 
#
NODE_FIRST_LOGIN_GREETING = "Welcome to your NX session"

#
# If set, the specified message will be provided to the user every
# time he/she has started a new session on this node.
#
NODE_LOGIN_GREETING = "Welcome to your NX session"


#
# Specify path and name of the command to start the GNOME session
#
COMMAND_START_GNOME="/usr/bin/dbus-launch --exit-with-session gnome-session"

#
# Specify path and name of the command to start the KDE session
#
COMMAND_START_KDE="/usr/bin/dbus-launch --exit-with-session startkde"
# Allow the server to use the privileged scripts to manage the SMB
#  shares.
# 
#  1: Enabled. When running the commands as the target user doesn't
#     work, the server will use the suid scripts to mount and unmount
#     the client shares.
# 
#  0: Disabled. Using the privileged scripts will not be allowed.
#     The mount will only be attempted by running the command as the
#     target user. If the host server is configured to forbid mounts by
#     unprivileged users, the operation will fail.
# 
#  By default, NX node will not use the privileged scripts so that the
#  system will behave according to the suid settings of the smbmount
#  and smbumount commands.
# 
#  Normally smbmount and smbumount can be set suid root to allow any
#  unprivileged user to mount his/her resources. By clearing the suid
#  bit and by letting the node use the privileged scripts, the system
#  administrator can gain greater control on the host node, by allowing
#  unprivileged users to mount their shares only within a NX session.  
#
#ENABLE_PRIVILEGED_SMB_SCRIPTS = "0"

```
-----

server.cfg
```

#
# Set config file format version.
#
CONFIG_FILE_VERSION = "1.0"

#
# Set the log level of NX Server. NX server logs to the syslog all
# the events that are <= to the level specified below, according to
# the following convention:
#
# KERN_ERR         3: Error condition.
# KERN_INFO        6: Informational.
# KERN_DEBUG       7: Debug-level messages.
#
# Note, anyway, that NX server uses level 6 in the syslog to log the
# event. This is intended to override any setting on the local syslog
# configuration that would prevent the event from being actually logged.
#
# The suggested values are:
#
# 6: This is the default value. Only the important events
#    are logged.
#
# 7: Sets logs to level debug.
#
#SESSION_LOG_LEVEL = "6"

#
# Specify hostname for the NX server.
#
#SERVER_NAME = "localhost.localdomain"

#
# Specify the TCP port where the NX server SSHD daemon is running.
#
SSHD_PORT = "3838"

#
# Set the base display number for NX sessions.
#
#DISPLAY_BASE = "1000"

#
# Set the maximum number of displays reserved for NX sessions.
#
#DISPLAY_LIMIT = "200"

#
# Set the maximum number of concurrent NX sessions.
#
#SESSION_LIMIT = "20"

#
# Set the maximum number of concurrent NX sessions that can be run by
# a single user. By default a user can run as many sessions as they
# are allowed on the server. By setting this value to 1, the system
# administrator can force the user to terminate any suspended session
# before starting a new one.
#
#SESSION_USER_LIMIT = "20"

#
# Set for how long NX server will retain data related to terminated
# sessions in its session history.
#
# <0: Never delete data from NX session history.
#
#  0: Disable NX sessions history.
#
# >0: Keep data in session history for this amount
#     of seconds.
#
# The default value, 2592000, lets NX server keep session data
# for 30 days.
#
#SESSION_HISTORY = "2592000"

#
# Allow the server to terminate oldest suspended sessions:
#
# 1: Enabled. Enable the automatic kill of the suspended
#    sessions.
#
# 0: Disabled. Suspended sessions are never terminated.
#
# When this option is set, and the server capacity has been reached,
# i.e. the maximum number of concurrent sessions could be exceeded,
# the server will kill the oldest suspended sessions to make room for
# the new user.
#
ENABLE_AUTOKILL_SESSIONS = "1"

#
# Enable persistent sessions for users. If the option is followed by
# the keyword 'all', all users are allowed to run persistent sessions.
# Alternatively, it can be followed by a list of comma-separated user-
# names. The default value is 'all' which corresponds to enabling
# persistent sessions for all users. Values specified are overriden
# by the value set for the 'DISABLE_PERSISTENT_SESSION' key.
#
#ENABLE_PERSISTENT_SESSION = "all"

#
# Disable persistent sessions for users. If the option is followed by
# the keyword 'all', no user is allowed to run persistent sessions. Al-
# ternatively, the option can be followed by a list of comma-separated
# usernames. The default value is the empty string which corresponds
# to disabling persistent sessions for no user. The values specified
# override the values set for the 'ENABLE_PERSISTENT_SESSION' key.
#
#DISABLE_PERSISTENT_SESSION = ""

#
# Enable or disable SSL encryption of all traffic.
#
#
# 1: Enabled. Unencrypted connections between the proxies will
#    be allowed.                                      
#
# 0: Disabled. Forbid the use of unencrypted connections. The
#    server will force the client to tunnel the proxy
#    connections over the encrypted channel.
#
# Session negotiation always happens across an encrypted channel.
# Normally the user can specify if subsequent communication must
# take place through a direct connection between the proxies or by
# tunneling it through SSH. You may uncomment the following line
# and set the value to 0 to increase the security of the host
# server or if your NX server is behind a firewall preventing
# the access to the set of ports used by the NX server.
#
# Unencrypted sessions require that the firewall lets the proxies
# communicate over the TCP ports ranging from:
#
# DISPLAY_BASE + 4000
#
# to:
#
# DISPLAY_BASE + 4000 + DISPLAY_LIMIT
#
# By default the user is allowed to specify if a session will run
# unencrypted, for example when running the session across the
# same LAN or when performance is an issue.
#
ENABLE_UNENCRYPTED_SESSION = "0"

#
# Enable or disable clipboard:
#
# client: The content copied on the client can be pasted inside the
#         NX session.
#
# server: The content copied inside the NX session can be pasted
#         on the client.
#
# both:   The copy&paste operations are allowed between both the
#         client and the NX session and viceversa.
#
# none:   The copy&paste operations between the client and the NX
#         session are never allowed.
#
#ENABLE_CLIPBOARD = "both"

#
# Enable or disable NX users DB:
#
# 1: Enabled. Only users listed in NX users DB can login to the NX
#    server.
#
# 0: Disabled. All the authenticated users can login.
#
# If the NX user DB is disabled, any user providing a valid password
# from local DB or through SSHD authentication, can connect to the NX
# system. This is likely to be the default when SSHD authentication
# with PAM is enabled.
#
ENABLE_USER_DB = "0"

#
# Enable or disable NX password DB:
#
# 1: Enabled. Use NX password DB to authenticate users.
#
# 0: Disabled. Use SSHD + PAM authentication.
#
# System administrators can enable a restricted set of users to con-
# nect to the NX server by setting ENABLE_USER_DB to 1 and adding
# those users to the DB. If user is enabled to connect, his/her pass-
# word will be verified against the current PAM settings by the SSHD
# daemon.
#
# If both 'ENABLE_USER_DB' and 'ENABLE_PASSWORD_DB' are set to 0, any
# user being authenticated by SSHD account will be enabled to connect
# to the system.
#
ENABLE_PASSWORD_DB = "0"

#
# Specify hostname of the server used for NX SSH authentication.
#
SSHD_AUTH_SERVER = "127.0.0.1"

#
# Specify the TCP port where the SSHD daemon is running on the NX SSH
# authentication server.
#
SSHD_AUTH_PORT = "3838"

#
# Enable or disable statistics:
#
# 1: Enabled. Enable the production of NX statistics.
#
# 0: Disabled. Disable the production of NX statistics.
# 
# Run the nxstat daemon in background. This daemon can be used to
# produce statistics about either the host machine, by elaborating
# data provided by the nxsendor daemon, or the NX services. The NX
# statistics can be queried and displayed by the NX Server Manager.
#
ENABLE_STATISTICS_DB = "1"

#
# Specify the hostname or IP address where the nxsensor daemon will
# be assumed to run.
#
SERVER_SENSOR_HOST = "127.0.0.1"

#
# Specify the port where the server will contact the nxsensor daemon
# to collect the statistics.
#
SERVER_SENSOR_PORT = "19250"

#
# Enable or disable load balancing:
#
# 1: Enabled. Let  NX server decide the node host according to the
#    hosts available in the NX Node DB.
#
# 0: Disabled. Start NX session on localhost.
#
#ENABLE_LOAD_BALANCING = "0"

#
# Specify a list of comma-separated 'hostname:port' values for XDM
# server.
#
#ROUND_ROBIN_XDM_LIST = "localhost:177"

#
# Enable or disable the XDM round robin query:
#
# 1: Enabled. Let NX server decide XDM host according to hostnames
#    that are defined in the ROUND_ROBIN_XDM_LIST key.
#
# 0: Disabled.
#
#ENABLE_ROUND_ROBIN_XDM_QUERY = "1"

#
# Enable or disable the XDM indirect query:
#
# 1: Enabled. Let the user obtain a list of available XDM hosts.
#
# 0: Disabled.
#
#ENABLE_INDIRECT_XDM_QUERY = "0"

#
# Enable or disable the XDM direct query:
#
# 1: Enabled. Let client specify XDM host.
#
# 0: Disabled.
#
#ENABLE_DIRECT_XDM_QUERY = "0"

#
# Enable or disable the XDM broadcast query:
#
# 1: Enabled. Let client connect to the first responding XDM host.
#
# 0: Disabled.
#
#ENABLE_BROADCAST_XDM_QUERY = "0"

#
# Specify path and name of the command 'sessreg'.
#
#COMMAND_SESSREG = "/usr/X11R6/bin/sessreg"

#
# Specify the location and file name of the SSH authorized keys.
#
#SSH_AUTHORIZED_KEYS = "authorized_keys2"

#
# Accept or refuse the NX client connection if SSHD does not export
# the 'SSH_CONNECTION' and 'SSH_CLIENT' variables in the environment
# passed to the NX server.
#
# 1: Refuse. Check the remote IP and don't accept the connection
#    if it can't be determined.
#
# 0: Accept. Check the remote IP and accept the connection even if
#    the remote IP is not provided.
#
#SSHD_CHECK_IP = "0"

#
# Enable or disable support for automatic provision of NX guest users:
#
# 1: Enabled. The NX server creates system accounts for guest users.
#
# 0: Disabled.
#
#ENABLE_GUEST_USER = "0"

#
# Specify the base username to be used by NX server to create guest
# users accounts. The server will add a progressive number to the
# name specified by GUEST_NAME, according to the range of values set
# in the BASE_GUEST_USER_ID and GUEST_USER_ID_LIMIT keys.
#
#GUEST_NAME = "guest"

#
# Set the base User Identifier (UID) number for NX guest users.
#
#BASE_GUEST_USER_ID = "10"

#
# Set the maximum User Identifier (UID) number reserved for NX guest
# users.
#
#GUEST_USER_ID_LIMIT = "200"

#
# Set the Group Identifier (GID) for NX guest users. The specified
# GID must already exist on the system.
#
#GUEST_USER_GROUP = "guest"

#
# Set the maximum number of concurrent NX guest users.
#
#GUEST_USER_LIMIT = "10"

#
# Set the maximum number of NX sessions a NX guest user can run before
# his/her account is terminated.
#
#GUEST_USER_CONNECTION_LIMIT = "5"

#
# Set for how long the NX server has to retain NX guest users accounts.
#
#  0: NX guest users accounts are never removed.
#
# >0: Maintain NX guest users accounts for this amount
#     of seconds.
#
# The default value, 2592000, lets NX server keep guest users accounts
# for 30 days.
#
#GUEST_USER_ACCOUNT_EXPIRY = "2592000"

#
# Set for how long the NX server has to keep alive a NX guest user's
# session. When the time is expired, NX server will kill the session.
#
#  0: NX guest user's session is never terminated.
#
# >0: Keep alive NX guest user' session for this amount
#     of seconds.
#
#GUEST_CONNECTION_EXPIRY = "0"

#
# Enable or disable possibility for NX guest users to suspend sessions:
#
# 1: Enabled. The NX server lets NX guest users suspend sessions.
#
# 0: Disabled.
#
#GUEST_USER_ALLOW_SUSPEND = "1"

#
# Set the home directory for NX guest users. If an empty value is
# specified, the NX server will create the guest user's home in the
# default directory set on the system. 
#
#GUEST_USER_HOME = "/home"

#
# Enable or disable removing the guest user from the system when the
# account is expired:
#
# 1: Enabled. When the guest account is expired, the NX server will
#    delete the account from both the system and the NX guests DB
#    and will remove the home directory.
#
# 0: Disabled. When the guest account is expired, the NX server will
#    keep the guest account on the system but will forbid this user
#    to start new sessions on the server.
#
#ENABLE_GUEST_WIPEOUT = "1"

#
# Allow the server to set disk quota for the guest accounts:
#
# 1: Enabled. When a new guest account is created on the system,
#    the server will set the disk quota for this user.
#
# 0: Disabled. No restrictions on the amount of disk space used
#    by each guest user are applied.
#
#ENABLE_GUEST_QUOTA = "0"

#
# Specify the username of the account to be used as a protoype for
# propagating its disk quota settings to all the new guest accounts.
# If the softlimit or the hardlimit on either the inode or the disk
# block are set, they will override the settings applied to the user
# prototype.
#
#GUEST_QUOTA_PROTONAME = "protoguest"

#
# Specify the maximum amount of disk space available for each of the
# guest users, checked as number of inodes. This limit can be exceeded
# for the grace period.
#
#GUEST_QUOTA_INODE_SOFTLIMIT = "0"

#
# Specify the absolute maximum amount of disk space available for
# each of the guest users, checked as number of inodes. Once this
# limit is reached, no further disk space can be used.
#
#GUEST_QUOTA_INODE_HARDLIMIT = "0"

#
# Specify the maximum amount of disk space available for each of the
# guest users, checked as number of disk blocks consumed. This limit
# can be exceeded for the grace period.
#
#GUEST_QUOTA_BLOCK_SOFTLIMIT = "0"

#
# Specify the absolute maximum amount of disk space available for each of the
# guest users, checked as number of disk blocks consumed. Once this
# limit is reached, no further disk space can be used.
#
#GUEST_QUOTA_BLOCK_HARDLIMIT = "0"

#
# Specify the grace period, expressed in seconds, during which the
# soft limit, set in the GUEST_QUOTA_INODE_SOFTLIMIT key may be
# exceeded.
#
#GUEST_QUOTA_INODE_GRACE_PERIOD = "0"

#
# Specify the grace period, expressed in seconds, during which the
# soft limit, set in the GUEST_QUOTA_BLOCK_SOFTLIMIT key may be
# exceeded.
#
#GUEST_QUOTA_BLOCK_GRACE_PERIOD = "0"

#
# Specify a list of comma-separated filesystem names or devices to
# which the disk quota restrictions will be applied. The default
# value is 'all' which corresponds to applying the disk quota limits
# to all the filesystems having disk quota enabled.
#
#GUEST_QUOTA_FILESYSTEMS = "all"

#
# Set the User Identifier (UID) number for NX users. If an empty value
# is specified, the NX server will create the account with the default
# value set on the system.
#
#USER_ID = "10"

#
# Set the Group Identifier (GID) for NX users. If an empty value is
# specified, the NX server will create the account with the default
# value set on the system.
#
#USER_GROUP = "users"

#
# Set the home directory for NX users. If an empty value is specified,
# the NX server will create the user's home in the default directory
# set on the system.
#
#USER_HOME = "/home"


```
-----

NXClient detail
```

NX> 203 NXSSH running with pid: 2209
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 68.54.239.81 on port: 3838
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 2.1.0-18 - LFE
NX> 105 Hello NXCLIENT - Version 2.1.0
NX> 134 Accepted protocol: 2.1.0
NX> 105 Set shell_mode: shell
NX> 105 Set auth_mode: password
NX> 105 Login 
NX> 101 User: tannedin
NX> 102 Password: *******
NX> 103 Welcome to: nocturne user: tannedin
NX> 105 Listsession --user="tannedin" --status="suspended\054running" --geometry="1280x800x24+render" --type="unix-gnome" 
NX> 127 Available sessions: 

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------

NX> 148 Server capacity: not reached for user: tannedin
NX> 105 Start session with: --link="isdn" --backingstore="1" --streaming="1" --nodelay="1" --encryption="1" --cache="32M" --images="128M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="Nocturne" --type="unix-gnome" --geometry="800x600+240+76" --client="linux" --keyboard="pc105\057us" --screeninfo="800x600x24+render" 
NX> 595 ERROR: A fatal error occurred in NX Server.
Killed by signal 15.

```
-----

cat /var/log/messages | grep A9A2CF61
```

Feb  1 12:22:54 nocturne NXSERVER 2.1.0-18[12350]: ERROR: (exception id A9A2CF61) NX> 596 ERROR: NXNODE Ver. 2.1.0-15  (Error id e0203C2)
Feb  1 12:22:54 nocturne NXSERVER 2.1.0-18[12350]: ERROR: (exception id A9A2CF61) NX> 596 ERROR: Thu Feb  1 12:22:52 2007 running as user: 'tannedin' (uid: 1000) on ''
Feb  1 12:22:54 nocturne NXSERVER 2.1.0-18[12350]: ERROR: (exception id A9A2CF61) NX> 596 ERROR: in node start session: create session: run commands
Feb  1 12:22:54 nocturne NXSERVER 2.1.0-18[12350]: ERROR: (exception id A9A2CF61) NX> 596 ERROR: execution of last command failed
Feb  1 12:22:54 nocturne NXSERVER 2.1.0-18[12350]: ERROR: (exception id A9A2CF61) NX> 596 last command: /bin/bash --login -c 'xauth -v source /home/tannedin/.nx/C-nocturne-1007-5E8E5273763678FD3B9D21F9FAAC642E/scripts/authority'
Feb  1 12:22:54 nocturne NXSERVER 2.1.0-18[12350]: ERROR: (exception id A9A2CF61) NX> 596 exit value: 1
Feb  1 12:22:54 nocturne NXSERVER 2.1.0-18[12350]: ERROR: (exception id A9A2CF61) NX> 596 stdout: 
Feb  1 12:22:54 nocturne NXSERVER 2.1.0-18[12350]: ERROR: (exception id A9A2CF61) NX> 596 stderr: xauth:  error in locking authority file /home/tannedin/.Xauthority
Feb  1 12:22:54 nocturne NXSERVER 2.1.0-18[12350]: ERROR: (exception id A9A2CF61) NX> 596 init: stdin arguments: user=tannedin,userip=68%2e54%2e239%2e81,uniqueid=5E8E5273763678FD3B9D21F9FAAC642E,display=1007,license=%28None%29,subscriptionid=None,productid=LFE,reconnect=1,balance_host=192%2e168%2e1%2e112,encryption_mode=3,connection=local,images=128M,cache=32M,client=linux,media=0,backingstore=1,encryption=1,strict=0,clipboard=both,shpix=1,rootless=0,composite=1,session=Nocturne,shmem=1,type=unix%2dgnome,virtualdesktop=1,screeninfo=800x600x24%2brender,nodelay=1,streaming=1,keyboard=pc105%2fus,geometry=800x600%2b240%2b76,link=isdn
Feb  1 12:22:54 nocturne NXSERVER 2.1.0-18[12350]: ERROR: (exception id A9A2CF61) NXNodeExec::exec('startsession', 'user=tannedin&userip=68%2e54%2e239%2e81&uniqueid=5E8E5273763678F...', 'localhost', 3838) called at handlers/nxserver.pl line 2868
Feb  1 12:22:54 nocturne NXSERVER 2.1.0-18[12350]: ERROR: (exception id A9A2CF61) NXShell::handler_session_start('--link="isdn" --backingstore="1" --streaming="1" --nodelay="1" -...') called at NXShell.pm line 374
Feb  1 12:22:54 nocturne NXSERVER 2.1.0-18[12350]: ERROR: (exception id A9A2CF61) NXShell::handle_command('startsession', '--link="isdn" --backingstore="1" --streaming="1" --nodelay="1" -...') called at NXShell.pm line 145
Feb  1 12:22:54 nocturne NXSERVER 2.1.0-18[12350]: ERROR: (exception id A9A2CF61) NXShell::run() called at nxserver.pl line 4519
Feb  1 12:22:54 nocturne NXSERVER 2.1.0-18[12350]: ERROR: (exception id A9A2CF61) eval {...} called at nxserver.pl line 4478

```
-----------
anyone have any ideas?

---

### Post by TwoWordz on 2007-02-06
Hello,

I would just do a 

apt-get remove --purge nxclient nxnode nxserver

then

rm -rf /usr/NX

then reinstall. 

What was the other setting you changed regarding ssh? Are you running ssh on an different port? If so, I don't think you need to change anything to nx configuration.

TW.

---

### Post by tannedin on 2007-02-06
SSH is configured on a different port.  This is mostly because my router cannot handle direct port forwarding.  The other reason is simply port hiding.

When I tried NX without changing the config files without the changes for the SSH, server & node freaked out because they couldn't connect to localhost.  At that point I dug through the configs and found an actual part regarding SSH Ports, hence the change.

---

### Post by 2pi on 2007-03-20
Hi Tannedin,

just try to delete the .Xauthority file of the user you want to log in. I had the same error messages from the server - then i connected via ssh -X and tried to start a gnome-terminal -> there has been a failure with the locking of the .Xauthority.
After deleting the .Xauthority in the users home ssh -X and nx worked well

hope this helps.

2pi

---

### Post by tannedin on 2007-03-21
well, living the Army Barracks has taken its toll on exactly how my machines are connected, which obviously greatly annoys me.  So, as soon as I get ethernet to one of the machines, I'll be sure to try that out and hopefully I'll remember to post my findings

Thank for the suggestion
-Gaibryel

---

### Post by serpentine on 2007-04-30
tannedin,

Here's the official NX guide to follow for installation for port 22 use on Ubuntu:

[http://www.nomachine.com/ar/view.php?ar_id=AR12D00432](http://www.nomachine.com/ar/view.php?ar_id=AR12D00432)

/John

---

