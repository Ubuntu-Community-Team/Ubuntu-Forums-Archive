---
title: "VMWare Server not releasing memory on close"
date: 2007-08-26
forum: General Help
---

### Post by knowmad on 2007-08-26
Hi,

I've successfully installed VMWare Server using the instructions from [http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html](http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html). I am able to add and execute virtual machines as well as monitor them remotely using VMWare Server Console. It's very cool!

While reviewing sytem load and resource usage with 'top', I noticed that an excessive amount of RAM was being consumed although I was only running 2 x 512Mb servers. I shut down the servers but the memory usage stayed high. I figured that perhaps vmware was holding it open. I restarted the servers to see if memory would remain the same or grow; it grew. So I shutdown vmware server to see if closing the parent process would clear the memory. It still remained high until a reboot.

I could not find any other mention of memory leaks or vmware not releasing memory back to the host server around the net. Has anyone else seen this issue? I wonder if it is a problem due to 64-bit hardware.

Here are my host server configurations:

AMD Opteron 246 (64-bit single core)
4Gb RAM
Feisty Fawn 7.04
kernel 2.6.20-16-server


Thanks for any suggestions,
William

---

### Post by fjgaude on 2007-08-26
Hey, I think this is normal if your host is Linux. Linux uses all the memory as cache so we have best quickness; it's not like Windows.

Really, Linux uses all the RAM in your system as soon as you start using programs, like vmware, and doesn't let go... all in cache ready for quick use without having to go back to disk. In fact vmware because of its closeness with the kernel may still be in cache even when unloaded.

frank

---

### Post by utpeter on 2008-01-02
Hi,
I run into the same problem on IBM eserver with 10 GB RAM. After intalling VMware Server 2 Beta, I can see that almos all the RAM is used without even one VM running. This is a 32 bit installation on Gutsy Server. I know Linox usually cashes RAM. I've been using VMware Server and ESX for few years. I've never seen such behaviour (VMware UI showing almost 100% RAM usage without ruuning VMs) even on Windows hosts (Which r VERY MUCH RAM consuming machines). Hope this is not a bug in the VMware Server 2 beta.

---

### Post by insert_name_here on 2008-01-26
I have this too, in standard VMware server from repos.

After I shut vmware, 60-some percent of my RAM is being used as cache.  Therefore, when I try to start something even minimally memory-intensive (firefox, amarok) it goes slowly or even locks up the program.

It would be terrific if I could, somehow, clear all the cached RAM that vmware uses to restore my computer to its state prior to when I ran vmware without restarting.

---

