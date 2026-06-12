---
title: "SSH to ubuntu server vm from ubuntu pc"
date: 2015-11-25
forum: General Help
---

### Post by william_mcarthur on 2015-11-25
Hi There,

So I'm pretty new to Ubuntu and learning quickly but I seem to have got stuck trying to ssh to my ubuntu vm. I have no idea of how to get the hostname and ip address so that I can connect to it.

Would be awesome if someone could help me out!

Thanks

---

### Post by sailingboyLLB on 2015-11-25
are you trying to ssh from the host OS that has the VM in it or from another computer?

there's a couple of things here. an ssh server is not installed by default.  you need to run ```
sudo apt-get install openssh-server
``` on the guest OS.

now for the IP address, most VM's support a couple of different options.  here is the documentation for virtualbox on the networking options. although the specifics are only helpful if you're using virtualbox, the concepts apply to most VM's.  [https://www.virtualbox.org/manual/ch06.html](https://www.virtualbox.org/manual/ch06.html)

to get the IP, you can run ```
ifconfig
``` on the guest machine.  you can also get this information from the VM program on the host, for example in virtualbox you can hover over the network icon in the VM window.  keep in mind, not all networking modes will allow access to the VM from the outside.

---

