---
title: "Kernel 4.4.x and Suricata timestamp issues"
date: 2016-02-21
forum: General Help
---

### Post by karesmakro on 2016-02-21
I've already posted to the suricata user mailing list, where they mean, that this may be a ubuntu specific issue!

I'm using ubuntu 14.04 lts 64 bit with one ethernet and nfqueue on a virtual machine with kvm and all is working fine. After upgrading from kernel 4.3.5 to 4.4.2 I have timestamp issus in suricata fast.log and connection interruptions.
```
01/01/1970-01:00:00.000000  [Drop] [**] [1:2010935:2] ET POLICY Suspicious inbound to MSSQL port 1433 [**] [Classification: Potentially Bad Traffic] [Priority: 2] {TCP] xx.xx.xx.xx:xxxx -> xx.xx.xx.xx:1433
```
another hardware show's timestamps like this one:
```
00.000000  [Drop] [**] [1:2010935:2] ET POLICY Suspicious inbound to MSSQL port 1433 [**] [Classification: Potentially Bad Traffic] [Priority: 2] {TCP} xx.xx.xx.xx:29358 -> xx.xx.xx.xx:1433
```

the couriousity is that some of logs have the right timestamp, but it seems to be rule related, because this entries have always the right timestamp:
```
02/20/2016-20:53:31.085939  [Drop] [**] [1:2101201:10] GPL WEB_SERVER 403 Forbidden [**] [Classification: Attempted Information Leak] [Priority: 2] {TCP} xx.xx.xx.xx:80 -> xx.xx.xx.xx:51728
```

I'm also using an ubuntu 15.10 64 bit release, but it is using ethernet bridging and nfqueue. The timestamps on this machine are correct, but I have a lot of "SURICATA STREAM ESTABLISHED retransmission packet beforelast ack [**] [Classification: (null)]" messages in fast.log and sometimes unexpectable connection interruptions.

[https://redmine.openinfosecfoundation.org/issues/1715](https://redmine.openinfosecfoundation.org/issues/1715)

Can anyone tell me what makes Ubuntu different here

regards

---

