---
title: "Help with bash script for VPN"
date: 2007-01-30
forum: General Help
---

### Post by dr_d12 on 2007-01-30
Hello,
I use Cisco VPN to connect through work. To connect I have been entering the following into terminal:

     screen
     sudo /etc/init.d/vpnclient_init start
     sudo vpnclient connect mcgill

I hit enter to accept my username (or I can type my username again),
I enter my password and hit enter
I have to type yes and hit enter
Then I hit Ctrl-A and Ctrl-D to detach the session, leaving VPN open.

I'm trying to write a bash file to automate the entire process, or as much of it as possible.
 So far, the following file (VPNconnect.sh) will start vpnclient and make the connection:

     #!/bin/bash
     sudo /etc/init.d/vpnclient_init start
     sudo vpnclient connect mcgill

Then I have to enter username, password, and yes. I tried to use echo to enter these but that didn't work (yes I'm new to this).

I want to use:

     #!/bin/bash
     screen -d -m ./VPNconect.sh

in order to run the VPNconnect script in a screen session, but if I can't enter my username and password (and yes) with bash, that won't help at all.

Your comments are welcome.
DD

---

