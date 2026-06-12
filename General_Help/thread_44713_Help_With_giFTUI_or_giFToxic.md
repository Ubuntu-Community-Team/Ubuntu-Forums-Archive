---
title: "Help With giFTUI or giFToxic?"
date: 2005-06-27
forum: General Help
---

### Post by polo_step on 2005-06-27
Haven't had any luck at getting either of these giFT frontends to work, nor do I see anything in search.

Is there a better giFT frontend or any help in getting one of these to operate properly?

Thanks for any help!

---

### Post by skoal on 2005-06-27
I'm pretty sure they work as is, since I've used them before but still prefer 'giFTcurs'.  I think all you need to do is start the giFT daemon up first prior to launching one of those GUI clients.  For me, I think all I do is:

skoal@morpheus:///tmp $ [COLOR=DarkRed]giftd -d[/COLOR]
[10:02:36] giFT: 26910
skoal@morpheus:///tmp $ [COLOR=DarkRed]giFToxic[/COLOR]

and then I'm off and running to commit some petty theft...

\\//_

---

### Post by polo_step on 2005-06-27
Odd, but I can't get giftcurs to do much.  I do the giftd -d thing and get a response:
=================================
anonymous@beatdown:~$ giftd -v
[08:46:01] giftd 0.11.8.1 (Dec 12 2004 22:42:45) started
[08:46:01] *** GIFT-ERROR: bind: Address already in use
[08:46:01] *** GIFT-FATAL: Failed to load interface subsystem

NOTE:
There may be another giFT daemon running on this host.  Check to see if the
interface port (1213) is currently in use by another process.

[08:46:01] *** Often times more information can be found in the log file or with the -v command line switch.
==================================

When I try to run giftui, I get:

==================================
anonymous@beatdown:~$ giftui
giftui : No host to connect /apps/giftui/daemon/host.
==================================

---

### Post by skoal on 2005-06-27
Just a few things to consider:
[list]
[*]Have you already run the 'gift-setup'?  You're supposed to do that right after you install the 'giFT' package.  There's not any GUI setup tool for giFT that I know of...
[*]The 'giftd -v' (the -v switch) is pretty useless on it's own unless you combine it with another option, as in 'giftd -vd'.  Check your ~/.giFT path for the log file it pipes messages to:
```
skoal@morpheus://~/.giFT $ ls
giftd.conf  giftd.log  Gnutella  OpenFT  shares  ui
```
[/list]
* When you try to launch giftd with just a -v switch, you'll get that error message you last posted whether giftd was already running or not.

\\//_

---

### Post by polo_step on 2005-06-27
[QUOTE=skoal]Have you already run the 'gift-setup'?  You're supposed to do that right after you install the 'giFT' package.  [/quote]
Yeah, I did, though it was mostly just with the defaults.

> Check your ~/.giFT path for the log file it pipes messages to:
```
skoal@morpheus://~/.giFT $ ls
giftd.conf  giftd.log  Gnutella  OpenFT  shares  ui
```

I get:
==================================
anonymous@beatdown:~$ ~/.giFT $ ls
bash: /home/anonymous/.giFT: is a directory
==================================

I don't actually find any such directory under /home/anonymous/ though.  :???:

---

### Post by skoal on 2005-06-27
oops! maybe you initially ran gift-setup using sudo?  Check your /root/.giFT and see if you have all those configuration settings there.  I would just re-run gift-setup (*as normal user*) and see what happens.  I've attached my 'gift.conf' for you to comparw against.  I think the only changes I made to defaults were my download/upload/shareable paths...

\\//_

---

### Post by polo_step on 2005-06-27
[QUOTE=skoal]maybe you initially ran gift-setup using sudo?  [/quote]

No.
> Check your /root/.giFT and see if you have all those configuration settings there. 
Nope.  I do see what LOOKS like those fines in /user/share/giFT though the file looks like a template.

It would appear that running setup -- which I've done several times -- does not leave a saved configuration file anywhere.  Mysterious...

I run a system search for giFT.conf and it turns up nothing.

---

### Post by polo_step on 2005-07-06
Ah!  My problem was that I didn't understand the hidden file thingy, which I have now squared away.

After running giftd -d in terminal, I can load giFTcurs and have it work, but not giFTui, which fails to run. It tries to load, but never makes it.

I'm also not sure which filesharing network I'm connecting to.  Whatever it is, it's pretty small, with a userbase of only around 100K.


