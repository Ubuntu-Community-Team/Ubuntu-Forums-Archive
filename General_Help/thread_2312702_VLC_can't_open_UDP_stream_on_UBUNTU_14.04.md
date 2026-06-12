---
title: "VLC can't open UDP stream on UBUNTU 14.04"
date: 2016-02-06
forum: General Help
---

### Post by dejan-ciric-do on 2016-02-06
Hello,

I have Ubuntu desktop 14.04 with two NIC, eth0 and eth1. One is just for internet and the other one is on local subnet where multicast UDP stream is coming.
Default route is on eth0, and multicast route is on eth1. UDP stream is coming on eth1 and I can see that is here with TCPDUMP on that interface but can't open it in VLC. In VLC log I can see that VLC can't open that port or what?
Can someone help me? Is that problem with some user rights or port is closed, or what?
The same stream I can play on other computer with windows. Here is VLC log:

main debug: processing request item: udp://225.224.2.2:1002, node: Playlist, skip: 0
main debug: resyncing on udp://225.224.2.2:1002
main debug: udp://225.224.2.2:1002 is at 9
main debug: starting playback of the new playlist item
main debug: resyncing on udp://225.224.2.2:1002
main debug: udp://225.224.2.2:1002 is at 9
main debug: creating new input thread
main debug: Creating an input for 'udp://225.224.2.2:1002'
main debug: using timeshift granularity of 50 MiB, in path '/tmp'
main debug: `udp://@225.224.2.2:1002' gives access `udp' demux `' path `@225.224.2.2:1002'
main debug: creating demux: access='udp' demux='' location='@225.224.2.2:1002' file='(null)'
main debug: looking for access_demux module matching "udp": 20 candidates
main debug: no access_demux modules matched
main debug: creating access 'udp' location='@225.224.2.2:1002', path='(null)'
main debug: looking for access module matching "udp": 25 candidates
access_udp debug: opening server=:0 local=225.224.2.2:1002
main debug: net: opening 225.224.2.2 datagram port 1002
main error: socket bind error (Permission denied)
access_udp error: cannot open socket
main debug: no access modules matched
main error: open of `udp://@225.224.2.2:1002' failed
main debug: dead input
main debug: changing item without a request (current 9/10)
main debug: nothing to play

here is ip route:

ip route
default via 192.168.2.1 dev eth0  proto static 
192.168.2.0/24 dev eth0  proto kernel  scope link  src 192.168.2.50  metric 1 
192.168.10.0/24 dev eth1  proto kernel  scope link  src 192.168.10.25  metric 1 
224.0.0.0/4 via 192.168.10.25 dev eth1

---

