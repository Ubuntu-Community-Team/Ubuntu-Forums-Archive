---
title: "Need help getting XMMS -&gt; icecast relay working"
date: 2007-04-11
forum: General Help
---

### Post by oldweasel on 2007-04-11
Is there a guide anywhere that can help me get a XMMS -> icecast relay working? I can get Icecast running, and also get XMMS running with the liveice plugin, but I get all sorts of errors when xmms tries to connect to icecast. 

i also get a 403 eror when trying to connect to the icecast webpage admin interface.

Does anyone know where I might be able to get information on getting these working?

EDIT:

Here is the icecast log error message I recieve when trying to access the web interface: No mountfile found, refusing access to WWW admin
Also, I recieve the following message when XMMS tries to send a feed to the icecast server: 
[11/Apr/2007:10:38:06] Kicking unknown 4 [localhost] [Stupid headers], connected for 0 second

Here is my icecast config file:
```

# This be a comment, I like comments.
# To use this file, copy it to etc/icecast.conf in the icecast base directory

################################################################################
# I suggest you read this file carefully, and don't do anything silly
# cause the configuration file parser is pretty lame.
# If not stated otherwize, you can change these while the server is 
# running (through the admin console). Or by changing this file
# and using the rehash command (or (if supported) sending SIGHUP)
# Please use the admin console though, cause that's what its there for :)
################################################################################

############### Server Location and Resposible Person ##########################
# Server meta info, please fill out these.  
# They get displayed when listing directories, streams, and 
# if the client supports it, among the other stream headers.
# You can put anything here, it's just for show.
###############

location Just west of Mars
rp_email kirk@enterprise.space
server_url http://www.icecast.org/

########################### Server Limits ######################################
# These describe the maximum number of simultaneous connections allowed.
# When reached, the server will refuse access.
# There is a builtin bandwidth measuring tool inside the icecast server,
# and when icecast thinks that it is using more than "throttle" MB/s, then
# no clients or sources will be allowed until the bandwidth usage goes back
# down below the limit. Use this with caution, since the bandwidth measurement
# is in no way an exact science.
###########################

max_clients 5
max_clients_per_source 5
max_sources 5
max_admins 5
throttle 10.0

########################## Stream Meta Data ####################################
# This is a experimental feature, at best. 
# When it does not work, it will put the whole stream out of synk on the client
# side, and you will get a big mess.
# use_meta_data controls whether this icecast server will use title streaming at
# 	        all. It's turned off by default, cause it creates chirps in the
#               stream if you're not careful.
# streamtitletemplate is a the template for creating the title that gets sent to
#                     the client and the directory server. %s will be
#		      substituted for the actual filename.
# streamurl is the default url for each stream.
# nametemplate is a template for the name of each stream.
# desctemplate is a template for the description of each stream.
##########################
use_meta_data 0
streamurllock 0
streamtitletemplate %s
streamurl http://yp.icecast.org
nametemplate %s
desctemplate %s


######################## Mountpoint fallback ###################################
# By default, if a user requests a stream that is not found, this user will be
# given the default stream instead. The default stream is per default the oldest
# stream on the server, but this can be changed with the priority value in the
# 'modify' command. 
# If you don't want the user to get the default mount, but instead a
# HTTP 404 Stream Not Found, then set this to 0
########################

mount_fallback 1

######################### Server passwords #####################################
# icecast for Debian has been compiled with crypt support.
# Thus, you have to create a crypted version of the password. 
# You can generate encrypted passwords with makepasswd.
# Please *change* default password before using it.
#########################

encoder_password noTEC0b1puiy2  #hackme
admin_password   noTEC0b1puiy2  #hackme
oper_password    noTEC0b1puiy2  #hackme


######################## Directory servers #####################################
# A directory server is a "meta-server" where you, for free, can list
# your own icecast server. This is a great way of getting more listeners.
# The touch_freq is how often to "update" the directory server with information
# from your server. (e.g number of listeners, stream info, etc..)
########################

#icydir yp.shoutcast.com
#icydir yp.breakfree.com
#icydir yp.musicseek.net
#icydir yp.van-pelt.com
#icydir yp.radiostation.de
#directory yp.icecast.org
#directory yp.mp3.de
touch_freq 5

############# Server IP/port configuration (IMPORTANT) #########################
# If no hostname is specified, icecast will listen on all available interfaces,
# i.e INADDR_ANY. This is probably what you want.
# If you want icecast to _only_ listen on a specified ip, then change the 
# "hostname" parameter. The "port" parameter is rather self-explanatory. 
# As of icecast 1.3, all connections use port 8000. Admins, encoders, clients, 
# the whole thing. So no more messing with 3 different ports in the firewall 
# rules.
# The server_name can currently ONLY be specified here, and ONLY when you start
# the server. Changing it later on will not have the desired effect.
# The server_name specifies the hostname of the server, don't set it to an ip, 
# and don't even THINK about setting it to a hostname not pointing to your ip.
# - WARNING - WARNING - WARNING - (important, get it?)
# It is VERY important that this server_name does actually resolv to the ip you
# are running your server at. If not, BAD THINGS<tm> will happen.
# E.g localhost is definately probably not what you want :)
# Using your ip will probably work.. but it will look nicer with your hostname.
# The problem is that if you specify something that doesn't resolve to yourself,
# then virtual host support will get fscked up, and default server action
# might not work either.
# Also, changing the port here will not affect the server when doing a 'rehash'
# since binding to a port is done only once, when the server is started.
# server is started.
# Users on dialup connections with dynamic ip:s are in trouble here, I know.
# You will just have to live without the virtual hosts support, cause there is
# no portable way of getting all the ip:s the process is binding to. Either
# edit this file before starting icecast and fill in the current ip, or just
# live with it. Setting the value to "dynamic", will tell the icecast server
# that there is no reliable hostname for this machine.
#
# you can now use multiple ports.  the default port is the first one defined.
# define PORT, and PORT+1 for shoutcast compatibility.
#############

hostname 127.0.0.1

port 9003
port 9004

server_name localhost.localdomain

####################### Directory server options ##############################
# You can now force the directory server to use the server_name value instead
# of the originating ip. For most people this is unnecessary, since it is the
# same. But for people behind proxies, this should be very useful.
# Set it to 1 if you want to force use of the server_name variable.
#######################

force_servername 0

######################## Main Server Logfile ##################################
# This is the file where icecast prints all the information about
# connections, warnings, errors, etc...
# You cannot change this in the admin console, but changing it here
# and then rehashing the server will work.
# logfiledebuglevel is the debugging level for all output to the main logfile.
# consoledebuglevel is the debugging level to the icecast console.
# accessfile is the file where all connects/disconnects goes
# usagefile is a file for periodic bandwidth and usage information goes
########################

logfile icecast.log
accessfile access.log
usagefile usage.log
logfiledebuglevel 0
consoledebuglevel 0

########################## Reverse Lookups ####################################
# Set this to 1 if you want ip:s to be looked up (using reverse lookup)
# or 0 if you just want the ip:s (which is slightly faster)
##########################

reverse_lookups 1

############################ Console mode #####################################
# Use 0 if you want stdin to become a local admin console with log tailing
# Use 1 if you want stdin to become a local admin console
# Use 2 if you just want the console to become a log window
# Use 3 if you want the icecast server to be launched in the background (not available for Win32)
############################

console_mode 0

########################### Client Timeout ####################################
# (How to deal with clients when no encoder is connected)
# A negative value means keep them forever
# 0 (zero) means kick them out instantly
# X > 0 means keep them X seconds
###########################

client_timeout -1

######################### Kicking clients #####################################
# If set to 1, then clients whose source has disconnected will
# be kicked. If set to 0, they will simply be moved to another
# stream. This only has an effect if client_timeout is <= 0.
#########################

kick_clients 0

###################### Static file directory ##################################
# This enables the http-server file streaming support in icecast.
# If you don't want to go through the trouble of setting up apache
# or roxen or whatever, then you can just specify a directory here,
# and then http://your_server:port/file/file.mp3 will be equivalent
# to /staticdir/file.mp3
# The http server support is of course very limited, don't try to 
# do anything fancy. Also, only .mp3 files will be displayed.
######################

#staticdir c:\windows\desktop
staticdir /usr/share/icecast/static

############################# Templates ######################################
# the icecast server uses templtes to format output for list.cgi and
# various errors.  you can specify the directory that these are read from
# please use absolute paths if possible
#############################

templatedir /usr/share/icecast/templates

############################# Statistics ######################################
# The icecast server dumps statistics to a file on a regular basis.
# You can specify how often (stats_time), and to what file (stats_log)
# StatsTime (how often to dump stats, in seconds)
# 0 (zero) means to not dump stats
# X > 0 means dump stats every X seconds to the file specified by stats_log
#############################

logdir /var/log/icecast
stats_log stats.log
statshtml_log stats.html
stats_time 60

############# Aliases (including virtual host support) ########################
# In icecast servers prior to the 1.3 release, you could run a icecast
# server as a relay for another icecast server, simply acting as a 
# client on the other server and serving the local clients. This was
# of course a neat way of increasing the number of possible listeners
# for your broadcast. You could build a tree-like structure of relays
# and broadcast to 1000 listeners without problem with the originating
# stream on a cable modem or whatever.
# In icecast 1.3.0 and above, we make this procedure much simpler.
# If you want to relay a stream from another server, simply add an 
# alias for that server. Say you want to relay the broadcast originating
# from my machine (laika.linux.tm:8000/laika), on your machine, do this:
# alias laika http://laika.linux.tm:8000/laika
# What happens is that when a listeners connects to your server and
# requests the /laika stream, then your icecast server will connect
# as a client to my machine, and then feed my stream to the listener.
# All subsequent requests for /laika will use the same feed (i.e only
# one connect will be made to my machine). Icecast will automagically
# shut the link from my machine down when no one is listening. I.e
# no bandwidth will be wasted.
# The old functionality (i.e adding a more or less static relay) is still
# there, but you have to do it from the admin console. Just do
# relay pull http://laika.linux.tm:8000, and that will be accessible as
# http://your_machine:port/laika.linux.tm:8000/ (you can change this with
# the -m option to relay pull.
# There is also a possibity to do it the other way around, starting at
# the originating server. Just do "relay push <source_id> host:port", and
# your stream will be relayed to the remote server.
# In theory, this should enable virtual host support, cause you can
# specify an alias like so:
# alias http://virtual.host.com:port/whatever /something
# This will make all requests to virtual.host.com:port/whatever use the
# stream /something. This is not really thorougly tested, but it should
# work if your server_name is correctly set, and the client is sending
# the valid Host: <host:port> http header.
#############

#alias radiofri http://195.7.65.207:6903 

############################ Kick Relays ######################################
# How long to keep aliased sources when no clients are left listening to it.
############################
kick_relays 0

############################ Transparent proxy ################################
# This is somewhat equivalent to making _all_ request to aliased sources. So
# instead of adding an alias for all streams in the world, turn on the
# transparent proxy support. Using this on a server that has streams of it's
# own can be quite tricky, and then, as usual it is _very_ important that
# the server_name is correct. 
# Most mp3 playing clients have support for a http proxy 
# (afaik x11amp and winamp do, anyway). If listeners set your machine as this
# proxy, and you turn on transparent_proxy, then when a client requests
# http://whatever.com:port/whatever, then your icecast server will connect
# to whatever.com and feed the whatever-stream to the client. All subsequent
# request for this stream will use the same feed, just as if it was an alias.
# When running icecast with your own broadcasts, then you should turn this off,
# or anyone can bring your network down with a lot of relaying connects.
# Don't turn this on if you don't have a server_name set
############################
transparent_proxy 0

acl_policy 1
#deny all *
#allow all *.ryd.student.liu.se

```