Here's the gifd.conf file:
================================
# $Id: giftd.conf.template,v 1.6 2004/09/08 12:05:32 mkern Exp $
###############################################################################

###############################################################################
# MAIN

[main]

#
# Boolean determining whether or not this file has been reviewed and is
# complete.  giFT will fail to start unless this is non-zero.  This is done
# so that we can make sure you, at the very least, read through this file.
#
# Default: 0
#
setup = 9

#
# Space separated list of hosts to allow connection to giFT's interface
# protocol (running default on port 1213).  This protocol is used for GUIs
# to communicate with giFT and could be considered a security risk to allow
# external connections.
#
# The following special keywords are supported:
#
#  ALL       - Synonym for 0.0.0.0/0
#  LOCAL     - Synonym for 127.0.0.0/8 192.168.0.0/16 172.0.0.0/11 10.0.0.0/8
#
# Bitwidth fields are optional.
#
# Default: LOCAL
#
hosts_allow = LOCAL

#
# Port on which to listen for user interface connections.  Unless you have a
# special need to talk to the client on a non-standard port, just accept the
# default.
#
# NOTE:
#  If you change this value, you will also need to modify the ui.conf
#  configuration for the machine which will be making outgoing connections
#  here.
#
client_port = 1213

#
# Determines whether or not to follow symbolic links.  If this value is set
# non-zero, symlinks will be traversed and a directory inode tracking system
# will be used to ensure that giFT does not descend the same directory
# twice.  If you do not have any symlinks or do not want them traversed, set
# this to 0 for a very minor efficiency gain.
#
# Windows users: this setting has no effect.
#
# Default: 1
#
follow_symlinks = 1

#
# Colon separated list of protocol plugins to load by default.  If dynamic
# library support is enabled, the plugin specified will be stat'd to check if
# it is a loadable path.  If that fails, the fallback method is to attempt to
# construct the fully qualified path based on the configured environment.
#
# NOTES:
#  Without dynamic library support, this plugin must have been compiled into
#  your giFT binary.  With, this plugin must exist in the installed
#  plugin directory.  giFT -V will output this path to you, if you are not
#  sure.
#
#  Protocol names are case sensitive, so use OpenFT, not Openft.
#
# For example, to use the OpenFT and Gnutella protocols use:
#
#  OpenFT:Gnutella
#
# Default: none
#
plugins = OpenFT:Gnutella

###############################################################################
# DOWNLOAD CONTROLS

[download]

#
# Directory to store transfers while they are being operated on.  Temporary
# state files are also kept here.  It is recommended, but not required, that
# the incoming and completed directories are on the same partition (drive).
#
# Windows users: please use the following path specification:
#
# incoming=/[drive]/dir1/dir2
#
# For example, to refer to C:\Program Files\giFT\incoming, use:
#
# incoming=/C/Program Files/giFT/incoming
#
# Default (*nix):    ~/.giFT/incoming
# Default (Windows): /C/Program Files/giFT/incoming
#
incoming = ~/.giFT/incoming

#
# Directory which will contain files after they have successfully finished
# downloading.
#
# Default (*nix):    ~/.giFT/completed
# Default (Windows): /C/Program Files/giFT/completed
#
completed = ~/.giFT/completed

###############################################################################
# SHARE SUBMISSION AND UPLOAD CONTROL

[sharing]

#
# Maximum amount of uploads allowed from the same user at any given time.  It
# is recommended that you keep this at 1 in order to prevent users from
# unfairly queueing your connection.
#
# Default: 1
#
max_peruser_uploads = 1

#
# Determines whether or not to hide directories which contain a leading dot.
# These directories are commonly meant to be "hidden" and thus should not be
# submitted to the network.  Selecting 0 here will submit all directories.
#
# On Windows files will additionally be checked for the hidden attribute and
# not shared if it is set and hide_dot_files is 1.
#
# Default: 1
#
hide_dot_files = 1

