---
title: "Someone Please Help Me With Zussaweb"
date: 2007-10-09
forum: General Help
---

### Post by cchester on 2007-10-09
Hi,

Could someone please help me with the issue I am having in getting Zussaweb to work with my Hellanzb?

I have Hellanzb working and it is fine does what it is supposed to do. For the life of me I can't seem to get it and Zussaweb to work with each other. I would love to get this working so that I have a GUI for Hellanzb. So please help me out.

Do I need a php server running to make this work? The files are PHP.

If so what do I need to do?

I think I am misunderstanding how to setup up both config files I guess and then what exactly to type into Firefox.

Here is my Hellanzb.conf Please let me know if I have anything wrong and what I need to change if anything:

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
Hellanzb.LOG_FILE = os.path.expanduser('~') + '/.hellanzb/log'

# Uncomment this line to log DEBUG messages to the specified file
#Hellanzb.DEBUG_MODE = os.path.expanduser('~') + '/.hellanzb/log-debug'

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
defineServer(id = 'changeme',
             hosts = [ 'news.giganews.com:119' ],
             #hosts = [ 'news.changeme.com', 'morenews.changeme.com:8000' ],


             username = '*********',
             password = '*******',
             #username = None,           # no auth
             #password = None,

             connections = 10,
             antiIdle = 4.5 * 60,        # 4 minutes, 30 seconds, 0 to disable
             #bindTo = '204.31.33.7',    # connect FROM this ip address
             #enabled = False,           # disable this server
             #skipGroupCmd = False,      # skip sending nntp GROUP commands
             #fillserver = 0,            # defaults to 0 (a main server).
                                         # fillservers must have values > 0
                                         # (priority)
             ssl = False
             )

# Uncomment this line to limit all server connections to the specified KB/s
# bandwidth
#Hellanzb.MAX_RATE = 150 # limit to 150kB/s


# Important locations
Hellanzb.PREFIX_DIR = os.path.expanduser('~') + '/home/chris/'

# Where to put queued .nzb files
Hellanzb.QUEUE_DIR = Hellanzb.PREFIX_DIR + 'nzb/daemon.queue/'

# Where the fully processed archives go
Hellanzb.DEST_DIR = Hellanzb.PREFIX_DIR + 'done/'

# The .nzb currently being downloaded is stored here
Hellanzb.CURRENT_DIR = Hellanzb.PREFIX_DIR + 'nzb/daemon.current/'

# The archive currently being downloaded is stored here
Hellanzb.WORKING_DIR = Hellanzb.PREFIX_DIR + 'nzb/daemon.working/'

# Archives interrupted in the middle of downloading are stored here temporarily
Hellanzb.POSTPONED_DIR = Hellanzb.PREFIX_DIR + 'nzb/daemon.postponed/'

# Archives currently being processed. May contains archive directories, or
# symbolic links to archive directories
Hellanzb.PROCESSING_DIR = Hellanzb.PREFIX_DIR + 'nzb/daemon.processing/'

# Temp storage
Hellanzb.TEMP_DIR = Hellanzb.PREFIX_DIR + 'nzb/daemon.temp/'

# Filename to store hellanzb state in between CTRL-Cs. The state (includes the
# order of the queue, and smart par recovery information) is intermittently
# written out as XML to this file
Hellanzb.STATE_XML_FILE = Hellanzb.PREFIX_DIR + 'nzb/hellanzbState.xml'


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
Hellanzb.SMART_PAR = True

# Supply a path to the (un)rar command
#Hellanzb.UNRAR_CMD = None

# Supply a path to the par2 command
Hellanzb.PAR2_CMD = '/usr/bin/par2'

# Skip unraring during post processing
Hellanzb.SKIP_UNRAR = False

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
Hellanzb.XMLRPC_SERVER_BIND = '127.0.0.1'

# Port number the XML RPC server will listen on, and the client will connect to.
# Set to 'None' (without the quotes!) for no XML RPC server
Hellanzb.XMLRPC_PORT = 8760

# Password for the XML RPC server. You might probably never use this, but the
# command line XML RPC calls do -- it should definitely be changed from its
# default value. The XML RPC username is hardcoded as 'hellanzb' -- E.g. URL:
# [http://hellanzb:changeme@localhost:8760](http://hellanzb:changeme@localhost:8760)
Hellanzb.XMLRPC_PASSWORD = 'changeme'


# Username/Password to [http://www.newzbin.com](http://www.newzbin.com) for automatic NZB downloading
Hellanzb.NEWZBIN_USERNAME = None
Hellanzb.NEWZBIN_PASSWORD = None


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



I blocked out my username and pass.

Ok here is my Zussaweb file as said before please let me know if anything is wrong or if I need to add anything I am new to this:

<?php

$host = 'localhost';
$port = 8760;
$user = 'hellanzb';
$passwd = 'changeme';
// Download settings
$download_max_filesize = 3000000;
$downloaded_allowed_types = array(
    "application/x-gzip-compressed"     => ".tar.gz, .tgz",
    "application/x-zip-compressed"         => ".zip",
    "application/x-tar"            => ".tar",
    "text/plain"                => ".html, .php, .txt, .inc (etc)",
    "text/xml"                => ".nzb",
    "image/bmp"                 => ".bmp, .ico",
    "image/gif"                 => ".gif",
    "image/pjpeg"                => ".jpg, .jpeg",
    "image/jpeg"                => ".jpg, .jpeg",
    "application/x-shockwave-flash"     => ".swf",
    "application/msword"            => ".doc",
    "application/vnd.ms-excel"        => ".xls",
    "application/octet-stream"        => ".exe, .fla (etc)"
); # these are only a few examples, you can add as many as you like
$download_nzb_path = '/mnt/video/nzb/daemon.queue';
define ("disk", "/mnt/video/incoming/");
?>

I left host port and user alone because they matched Hellanzb.

So does anyone have any ideas? I have hellanzb running in a terminal and typed [http://127.0.0.1:8760](http://127.0.0.1:8760) in and then my username and pass and I get a blank page. So is that right or wrong?

I am totaly lost and can't seem to get this to work. Please can someone help that has hellanzb working and Zussaweb working together. Thanks.

---

### Post by Jake9999 on 2008-07-06
You forgot to install apache and php.

Here's a guide to help you: [http://www.jamiedumbill.com/index.php?page=41](http://www.jamiedumbill.com/index.php?page=41)

---

