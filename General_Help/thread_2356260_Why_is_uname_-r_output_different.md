---
title: "Why is uname -r output different"
date: 2017-03-21
forum: General Help
---

### Post by rfedeleo on 2017-03-21
I am running 2 identical servers. I just updated everything and rebooted. When I run lsb-release -a I get the following on both servers:

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 14.04.5 LTS
Release:        14.04
Codename:       trusty


However when I run uname -r
I get 
3.13.0-112-generic
3.13.0-113-generic

Can someone explain to me how this might happen? The reason why we are wanting to resolve this is that we are running some iperf3 tests and the results are coming back slightly different depending on which side we initiate the test from. Before addressing whether it is a networking issue we wanted to be sure that both machines are identical so as not to blame the network to prematurely.

Thanks

---

### Post by SeijiSensei on 2017-03-21
Did you run "sudo apt-get dist-upgrade" on both machines, or just "upgrade?"  Only the former will update the kernel.  The latter will report that certain items are "held back," usually the kernel and its associated files.  I assume you ran "sudo apt-get update" before upgrading on both machines.

---

