---
title: "Error installing Prey on Ubuntu 14.04"
date: 2015-04-30
forum: General Help
---

### Post by Briga on 2015-04-30
I would like to share an issue I encountered and how I fix it. 

I was installing prey (the tracking sw) on my Ubuntu 14.04 amd64 machine by downloading from the website since there is a 1.3.9 version vs the 0.6 in the repository. 

When you install the deb it has errors in the post installation process and apt-get install -f won't solve it. Here is how to do it, or at least worked for me.

Download the prey deb package
Install it via sudo dpkg -i or Ubuntu software centre as you like (--force-all won't work.... just in case). 

You'll be left with an error at the end. 

Open a terminal windows (Ctrl  + Alt + T)

To fix the error go to /var/lib/dpkg/info and run the command
```
cd /var/lib/dpkg/info
sudo nano prey.postinst
```
Of course you can use any other editor. 
Comment out the line with set -e by adding a # at the beginning:
```
#!/bin/bash
####################################################################
# Prey Debian Postinst Script
# Written by Tomás Pollak <tomas@forkhq.com> - (c) 2011 Fork Ltd.
# License: GPLv3
####################################################################

#set -e

```
Save it and now run
```
sudo apt-get install -f
```
error fixed. Only issue left is to complete manually the prey installation to configure the account. Run:
```
sudo /usr/lib/prey/current/bin/prey config account setup
```
and follow the instructions!

Best of luck :)

---

### Post by bernalaurelio on 2015-05-16
hello

 I followed your guide in ubuntu 14.04 and it worked well.

 I wanted to do the same in Ubuntu 15.04 and the installation ends without problems and the computer is added in the control panel of prey.

 The problem is that despite flag as lost prey computer software does not give any report on page.

 Thanks in advance for any help you could give me.


 thanks

;)

---