---

### Post by tux821 on 2007-05-26
I had the same problem, this icecast-server package is old and depreciated and hard to make work.
If it is possible for you please try the new 'icecast2' with ices2. 
There is some effort to make this great xmms-liveice plugin working but it's not there yet.., see:

[http://liveice.sourceforge.net/](http://liveice.sourceforge.net/)

Ok then. As an experiment I wanted to figure out how to stream with xmms + xmms-liveice plugin from my workstation to my KISS DP558 player with stage2 firmware. 
I could not get it to work with icecast2 so I was stuck to try it with the old icecast-server package. 
It took some hard work, but I managed to get it working.

_The configuration files_
In the /etc/icecast/ directory you find the icecast-server configuration files all with extension .dist.
Copy (or move) all those files -without- this extension to activate them (you need to be root for this or use sudo):

# cp /etc/icecast/icecast.conf.dist    /etc/icecast/icecast.conf

Do the same for the other files.

_The access control horror_
So you think you got it set up and now you can't get access to your icecast admin webpage.

For my workstation at internal IP 192.168.2.5 I did two things to make this work:

1) /etc/icecast/icecast.conf 
Lookup server_name part and edit as needed, note for this example I used my local workstation IP:

#hostname disabled
port 8000
port 8001
server_name 192.168.2.5