#
# Colon separated list of fully qualified paths you wish to share.  These
# directories will be recursed at giFT's startup and the files contained
# within will be subjected to an MD5 hashing.  The results will be cached and
# will only be recalculated on a per share basis when the size or
# modification time in the cache and on disk disagree, or the file name is
# changed.
#
# Sanity notice:
#  Do NOT share source directories!  Remote nodes will refuse to index your
#  shares if you are attempting to submit more than 64000 files.
#
# Security notice:
#  Do not share directories which may contain sensitive information, such as
#  ~ ($HOME).  Also note that any directories shared here will be stripped of
#  all but the last path element when submitted to other nodes for indexing,
#  effectively "hiding" the directory prefix.
#
# Windows users: please use the following path specification:
#
#  /[drive]/dir1/dir2:/[drive]/dir3/dir4 ...
#
# For example, to refer to C:\Program Files\giFT\shares and D:\shares, use:
#
#  /C/Program Files/giFT/shares:/D/shares
#
# Default: none
#
root = 

#
# Maximum amount of simultaneous uploads allowed.  Setting this to 0 will
# cause giFT to not limit outgoing transfers.  Use shares_hidden to disable
# sharing.
#
# Default: 0
#
max_uploads = 0

#
# Whether we allow sharing.  Setting this to 0 will allow sharing and uploads
# up to max_uploads.  If this is 1 your shares will be hidden from the world
# and uploading will be denied.  This may also be handled at run time via your
# GUI of choice.
#
# Default: 0
#
shares_hidden = 0

#
# Controls when giFT periodically rescans your shared directories for any
# changes (new files, missing files, changed files, etc.) and communicates
# those changes to the underlying protocols.  This parameter specifies how
# often (in seconds) you want that to happen.
#
# For your reference
# ==================
# 0        turns off periodic auto-resync
# 3600     one hour
# 86400    one day
# 604800   one week
#
# Default: 86400
#
auto_resync_interval = 86400

#
# Controls whether or not giFT should automatically share files that you have
# finished downloading.  This feature significantly improves the network's
# abundance of files and helps ease the load on those sharing popular files.
# It's a Good Thing (TM), please leave it on.
#
# Avoid setting your completed directories through sharing/root, as that
# setting will duplicate recursion of the completed directory and cause
# generally undesirable results.
#
# Default: 1
#
share_completed = 1

#
# Controls whether giFT ignores the incoming directory when sharing files. If
# this is 1 and the incoming directory is within one of the sharing roots all
# files in and below it will not be shared. This is what you want in all known
# universes. Should you find yourself running this software on a parallel
# world where it is necessary to share the incoming files please make sure it
# doesn't affect us back here. Thank you.
#
# Default: 1
#
ignore_incoming = 1

###############################################################################
# USER SPACE BANDWIDTH CONTROL

[bandwidth]

#
# Bandwidth throttling allows giFT to have some basic control over your
# bandwidth usage.  This code operates in user space, and as a result can not
# guarantee perfect accuracy.  If you wish to use this feature, please
# consider using a more reliable kernel space option first.  As always, google
# should be able to assist you there.
#
# The following configuration switches control the maximum number of bytes
# per second allowed for the given stream direction.  A setting of 0 will
# disable throttling for that direction.
#
# Default: 0
#
downstream = 0
upstream = 0

---

### Post by dolson on 2005-09-12
giftUI doesn't work for me either (using Breezy at the moment). I get a segmentation fault.

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread -1217964352 (LWP 5553)]
0xb7b00e18 in g_strdup () from /usr/lib/libglib-2.0.so.0

I was running giftUI successfully in Debian Sid just hours ago.

---

### Post by dextur on 2005-11-16
I have exactly the same problem.

Try specifying -s 127.0.0.1 and -p 1213 on the command line for giftui. That takes me one step further. to this: 

** (giftui:10006): CRITICAL **: str_to_color: assertion `str != NULL' failed
** (giftui:10006): CRITICAL **: str_to_color: assertion `str != NULL' failed
Segmenteringsfel

---

### Post by tequila mambo on 2008-06-07
Hi,

I have successfully installed and configured gift, unfortunately neither giftui nor apollon won't connect to any of the networks I have registered. Ares, Gnutella, Fastrack and OpenFT are successfully registered. When I start Giftui or Apollon, they show the four networks and the general status is "connected". The problem is that non of the networks will show any user or files. Every field of information about the networks is in zeros, even the local files.

Other p2p programs like amule work fine, nevertheless I need to get gift running, specially Ares network.

Any idea of what is going on?

---

### Post by rapper97 on 2008-06-25
[This thread]("http://ubuntuforums.org/showthread.php?t=198945") may be of some help to you - it was of some help to me; Gnutella works fine now, but Ares still gets hung up on "Connecting..."  I am unsure if it's just a matter of patience.

---

