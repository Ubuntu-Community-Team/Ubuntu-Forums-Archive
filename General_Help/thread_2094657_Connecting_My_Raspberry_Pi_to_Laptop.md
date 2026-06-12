---
title: "Connecting My Raspberry Pi to Laptop"
date: 2012-12-14
forum: General Help
---

### Post by Matt303x on 2012-12-14
Hello.

I am new to linux and Ubuntu (12.10). I am trying to connect my Raspberry Pi to my HP Laptop using the following guide

[http://interlockroc.org/2012/12/06/raspberry-pi-macgyver/](http://interlockroc.org/2012/12/06/raspberry-pi-macgyver/)

I am trying to SSH, and Setting Up a VNC Server

using the command below

ssh pi@x.x.x.x

The x's represent the IP address and as far as I can tell the Pi is connected to the Laptop ok however when I enter the above command into the terminal I get the following response

ssh: connect to host 10.42.0.1 port 22: connection refused

Could someone tell me how to get around this problem?

I did have a firewall installed however I unistalled it this hoping it would solve the problem with no luck

I would be grateful for any assistance. I am hoping the solution is something simple such as entering another command however my attempts so far with google have not been successful.

---

### Post by saurabhprimal on 2013-02-01
Install open ssh server on ubuntu.
sudo apt-get install openssh-server

I experienced the same problem. Worked for me.

Cheers!

---

### Post by Bucky Ball on 2013-02-01
*Thread moved to **General Help**.*

Welcome to the forums.

---

