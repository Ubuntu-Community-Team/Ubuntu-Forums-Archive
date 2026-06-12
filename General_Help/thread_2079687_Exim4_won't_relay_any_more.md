---
title: "Exim4 won't relay any more"
date: 2012-11-02
forum: General Help
---

### Post by lordbah on 2012-11-02
Suddenly exim4 won't relay mail from my other local computers.

2012-11-02 07:48:14 H=cpe-67-XXX-XXX-XX.rochester.res.rr.com ([192.168.218.110]) [67.XXX.XXX.XX] F=<lordbah@mydomain.com> rejected RCPT <me@elsewhere.com>: relay not permitted

The mail server is a Ubuntu desktop. 192.168.218.110 is an Android tablet.

My update-exim4.conf.conf had this which used to work:

dc_relay_nets='192.168.218.0/24'

This morning I changed it to the following and restarted, to see if I could get just one of my other devices to be able to send, and it still didn't work:

dc_relay_nets='192.168.218.110'

Exim version is 4.76, Ubuntu 12.04.1.

From the desktop, I can email external sites.

---

### Post by lordbah on 2012-11-02
I don't know why, but what fixed it was adding the desktop's external IP address to dc_relay_nets

dc_relay_nets='192.168.218.0/24;67.XXX.XXX.XX'

---

