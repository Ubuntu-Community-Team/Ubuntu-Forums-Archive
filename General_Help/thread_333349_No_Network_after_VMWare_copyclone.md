---
title: "No Network after VMWare copy/clone"
date: 2007-01-07
forum: General Help
---

### Post by speediii on 2007-01-07
After making a copy/clone of an ubuntu server 6.10 the copy reports the following network issues:

1. "ifconfig" shows no eth0 device, just the 127.0.0.1 loopback
2. "/etc/init.d/networking restart" reports:

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
SIOCSIFBRDADDR: No such device
eth0: ERROR while getting interface flags: No such device
Failed to bring up eth0.

I decided to post this tip because I am a newbie and this took me ages to figure out what happened to my installation:

Solution
When you create a complete clone/copy of your vmware machine, a new ethernet MAC address is assigned:

1. view the "vmware_ubuntu.vmx" file on your local machine and look for somwhting like:
ethernet0.generatedAddress = "00:0c:29:bc:64:65"

2. now edit the iftab file: "vi /etc/iftab".  The MAC address will be different:
eth0 mac 00:0c:29:94:e4:b8 arp 1

3. Change this to the mac address in the vmware *.vmx file.

4. reboot with "shutdown -r now" or restart networking as above.

This worked for me with vmware clones.

---

### Post by Luciano on 2007-01-27
Thank you so much for posting that solution, it worked perfectly for a similar scenario.
:D

---

### Post by gadeem0517 on 2008-02-18
Thanks for the post!  Been banging my head against my monitor this morning trying to figure this out.

---

