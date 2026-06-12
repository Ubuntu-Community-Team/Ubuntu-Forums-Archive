---
title: "PLEASE HELP: Client failed to connect to the D-BUS daemon"
date: 2013-05-02
forum: General Help
---

### Post by mvorloff on 2013-05-02
Hello everyone. I have this weird problem with D-BUS error messages and I wonder if anyone could help.

I am running Ubuntu 12.04.2 Desktop with VirtualBox 4.2.12 (host). On host I am running two Ubuntu 12.04.2 Server virtual machines (guests). Host and guests are on the same network, and I am able to rlogin and ssh from host to guests.
I am able to connect to either guest (individually) and with properly set DISPLAY variable on guest and xhost + on host I am able to bring up gvim, terminator and other GUI apps from guest to host.
The problem arises when after having brought up (seemingly) any GUI app on guest1. If I try to bring up the same GUI app on guest2 I am getting the following error messages on guest2 (yet GUI is still able to start):

**(gvim:2535): GConf-WARNING **: Client failed to connect to the D-BUS daemon:**
**Failed to connect to socket /tmp/dbus-SQEvsgIaCL: Connection refused**
 
This message seem to pop up on the guest that is second to display GUI. So if I start gvim on guest2, this message pops up on guest1 terminal when I try to gvim on guest1.
The other thing I noticed that this message **will not** pop up if I start gvim as user1 on guest1 and then gvim as user2 on guest2. Seemingly, it somehow rejects the same user from two guests and OK two users from two guests.
I tried connecting to guests with rlogin, ssh and ssh –Y. No difference.
I would greatly appreciate any help with this issue as I was banging my head on this for last two days.

---

### Post by mvorloff on 2013-05-02
Some additional info I just discovered... I get no error message if instead of launching "/usr/bin/gvim" I use "dbus-launch --exit-with-session /usr/bin/gvim"

---

### Post by mvorloff on 2013-05-04
Ok, I solved the problem myself.

Just in case if someone else faces the same issue here is the solution.

It turned out that problem was related to second VirtualBox guest being a clone from from the first.
Apparently, changing the /etc/hosts and /etc/network/interfaces was insufficient. 

On to top of that /var/lib/dbus/machine-id had to be removed on the cloned instance so that it got regenerated with a distinct id on reboot.

---

