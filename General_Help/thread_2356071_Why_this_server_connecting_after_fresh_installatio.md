---
title: "Why this server connecting after fresh installation?"
date: 2017-03-19
forum: General Help
---

### Post by jovanlibert on 2017-03-19
Hi! 

My command:

tcpdump

then i see this suspicious server always connecting to pc:

 IP 2.28.77.61.63590 > Ubuntu.30303: UDP, length 171

2.28.77.61


I have analysed that most ubuntu servers are in united kingdom - Isle Of man, but this server is in Scotland.

I reinstall ubuntu once a while and i don't remember that this server connected before, so i am thinking maybe my installation usb is infected?

Or maybe this server belongs to Ubuntu?

If it belongs to Ubuntu then what's the purpose of it?

P.S

I am not lazy i have searched for info all day about this ip, but haven't found any info that it belongs to ubuntu.
I am using Linux because i question everything and you will not get answers from windows because it's not open source.
Can you help me to find out answer?

Thanks!

---

### Post by SeijiSensei on 2017-03-19
If this is a publicly-visible server, I'd stop worrying about issues like this.  Most every public machine on the Internet gets probed dozens of times a day from all over the world.  Do you have anything listening on UDP port 30303?  Do you have a firewall?  If you have no running listener on that port, and you have a decent iptables firewall, you need to relax, or you'll drive yourself crazy tracking down every single probe.

And, no, it has nothing to do with Ubuntu.  Looks like a subscriber to Orange broadband: [http://ipaddress.is/2.28.77.61](http://ipaddress.is/2.28.77.61)

---

### Post by lisati on 2017-03-19
Agreed, if you have nothing listening to port 30303, you probably have nothing to worry about. I regularly see probes being recorded in my router's firewall log, and there's nothing there for the probes to find, let alone connect to.

---