2) /etc/hosts.allow
Here I enabled access to the icecast 8000 port for my workstation (127.0.0.1) and my local network '192.168.2.*':

8000: 127.0.0.1 LOCAL : ALLOW
8000: 192.168.2.

Now restart your icecast server and try to access your admin page:
# /etc/init.d/icecast-server restart

and point your webbrowser to: 
[http://127.0.0.1:8000/admin](http://127.0.0.1:8000/admin)

_streaming.. encrypted passwords sooo easy_
Well if you know it -then- its easy the big amount of text in the configuration file 'etc/icecast/icecast.conf'
is confusing.
Look up the 'Server passwords' part in the '/etc/icecast/icecast.conf' file.
This is what I used for my local experiment to get xmms-liveice to be able to connect to the icecast server:

# tGTqNUb YXjIENHpFiRV2
encoder_password YXjIENHpFiRV2
admin_password   YXjIENHpFiRV2
oper_password    YXjIENHpFiRV2

How does this work ?

*) Most important REMOVE ALL CHARACTER AFTER THE PASSWORD, ALSO THE COMMENTS, EVERYTHING!! 

The plaintext password in this example is 'tGTqNUb'.
This is the password which I did put in the xmms-liveice plugin. 
The 'YXjIENHpFiRV2' part is the crypted password set for all icecast access.
Again.. do not put any character behind this password, no comments, nothing or it will not work.
You can generate your own password with:
makepasswd -crypt
This will output a random password followed by the encrypted password.
Note: the default password 'hackme' also work donno,  but only if you remove the -complete- '  # hackme' comment part.

