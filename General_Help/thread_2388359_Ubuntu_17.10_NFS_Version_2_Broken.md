---
title: "Ubuntu 17.10 NFS Version 2 Broken"
date: 2018-04-01
forum: General Help
---

### Post by nanook2 on 2018-04-01
I have a heterogeneous network consisting of about a dozen+ different Linux distributions and one SunOS 4.1.4 machine (BSD based OS from the 80s-early 90s).  All the Linux machines speak at least NFSv3 and the vast majority NFSv4, but the SunOS box only speaks NFSv2.  In 17.10 I can not get nfs-kernel-server and nfs-common to server version 2 leaving this SunOS box stranded.  This worked in 17.04 and it works in Bionic but I am hesitant to upgrade a functioning server to a beta release, besides there is no way I know of doing it online.  I don't want to leave this SunOS box broken until 18.04 comes out (I have tested the beta and NFS does work on it).  I can not figure out how to use apport to submit a bug report where I can actually describe what it is doing.  I have added the necessary entries to /etc/default/nfs-kernel-server, and checked and rechecked that it is correct.  rpcinfo does not show nfs version 2 being served.  Any assistance would be much appreciated.  [EMAIL="nanook@eskimo.com"]nanook@eskimo.com[/EMAIL]  thanks.

---

