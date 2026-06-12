---
title: "jabberd2 XMPP conf files"
date: 2012-10-25
forum: General Help
---

### Post by slimx3m on 2012-10-25
so I think I made a screw up and for some reason what I am trying to do isn't working..... I've been trying to play around with XMPP (Jabber) in Ubuntu server 12.10.  Today I just remove the package and when I reinstalled it I realized that the config where still there.  so I ran the following command
```
rm -R /etc/jabberd2/
```
to get rid of the configs.  Then I remove the package and its dependencies.  after running another 
```
sudo apt-get install jabberd2
```
I noticed that the config where no longer there :( ... does any body know where I could get the config back? or perhaps tell ubuntu to download the configs as its exporting the packages like it did the first time?


thanks for your help in advance

PS: I've been using this doc -> [https://help.ubuntu.com/12.10/serverguide/jabberd2-server.html](https://help.ubuntu.com/12.10/serverguide/jabberd2-server.html)

---

### Post by slimx3m on 2012-10-26
alright... so here was my solution since I couldn't find it anywhere else.

download a new iso of ubuntu, boot it up on a VM, and then install jabberd2.  Grab /etc/jabberd2/ folder and then migrate all of those config to my actual server.

---

### Post by lisanels47 on 2012-11-12
I'm playing with the same thing.  I was unable to get jabberd2 to work, but did get ejabberd to work. 

To uninstall them and remove the configuration files, simply do;
apt-get purge package

That will remove the package, and all the configuration stuff.

---