Again restart your icecast-server, see command above.

_xmms-liveice plugin settings_
So at this stage you should have access to your icecast admin page and have an encrypted passwords setup :P
Now the last part, the xmms-liveice plugin.
For me xmms did crash many times before I did figure this out.

This is what I think made it work:
1) Audio format tab
Be sure to fill in the 'Executable name:' field for lame e.g. /usr/bin/lame
(or where you did install lame)
2) Server tab
For my experiment I used:
Server address: 127.0.0.1
Server port: 8000
Encoder Password: tGTqNUb
check the 'Use x-Audiocast Headers checkbox
Fill in a Stream Mountpoint e.g.: /mystream.mp3

Ok now apply your settings and enable the plugin.
Start playing a playlist and check if you see your stream appear on the icecast admin page:
[http://127.0.0.1:8000/admin?mode=sources](http://127.0.0.1:8000/admin?mode=sources)

Note if the stream is there you should be able to connect to it (finally ;)
For my experiment I pointed a webbrowser on another Linux box on my network to:

[http://192.168.2.5:8000/mystream.mp3](http://192.168.2.5:8000/mystream.mp3)

This should do it :P
If not follow this checklist again, reboot your icecast-server at every stage and analyse its logfile.
// Ah I remember 1 last thing I have a firewall running on my box (192.168.2.5), so I had to enable access to port '8000' for my local network.

---

### Post by Jose Catre-Vandis on 2007-06-03
Many thanks tux821, your great howto got me icecasting first time around :D

---

### Post by tux821 on 2007-06-09
> **Jose Catre-Vandis said:**
> Many thanks tux821, your great howto got me icecasting first time around :DThanx for the feedback, enjoy your icecast station ;)

---

