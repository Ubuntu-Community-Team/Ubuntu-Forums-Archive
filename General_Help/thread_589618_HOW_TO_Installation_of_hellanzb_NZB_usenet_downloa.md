---
title: "HOW TO: Installation of hellanzb NZB usenet downloader"
date: 2007-10-24
forum: General Help
---

### Post by TuxCrafter on 2007-10-24
== news ==

this script is kind of absolute now, just enter the below command to install hellanzb and configure the config file in $HOME/.hellanzb

```
 sudo apt-get install hellanzb
```

== ==== ==

HOW TO: Installation of hellanzb NZB usenet downloader

#Version:       0.0.8
#Date:          23-10-07
#Description:   Installation of hellanzb NZB usenet downloader and personal configuratin file

This script has both community support and commercial support.

Please post all your feedback about this script so I can continuously keep improving it.

I hope this script will help a lot of people!

Note: Hellanzb support scripts for better desktop integration will be posted in the near future.

---

### Post by K.Mandla on 2007-10-26
Moved to General Help.

---

### Post by mikebeecham on 2007-11-25
Sorry..being a bit of a noob Tuxcrafter, but how do install the .sh file of yours?  I have uninstalled hellanzb, and now have downloaded yours from your sig link?

---

### Post by TuxCrafter on 2007-11-25
> **mikebeecham said:**
> Sorry..being a bit of a noob Tuxcrafter, but how do install the .sh file of yours?  I have uninstalled hellanzb, and now have downloaded yours from your sig link?

open a terminal and execute the following command:

bash /path/to/script/hellanzb.sh

---

### Post by M3lon on 2007-11-26
solved

---

### Post by mikebeecham on 2007-11-26
Nope....I'm still getting the same Import error I was getting with the other Hellanzb version!



Not solved!

---

### Post by Kokanee-YYZ on 2008-01-29
Your bash script worked perfectly.  Thank you very much - you're a *nix guru! :)

---

### Post by terry_gardener on 2008-02-17
seems to work perfectly, so much easier to setup than the manual way. 

when i open it get c yenc module message after the location of the conf file, is this correct. 

Thanks again

---

### Post by TuxCrafter on 2008-02-17
> **terry_gardener said:**
> seems to work perfectly, so much easier to setup than the manual way. 

when i open it get c yenc module message after the location of the conf file, is this correct. 

Thanks again

jups that is correct, the c yenc module is faster

---

### Post by hscbaj on 2008-02-17
[code]Traceback (most recent call last):
  File "/usr/bin/hellanzb", line 14, in <module>
    from Hellanzb.Core import main
  File "/usr/lib/python2.5/site-packages/Hellanzb/Core.py", line 17, in <module>
    from Hellanzb.Daemon import initDaemon, postProcess
  File "/usr/lib/python2.5/site-packages/Hellanzb/Daemon.py", line 12, in <module>
    from twisted.scripts.twistd import daemonize
ImportError: cannot import name daemonize
[/quote]
Yes, I've tried installing it from the script file on this thread. Yes, I've installed it 1,2,3 as it suggests... Ive followed guides from other people on similar threads but I can't get the thing to work :(

Help?

---

### Post by darkworld on 2008-02-25
new to hellaznb. Ive installed via script, did the best i could in hellanzb.conf and found the hidden daemon folders in home directory. I did get some errors when installing so this maybe the issue. However, hellanzb, at command line fires it up and connects. 

Now I tried hellanzb.py at command line and it says command not found. A search of system reveals no hellaznb.py on system. Im not sure at all what im doing, what should this command do as opposed to just hellanzb?

---

### Post by TuxCrafter on 2008-02-25
> **darkworld said:**
> new to hellaznb. Ive installed via script, did the best i could in hellanzb.conf and found the hidden daemon folders in home directory. I did get some errors when installing so this maybe the issue. However, hellanzb, at command line fires it up and connects. 

Now I tried hellanzb.py at command line and it says command not found. A search of system reveals no hellaznb.py on system. Im not sure at all what im doing, what should this command do as opposed to just hellanzb?

the ubuntu packager of hellanzb renamed the hellanzb.py command to hellanzb so if you use the upstream version user hellanzb.py and if you installed the ubuntu version use hellanzb

---

### Post by Nicepen on 2008-04-14
I also get the twisted.copyright import error.  I have installed this on my own (many ways) and I have used the script to remove hellanzb and then reinstall it.  I know the problem is with Twisted and I think it puts the libs in two spots.  I ended up with part of my twisted lib in a directory that python doesn't want to read from.  Here is the error I get when I run "hellanzb.py"  

