---
title: "Stunnel4/Pan issue"
date: 2007-03-30
forum: General Help
---

### Post by ephman on 2007-03-30
hi,

i'm trying to trouble shoot a problem with a newsreader called pan
that i might be having.  i left this posting on the stunnel mailing list but no aswers.
 here's my setup:

ubuntu 6.10 kernel 2.6.17
pan 0.14.2
stunnel4 4.150

i created a snntp.conf file with only:
client = yes
foreground = yes
debug = 7

[nntps]
accept = localhost:2000
connect = inetnews.worldnet.att.net:563

then i run stunnel4 and this is the output:
ephman at wintermute:~$ sudo stunnel4 /etc/stunnel/snntp.conf
2007.03.29 13:54:47 LOG7[13414:3083015856]: RAND_status claims
sufficient entropy for the PRNG
2007.03.29 13:54:47 LOG6[13414:3083015856]: PRNG seeded successfully
2007.03.29 13:54:47 LOG7[13414:3083015856]: SSL context initialized
for service nntps
2007.03.29 13:54:47 LOG5[13414:3083015856]: stunnel 4.15 on
i486-pc-linux-gnu with OpenSSL 0.9.8b 04 May 2006
2007.03.29 13:54:47 LOG5[13414:3083015856]: Threading:PTHREAD
SSL:ENGINE Sockets:POLL,IPv6 Auth:LIBWRAP
2007.03.29 13:54:47 LOG6[13414:3083015856]: file ulimit = 1024 (can be
changed with 'ulimit -n')
2007.03.29 13:54:47 LOG6[13414:3083015856]: poll() used - no
FD_SETSIZE limit for file descriptors
2007.03.29 13:54:47 LOG5[13414:3083015856]: 500 clients allowed
2007.03.29 13:54:47 LOG7[13414:3083015856]: FD 3 in non-blocking mode
2007.03.29 13:54:47 LOG7[13414:3083015856]: FD 4 in non-blocking mode
2007.03.29 13:54:47 LOG7[13414:3083015856]: FD 5 in non-blocking mode
2007.03.29 13:54:47 LOG7[13414:3083015856]: SO_REUSEADDR option set on
accept socket
2007.03.29 13:54:47 LOG7[13414:3083015856]: nntps bound to 127.0.0.1:2000
2007.03.29 13:54:47 LOG7[13414:3083015856]: Created pid file
/var/run/stunnel4.pid


i then startup pan and it won't connect to the server the log file says:
Thu, 29 Mar 2007 13:58:15 - Pan 0.14.2.91 Started
Thu, 29 Mar 2007 13:58:15 - Directory
"/home/ephman/.pan/messages/cache" contains 0.0 MB in 0 files
Thu, 29 Mar 2007 13:58:15 - Directory
"/home/ephman/.pan/messages/folders/pan.sent" contains 0.0 MB in 0
files
Thu, 29 Mar 2007 13:58:15 - Directory
"/home/ephman/.pan/messages/folders/pan.sendlater" contains 0.0 MB in
0 files
Thu, 29 Mar 2007 13:58:15 - News server connection count: 0
Thu, 29 Mar 2007 13:58:19 - New connection 0x846da08 for
inetnews.worldnet.att.net, port 563
Thu, 29 Mar 2007 13:59:21 - NNTP handshake failed: Error reading from socket.
Thu, 29 Mar 2007 13:59:21 - Handshake failed: Error reading from socket.
Thu, 29 Mar 2007 13:59:26 - New connection 0x84a5850 for
inetnews.worldnet.att.net, port 563

any help or hints would be really helpful.  thanks.

be well,

ephman

---

### Post by yabbadabbadont on 2007-03-30
Did you configure pan so that it is connecting to localhost using port 2000?  You didn't say.

---

### Post by ephman on 2007-03-31
tada!  that was it.

thank you,

ephman

---

