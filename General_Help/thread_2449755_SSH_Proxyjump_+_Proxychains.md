---
title: "SSH Proxyjump + Proxychains"
date: 2020-09-01
forum: General Help
---

### Post by getut on 2020-09-01
I am needing some help figuring out ssh proxyjump.

I regularly use proxychains along with ssh with the -D option, but work from home has added a few extra hops that I haven't figured out how to deal with.

When the usual number of hops are there, this is what I use...

I open a terminal window and use the below command to establish a connection to my remote host A.

ssh -D 9999 user@hostA

I then open a second windows and use the following command to do the work I need to do. The app varies depending on the task needed. My proxychains.conf file is using SOCKS V5 on port 9999 as the config.

proxychains APPLICATION

In other words...

Localhost -> HostA -> Proxychained app to any host or service accessible from Host A


I now need to change that to

Localhost -> HostA -> HostB -> Proxychained app to any host or service accessible from Host B

I have read about proxyjump simplifying this but all the examples I see never specify a SOCKS host port number

but its something like 

ssh -J 

but that is where I get confused. I understand the first host will be hostA but host be is where my SOCKS "exit point" on the HostB network is. How do I do that and specify 9999 with proxyjump?

---

### Post by getut on 2020-09-01
I was making too much out of it. Much simpler than I thought...

ssh -J user@hostA -D 9999 user@hostB

proxychains APP

All of the examples online assumed SSH to the final host and were throwing another host in the examples that I didn't initially understand. Proxychains builds to the final host so it isn't a hop host as far as the proxyjump subcommand is concerned.

---

