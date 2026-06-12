---
title: "How to configure Prozilla and/or Axel in Gutsy"
date: 2008-04-07
forum: General Help
---

### Post by sayak on 2008-04-07
Hi I am a newby.
I cant get **axel** and **prozilla** to work

I installed Axel from synaptic package manager and Prozilla from **red hat linux** rpm prozilla-1.3.7.4-1.i386.rpm using alien

while** wget** downloads from the links** axel** and **prozilla** fail to do so from the same links.............

I was trying to download ubuntu ultimate from
[http://home.paulschou.com/pub/ultimate/ultimate-edition-1.7.iso](http://home.paulschou.com/pub/ultimate/ultimate-edition-1.7.iso)

and here are the outputs I got

**[COLOR="Red"]WGET[/COLOR] **-

 wget -O ultimate.iso [http://home.paulschou.com/pub/ultimate/ultimate-edition-1.7.iso](http://home.paulschou.com/pub/ultimate/ultimate-edition-1.7.iso)
--01:38:30--  [http://home.paulschou.com/pub/ultimate/ultimate-edition-1.7.iso](http://home.paulschou.com/pub/ultimate/ultimate-edition-1.7.iso)
           => `ultimate.iso'
Connecting to 172.31.100.29:3128... connected.
Proxy request sent, awaiting response... 200 OK
Length: 2,10,92,61,824 (2.0G) [application/x-iso9660-image]

 0% [                                     ] 3,77,846       5.64K/s             

**[COLOR="Red"]AXEL[/COLOR]** -

sayak@Foxbat:~$ axel -o ultimate.iso [http://home.paulschou.com/pub/ultimate/ultimate-edition-1.7.iso](http://home.paulschou.com/pub/ultimate/ultimate-edition-1.7.iso)
Initializing download: [http://home.paulschou.com/pub/ultimate/ultimate-edition-1.7.iso](http://home.paulschou.com/pub/ultimate/ultimate-edition-1.7.iso)
Unable to connect to server home.paulschou.com:80

[COLOR="Red"]
**PROZILLA**[/COLOR] -

sayak@Foxbat:~$ proz  [http://home.paulschou.com/pub/ultimate/ultimate-edition-1.7.iso](http://home.paulschou.com/pub/ultimate/ultimate-edition-1.7.iso)

Error connecting to home.paulschou.com

Unable to resolve home.paulschou.com

Press any key to exit..

My **[COLOR="Purple"] /etc/axelrc[/COLOR]** file is -

############################################################################
##                                                                        ##
##   Example configuration file for Axel - A light download accelerator   ##
##                                                                        ##
############################################################################

# reconnect_delay sets the number of seconds before trying again to build
# a new connection to the server.
#
# reconnect_delay = 20

# You can set a maximum speed (bytes per second) here, Axel will try to be
# at most 5% faster or 5% slower.
#
# max_speed = 0

# You can set the maximum number of connections Axel will try to set up
# here. There's a value precompiled in the program too, setting this too
# high requires recompilation. PLEASE respect FTP server operators and other
# users: Don't set this one too high!!! 4 is enough in most cases.
#
# num_connections = 4

# If no data comes from a connection for this number of seconds, abort (and
# resume) the connection.
#
# connection_timeout = 45

# Set proxies. no_proxy is a comma-separated list of domains which are
# local, axel won't use any proxy for them. You don't have to specify full
# hostnames there.
#
# Note: If the HTTP_PROXY environment variable is set correctly already,
# you don't have to set it again here. The setting should be in the same
# format as the HTTP_PROXY var, like 'http://host.domain.com:8080/',
# although a string like 'host.domain.com:8080' should work too..
#
# Sometimes HTTP proxies support FTP downloads too, so the proxy you
# configure here will be used for FTP downloads too.
#
# If you have to use a SOCKS server for some reason, the program should
# work perfectly through socksify without even knowing about that server.
# I haven't tried it myself, so I would love to hear from you about the
# results.
#
# http_proxy = 
# no_proxy = 

# Keep CGI arguments in the local filename?
#
# strip_cgi_parameters = 1

# When downloading a HTTP directory/index page, (like [http://localhost/~me/](http://localhost/~me/))
# what local filename do we have to store it in?
#
# default_filename = default

# Save state every x seconds. Set this to 0 to disable state saving during
# download. State files will always be saved when the program terminates
# (unless the download is finished, of course) so this is only useful to
# protect yourself against sudden system crashes.
#
# save_state_interval = 10

# Buffer size: Maximum amount of bytes to read from a connection. One single
# buffer is used for all the connections (no separate per-connection buffer).
# A smaller buffer might improve the accuracy of the speed limiter, but a
# larger buffer is a better choice for fast connections.
#
# buffer_size = 5120

# By default some status messages about the download are printed. You can
# disable this by setting this one to zero.
#
# verbose = 1

# FTP searcher
#
# search_timeout - Maximum time (seconds) to wait for a speed test
# search_threads - Maximum number of speed tests at once
# search_amount  - Number of URL's to request from filesearching.com
# search_top     - Number of different URL's to use for download
#
# search_timeout = 10
# search_threads = 3
# search_amount = 15
# search_top = 3

# If you have multiple interfaces to the Internet, you can make Axel use all
# of them by listing them here (interface name or IP address). If one of the
# interfaces is faster than the other(s), you can list it more than once and
# it will be used more often.
#
# This option is blank by default, which means Axel uses the first match in
# the routing table.
#
# interfaces = 

# If you don't like the wget-alike interface, you can set this to 1 to get
# a scp-alike interface.
#
# alternate_output = 1






The **[COLOR="Purple"]/ect/prozilla.conf[/COLOR]** is-

# Prozilla rc file.
# Any line beginning w/ a "#" is a comment
# Empty lines are ignored

# This will generate a file named debug.log
# If you want to report a bug please also send the file debug.log.
#
#debug=off

# How many connections prozilla will make.
# This greatly depends on your bandwidth.
# Recommended values:
# 33k: dunno, tell us what you find to be the best
# 56-64k: dunno, tell us what you find to be the best
# Cable: dunno, tell us what you find to be the best
# DSL: dunno, tell us what you find to be the best
# Subspatial Transmissions: dunno, tell us if you have this ;)
# 
threads = 4

# How many servers will we ping at once
# Recommended values...
# 
pingatonce = 5 


# Wait 2*n seconds for a server response (default 2*4)
pingtimeout = 4

# The next option is a very nice thing. Just set it on ;)
# BTW, it's still under test. If you find bugs please report
# them at <prozilla@genesys.ro>
# 
# Patches are greatly appreciated.
ftpsearch = on

#The next line spcifies the server to use for the ftpsearch
# lycos changed it from ftpsearch.lycos com to the following 
#
# ftpsearchurl = [http://download.lycos.com/swadv/AdvResults.asp](http://download.lycos.com/swadv/AdvResults.asp) 
ftpsearchurl = [http://download.softpedia.ro:80](http://download.softpedia.ro:80)
# ftpsearchurl = [http://ftpsearch.uniovi.es:8000/ftpsearch](http://ftpsearch.uniovi.es:8000/ftpsearch)

# How many mirrors we will request from ftpsearch.
# This option only make sense w/ ftpsearch ON
#
mirrors = 40

# The timeout period
# How long do we wait when there is no response before starting again
#
#timeout = 180

# How many attempts do we make when we encounter a data transmission error
# to get the file in (default is 200), specify 0 to try infinitely  
#
tries = 200

#The timedelay between retries. (default 15 seconds)
#
retrydelay = 10

# The force option, off by default. When enabled cause Prozilla NOT
# to prompt the user about overwriting existent files etc..
# 
#forcemode = off

# Maximum redirections allowed
# 
maxredirs = 100

# Use ~/.netrc? On by default
# 
#netrc = on

# Uses PASV by default. If you don't like it set it OFF and will use PORT instead.
# 
pasv = on

# If you turn this option ON, when an error occurs, ProZilla will print the
# error to stdout and quit instead of waiting for the user to press a key to
# exit
# 
#nogetch = ON

#The maxbps option can be used to limit the bandwith consumption of
# prozilla for example maxbps = 40000 will limit it to consume a maximum of
# 40k of bandwith, the default is 0 which means unlimited bandwith
# consumption (ie no limitation just get as fast as possible)
#
#maxbps = 0


#mainoutputdir
#This specifies to which directory the output file will be built
#mainoutputdir = /home/weasel/downloads
#Now if you download a file called gcc-2.95.2.tar.bz2 it will be saved as 
#/home/weasel/downloads/gcc-2.95.2.tar.bz2
#
#mainoutputdir = .



Can any one please help me to get axel and/or prozilla working ??

Thanking you in advance

---

### Post by user@righthere on 2008-04-17
Do you use a proxy? If so, edit 

# http_proxy = 

to

http_proxy =  [http://host.domain.com:port/](http://host.domain.com:port/)

e.g. http_proxy = [http://127.0.0.1:5865/](http://127.0.0.1:5865/)

That should solve the axel issue. I don't see a similar line in the prozilla.conf so I dunno about that one.

---

### Post by myth1001 on 2008-05-31
if my proxy is 192.168.1.1:8080

am i supposed to key in

http_proxy = [http://192.168.1.1:8080/](http://192.168.1.1:8080/)


??

---

