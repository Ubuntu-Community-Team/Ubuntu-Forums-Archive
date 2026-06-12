---
title: "Telnet Server not starting"
date: 2014-03-26
forum: General Help
---

### Post by Alan_Killian on 2014-03-26
hello,
I am installing Ubuntu Server 13.10 and cant get telnet working on the server. I have installed both xinet.d & telnetd thru apt-get and restarted xinetd but nothing is started when I do a netstat -l.
In googling trouble I see mention of adding **telnet stream tcp wait telnetd /usr/sbin/tcpd /usr/sbin/in.telnetd** line to /etc/inetd.conf. I have no inetd.conf. I see that inetd has been depracated and I put the line in xinetd.conf and restarted xinetd service but still no telnet listening. Can someone advise me on what the proper settings for the telnet server and  what files they should be in. Here is the contents of my xinetd.conf file:

# Simple configuration file for xinetd
#
# Some defaults, and include /etc/xinetd.d/

defaults
{

# Please note that you need a log_type line to be able to use log_on_success
# and log_on_failure. The default is the following :
# log_type = SYSLOG daemon info

}

includedir /etc/xinetd.d

#:STANDARD: These are standard services.
telnet		stream	tcp	nowait	telnetd	/usr/sbin/tcpd	/usr/sbin/in.telnetd



Thanks

---

### Post by Alan_Killian on 2014-03-27
For anyone interested here is the link I found to get my Telnetd working on Ubuntu Server 13.10:
[http://ubuntuguide.net/install-and-enable-telnet-server-in-ubuntu-linux](http://ubuntuguide.net/install-and-enable-telnet-server-in-ubuntu-linux)

---