Traceback (most recent call last):
  File "/usr/local/bin/hellanzb.py", line 14, in <module>
    from Hellanzb.Core import main
  File "/usr/local/lib/python2.5/site-packages/Hellanzb/Core.py", line 9, in <module>
    from Hellanzb.HellaReactor import HellaReactor
  File "/usr/local/lib/python2.5/site-packages/Hellanzb/HellaReactor.py", line 11, in <module>
    import twisted.copyright
ImportError: No module named twisted.copyright



Please Help!  I have done lots of searching and all I can find is other people with the same problem.

---

### Post by pabloikba on 2008-05-01
So I believe I have everything installed and working (?).
From terminal I run hellanzb (Ubuntu).
It confirms by stating:

hellanzb v0.13 (config = /etc/hellanzb.conf, C yenc module)
(giganews) Opening 10 connections...
hellanzb - Now monitoring queue...

I used Firefox to download an .nzb file to the queue directory (as stated in the hellanzb.conf file. It just sits there with nothing happening.

What am I doing wrong?

Pablo

---

### Post by TuxCrafter on 2008-05-01
> **pabloikba said:**
> So I believe I have everything installed and working (?).
From terminal I run hellanzb (Ubuntu).
It confirms by stating:

hellanzb v0.13 (config = /etc/hellanzb.conf, C yenc module)
(giganews) Opening 10 connections...
hellanzb - Now monitoring queue...

I used Firefox to download an .nzb file to the queue directory (as stated in the hellanzb.conf file. It just sits there with nothing happening.

What am I doing wrong?

Pablo

can you try manually putting the nzb file in the query directory of hellanzb

---

### Post by pabloikba on 2008-05-01
If you mean "queue" directory, it is there....I do not have a "query" directory....

---

### Post by pabloikba on 2008-05-01
> **pabloikba said:**
> If you mean "queue" directory, it is there....I do not have a "query" directory....r

Here is copy of conf file (I changed password & username only):

# 
# hellanzb.conf - sample hellanzb configuration file
#
# To quickly get started, change the default defineServer() call and the
# Hellanzb.PREFIX_DIR directory
#
# This is actually interpreted python code: strings must be surrounded by
# quotes, numbers and the 'None' keyword should not
# 
# $Id: hellanzb.conf.sample 1057 2007-03-27 04:13:53Z pjenvey $

# Log output to this file, set to None (no single quotes) for no logging
Hellanzb.LOG_FILE = None
# os.path.expanduser('~') + '/.hellanzb/log/'

# Uncomment this line to log DEBUG messages to the specified file
Hellanzb.DEBUG_MODE = os.path.expanduser('~') + '/.hellanzb/log-debug'

# Automatically roll over both log files when they reach LOG_FILE_MAX_BYTES
# size
Hellanzb.LOG_FILE_MAX_BYTES = 0

# Save LOG_FILE_BACKUP_COUNT of those rolled over log files
Hellanzb.LOG_FILE_BACKUP_COUNT = 0


# Define server connections. Servers can have multiple hosts, hellanzb will
# persist the number of connections to each specified server. There may be
# multiple defineServer lines.

# Set both the username and password to 'None' (without the quotes) if your
# usenet server does not require authorization
defineServer(id = 'giganews',
             hosts = [ 'news.giganews.com:443' ],
             #hosts = [ 'news.changeme.com', 'morenews.changeme.com:8000' ],


             username = 'gn??????',
             password = '????????',
             #username = None,           # no auth
             #password = None,

             connections = 20,
             antiIdle = 4.5 * 60,        # 4 minutes, 30 seconds, 0 to disable
             #bindTo = '204.31.33.7',    # connect FROM this ip address
             #enabled = False,           # disable this server
             #skipGroupCmd = False,      # skip sending nntp GROUP commands
             #fillserver = 0,            # defaults to 0 (a main server).
                                         # fillservers must have values > 0
                                         # (priority)
             ssl = True
             )

# Uncomment this line to limit all server connections to the specified KB/s
# bandwidth
#Hellanzb.MAX_RATE = 150 # limit to 150kB/s


# Important locations
# Hellanzb.PREFIX_DIR = os.path.expanduser('~') + '/.hellanzb/'
Hellanzb.PREFIX_DIR = 'home/zack/Desktop/NZB/'

# Where to put queued .nzb files
Hellanzb.QUEUE_DIR = Hellanzb.PREFIX_DIR + 'queue/'

# Where the fully processed archives go
Hellanzb.DEST_DIR = Hellanzb.PREFIX_DIR + 'done/'

# The .nzb currently being downloaded is stored here
Hellanzb.CURRENT_DIR = Hellanzb.PREFIX_DIR + 'current/'

# The archive currently being downloaded is stored here
Hellanzb.WORKING_DIR = Hellanzb.PREFIX_DIR + 'working/'

# Archives interrupted in the middle of downloading are stored here temporarily
Hellanzb.POSTPONED_DIR = Hellanzb.PREFIX_DIR + 'postponed/'

# Archives currently being processed. May contains archive directories, or
# symbolic links to archive directories
Hellanzb.PROCESSING_DIR = Hellanzb.PREFIX_DIR + 'processing/'

# Temp storage
Hellanzb.TEMP_DIR = Hellanzb.PREFIX_DIR + 'temp/'

# Filename to store hellanzb state in between CTRL-Cs. The state (includes the
# order of the queue, and smart par recovery information) is intermittently
# written out as XML to this file
Hellanzb.STATE_XML_FILE = Hellanzb.PREFIX_DIR + 'hellanzbState.xml'


# _Sub directory within the nzb archive dir_ to move processed files to
Hellanzb.PROCESSED_SUBDIR = 'processed'

# Remove the PROCESSED_SUBDIR if the archive was successfully post processed. 
# Warning: The normal Hellanzb.LOG_FILE should be enabled with this option --
# for a record of what hellanzb deletes
Hellanzb.DELETE_PROCESSED = True


# Maximum amount of memory used to cache encoded Article data segments.
# hellanzb will write article data to disk when this cache is exceeded
# Available settings:
# -1: Unlimited size
#  0: Disable cache (only cache to disk)
# >0: Limit cache to this size, in bytes, KB, MB, e.g.:
#     1024 '1024KB' '100MB' '1GB'
#Hellanzb.CACHE_LIMIT = 0


# Save archives into a sub directory of DEST_DIR named after their newzbin.com
# category (when queued using the enqueuenewzbin XMLRPC call); e.g. Apps,
# Movies, Music
Hellanzb.CATEGORIZE_DEST = True

# Disable SMART_PAR (download all PAR files)
#Hellanzb.SMART_PAR = False

# Supply a path to the (un)rar command
#Hellanzb.UNRAR_CMD = None

# Supply a path to the par2 command
Hellanzb.PAR2_CMD = '/usr/bin/par2'

# Skip unraring during post processing
Hellanzb.SKIP_UNRAR = True

# Supply a path to the optional macbinconv command (for converting MacBinary
# files)
#Hellanzb.MACBINCONV_CMD = None

# hellanzb inherits the umask from the current user's environment (unless it's
# running in daemon mode). The umask can be forced with this option
#Hellanzb.UMASK = 0022


# Supported music types (case insensitive) and optionally their decompression
# executables
# and the file type that executable will decompress to (case insensitive). The
# exes must be in the PATH.
#
# <FILE> will be replaced with the name of music file
# optional <DESTFILE> is <FILE> with the specified extension
#
# None means these files don't need to be decompressed
defineMusicType('wav', None, None)
defineMusicType('mp3', None, None)
#defineMusicType('ape', 'mac <FILE> <DESTFILE> -d', 'wav')
#defineMusicType('flac', 'flac -d -- <FILE>', 'wav')
#defineMusicType('shn', 'shorten -x < <FILE> > <DESTFILE>', 'wav')

# Max files we should decompress at the same time
Hellanzb.MAX_DECOMPRESSION_THREADS = 2


# Enable Mac OS X Growl notifications
Hellanzb.GROWL_NOTIFY = False

# The growl notification server, in the format 'hostname'
Hellanzb.GROWL_SERVER = 'IP'

# The growl password
Hellanzb.GROWL_PASSWORD = 'password'


# Enable libNotify Daemon notifications
Hellanzb.LIBNOTIFY_NOTIFY = False


# Disable ANSI color codes in the main screen (preserves the in place scroller)
#Hellanzb.DISABLE_COLORS = False

# Disable ALL ANSI color codes in the main screen (for terminals that don't
# support ANY ANSI codes
#Hellanzb.DISABLE_ANSI = False


# Hostname for the XMLRPC client to connect to. By default, localhost
Hellanzb.XMLRPC_SERVER = 'localhost'

# IP address on which the XMLRPC Server will be binded to.
# Type '0.0.0.0' for any interfaces, '127.0.0.1' will disable remote access
Hellanzb.XMLRPC_SERVER_BIND = '0.0.0.0'

# Port number the XML RPC server will listen on, and the client will connect to.
# Set to 'None' (without the quotes!) for no XML RPC server
Hellanzb.XMLRPC_PORT = 8760

# Password for the XML RPC server. You might probably never use this, but the
# command line XML RPC calls do -- it should definitely be changed from its
# default value. The XML RPC username is hardcoded as 'hellanzb' -- E.g. URL:
# [http://hellanzb:changeme@localhost:8760](http://hellanzb:changeme@localhost:8760)
Hellanzb.XMLRPC_PASSWORD = '??????'


# Username/Password to [http://www.newzbin.com](http://www.newzbin.com) for automatic NZB downloading
Hellanzb.NEWZBIN_USERNAME = "??????"
Hellanzb.NEWZBIN_PASSWORD = "??????"


# If any of the following file types are missing from the archive and cannot be
# repaired, continue processing because they're unimportant (case insensitive)
Hellanzb.NOT_REQUIRED_FILE_TYPES = [ 'log', 'm3u', 'nfo', 'nzb', 'sfv', 'txt' ]

# Don't get rid of (move into the PROCESSED dir) the following file types when
# finished post processing (case insensitive)
#Hellanzb.KEEP_FILE_TYPES = [ 'log', 'm3u', 'nfo', 'nzb', 'sfv', 'txt' ]
Hellanzb.KEEP_FILE_TYPES = [ 'nfo', 'txt' ]


# List of alternative file extensions matched as NZB files in the QUEUE_DIR.
# The 'nzb' file extension is always matched
#Hellanzb.OTHER_NZB_FILE_TYPES = [ 'xml' ]

# Support extracting NZBs from ZIP files with this suffix (case insensitive) in
# QUEUE_DIR. Defaults to '.nzb.zip'. Set to False to disable.
#Hellanzb.NZB_ZIPS = '.nzb.zip'

# Support extracting NZBs from GZIP files with this suffix (case insensitive)
# in QUEUE_DIR. Defaults to '.nzb.gz'. Set to False to disable.
#Hellanzb.NZB_GZIPS = '.nzb.gz'

# Delay enqueueing new, recently modified NZB files added to the QUEUE_DIR until
# this many seconds have passed since the NZB's last modification time (defaults
# to 10 seconds)
#Hellanzb.NZBQUEUE_MDELAY = 10

# Optional external handler script. hellanzb will run this script after post
# processing an archive, with the following arguments:
#
# handler_script type archiveName destDir elapsedTime parMessage
#
# type: post processing result, either 'SUCCESS' or 'ERROR'
# archiveName: name of the archive, e.g. 'Usenet_Post5'
# destDir: where the archive ended up, e.g. '/ext2/usenet/Usenet_Post5'
# elapsedTime: a pretty string showing how long post processing took, e.g.
#              '10m 37s'
# parMessage: optional post processing message. e.g. '(No Pars)'
#Hellanzb.EXTERNAL_HANDLER_SCRIPT = '~/bin/post_hellanzb.sh'

---

### Post by TuxCrafter on 2008-05-02
> **pabloikba said:**
> r

Here is copy of conf file (I changed password & username only):



hehe, for next time please attached the file instead of including them in the post, this is better for the server, environment and our eyes.

yes i meant queue indeed the nzb files should be placed here:
/home/zack/Desktop/NZB/queue/

If this does not work please enable the logging and check the logging files, i suspect that the connection is not good or something like that... ( i have not tested the hardy version yet.. no time so far)

---

### Post by pabloikba on 2008-05-02
Thanks for your reply...I'm sorry about pasting the conf file instead of attaching it.

I changed the conf file to read:
Hellanzb.LOG_FILE = 'home/zack/Desktop/NZB/log'

That's the only change I made. I started hellanzb and then I dropped an nzb file into the queue directory. Nothing happened. No processing, no logfile, nothing.

I am brand new at linux/ubuntu and must be doing something wrong or not doing something I should be doing. I appreciate your help. Many thanks.

Pablo

PS The Terminal Window shows:

zack@zack-laptop:~$ hellanzb

hellanzb v0.13 (config = /etc/hellanzb.conf, C yenc module)
(giganews) Openng 20 connection...
hellanzb - Now monitoring queue...

When I ran the list command it showed this:

zack@zack-laptop:~$ hellanzb list
Unable to connect to XMLRPC server,
error: Connection was refused by other side: 111: Connection refused.
The hellanzb queue daemon @ [http://hellanzb:sn00ks@localhost:8760](http://hellanzb:sn00ks@localhost:8760) probably isn't running

---

### Post by pathetic on 2008-05-06
Maybe I am wrong, but I think the previous comment meant you should start by fixing this line from:
[FONT="Courier New"][INDENT]Hellanzb.PREFIX_DIR = 'home/zack/Desktop/NZB/'[/INDENT]
[/FONT]to
[FONT="Courier New"][INDENT]Hellanzb.PREFIX_DIR = '/home/zack/Desktop/NZB/'[/INDENT][/FONT]

---

### Post by robgue on 2008-05-06
if you use newzbin there is a firefox plugin that will load the nzb automatically as long as hellanzb is running.

---

