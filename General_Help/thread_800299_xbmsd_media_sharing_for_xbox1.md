---
title: "xbmsd media sharing for xbox1"
date: 2008-05-19
forum: General Help
---

### Post by Voorhees1979 on 2008-05-19
Hi there

I have started to use my xbox1 with xbmc for media instead of my xbox360. I stumbled across xbmsd and it works really well. But I have one slight problem. I can only share one location.

I have my ripped movies on /media/Archive/Media/
My TV eps are on /media/disk/TV/

So two different drives. I can share my Movies folder no worries, but cant find out how to share two folders at the same time. I will paste the conf file below. 

To get around this for the time being I am also running Ushare which shares my TV at the same time as xbmsd shares my movies, they work well together. For some reason Ushare wont fast forward on the xbox1 but fast forwards fine on my xbox360.

Thanks to anyone who can help me :)

# Example xbmsd configuration file. Note: if xbmsd is installed
# system-wide you should NOT specify a PID file here as it is
# specified in the system init script.



# The root directory of the server. This MUST be specified, otherwise
# the daemon won't start.
#
#root /var/empty
root /media/Archive/Media


# The MAP command maps a file (relative to server root) to any file in
# the filesystem or to a HTTP stream. All path components must exist
# as real or mapped; you can map them to empty directories if needed,
# as in the example below (note: not all systems have /var/empty).
#
#map movies /var/empty
#map movies/movie1.avi /tmp/foo.avi
#map movies/movie2.mpg [http://localhost/movies/bar.mpg](http://localhost/movies/bar.mpg)

# The CONF command generates "synthetic" mplayer configuration file
# for files ending int the specified file extension. That is, if
# <file>.conf does not exists as real or mapped, it is mapped to the
# specified file. This example maps all MPEG transport streams (*.ts,
# used e.g. for DVB streams) to have a deinterlacing mplayer
# configuration file (should contain e.g. linear blend deinterlacing:
# "vf-pre=pp=lb").
#
#map ts /etc/xbmsd/deinterlace.conf


# The FILTER command specifies that files with the given extensions
# should be given as the first argument to the given program and the
# program output (stdout) is sent as the file contents. An absolute
# path for the program specifies a global filter, a relative path a
# directory-specific one. This example just makes all AVI and Matroska
# files to be streams.
#
#filter avi,mkv /bin/cat

# Set this to no if you want filtered files to show as streams (size
# of streams is zero) also in directory listings. The default is yes,
# which means that filtered files show just like the originals in
# directory listings.
#
#stealth_filters no


# The address the server will listen on. Defaults to all local
# addresses. This is name-resolved, so it need not be numeric but
# should be to avoid misconfiguration.
#
#listen localhost

# The network interface the server will listen on. Only available on
# Linux systems.
#iface eth0

# Specify an alternative TCP port to listen. Defaults to 1400.
#
#port 11400

# Specify an alternate UDP port for the server discovery
# protocol. Defaults to 1400. Set to 0 to disable server discovery.
#
#discovery_port 0

# This is the server description sent in server discovery
# packets. Default is the hostname of the system.
#
#hostname



# When reading a file, this is how often (in kilobytes) the file size
# will be checked for changes. This is necessary if you are reading a
# file that is being downloaded i.e. its size is growing. By default
# the size is checked for every read megabyte (1024), which should be
# good enough for most purposes.
#
#stat_interval 1024

# Set this to yes if seeking a stream should return success even
# though the seek is not done. By default trying to seek a stream
# returns an error.
#
#seek_streams yes



# The user and group that xbmsd should run as. Only applicable if
# started as root. The default user is nobody, and the default group
# is the default group of the user. The example below runs as user
# nobody and group users.
#
#user nobody
#user users

# Set the global password. If set, the server requires authentication
# and ANY user can authenticate with this password.
#
#password "Let me in, please."

# Specify the password file. If specified, the server will require
# authentication and reads the user names and password from this
# file. See the man page for details.
#
#password_file /etc/xbmsd/xbmsd.passwd

---

### Post by xboxbman on 2008-05-23
i've had the same problem for some time and haven't been able to find a solution.

---

### Post by avel on 2008-05-24
Isn't "Xbox Media Streaming Protocol (XBMSP)" deprecated according to XBMC developers themselves?

You should have no problem sharing files via SMB/CIFS (samba). That's the way I have personally set it up. Is there any praticular reason to avoid SMB?

---

### Post by Zorael on 2008-05-24
> **avel said:**
> Isn't "Xbox Media Streaming Protocol (XBMSP)" deprecated according to XBMC developers themselves?

You should have no problem sharing files via SMB/CIFS (samba). That's the way I have personally set it up. Is there any praticular reason to avoid SMB?

When sharing over Internet, I'd say. I had a box set up elsewhere (250km away) with huge storage and ftp/radmin access, and getting SMB to work would either mean opening up the SMB ports to the interblag, or setting up a VPN. Awfully slow compared to just using ccx.

---

### Post by Voorhees1979 on 2008-05-26
Hi

For some reason I cannot get the xbox to see samba shares.

---

