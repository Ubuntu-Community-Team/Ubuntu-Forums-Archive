---
title: "tcpdump across SSH session crashes during capture"
date: 2014-03-26
forum: General Help
---

### Post by sean39 on 2014-03-26
I am experimenting with running tcpdump across an SSH session and piping the output to a local run of tcpdump.

Here is the full command I am running

```
ssh -i /root/.ssh/id_rsa root@192.168.100.3 "tcpdump -l -w - host \(192.168.100.1 and 192.168.100.3\)" | tcpdump -r - -l -w test.pcap &
```

The remote tcpdump capture begins and all seems well.  However, after a short while (in this case about 10-15 seconds), if I start performing other tasks on my local machine (like hitting the ENTER key multiple times, in this case) the whole thing crashes and I get the following output:

```
[2]+  Stopped                 ssh -i /root/.ssh/id_rsa root@192.168.100.3 "tcpdump -l -w - host \(192.168.100.1 and 192.168.100.3\)" | tcpdump -r - -l -w test.pcap
```

The local file that I wrote the capture to (test.pcap) contains pcap data up until the crash and I see this at the end of the pcap file:

```
tcpdump: pcap_loop: truncated dump file; tried to read 98 captured bytes, only got 66
```

Does anyone have some insight for me?

P.S. In case you are interested, I am trying to test a way to sniff traffic on multiple remote machines and store all the captures on a centralized machine in psuedo-realtime without the need for taps and the like.

---

### Post by Lars Noodén on 2014-03-27
Are you sure to exclude SSH traffic between your client and server from capture?  If not, the number of packets will snowball until things clog.

---

