---
title: "Ubuntu KVM windows 7 virtual machine no network access"
date: 2014-01-24
forum: General Help
---

### Post by claudio6 on 2014-01-24
Hi, i have just installed ubuntu 13.10 64bit and kvm which works perfectly, i installed a win 7 machine but i notice that when i boot the win machine internet works for a couple of minutes and the disconnects telling me that i have an unidentified network. I serched google but i cannot find a fix to this problem.

Any help?

thx

---

### Post by claudio6 on 2014-01-24
The network under kvm is configured as "nat"

---

### Post by claudio6 on 2014-01-25
no one can help me?

---

### Post by Jonas_Kirk_Pederse on 2014-02-27
Hello 
I have had the same problems as you. A small fix is to change the network card to e1000. This work for me but is it still really slow. Have a good friend that have made a really good blog post about this problem. He also describe what to do to get more performance out of the machine.
Here take a look [http://moozing.wordpress.com/2012/11/30/windows-7-in-qemukvm/](http://moozing.wordpress.com/2012/11/30/windows-7-in-qemukvm/)

---

### Post by baris3 on 2014-02-27
Can't you use a bridged network?

---

### Post by Jonas_Kirk_Pederse on 2014-02-27
well of cause you can. But that will surely not fix the problem because it is the VM image that has a problem obtaining a IP from a DHCP. I use Bridge network in my setup and still had the problem

---

