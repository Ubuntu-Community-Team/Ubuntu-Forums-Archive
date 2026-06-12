---
title: "To run Webmin at startup."
date: 2005-08-09
forum: General Help
---

### Post by crxyem on 2005-08-09
After recieving this error.
also reffer to this thread for original poster Q. [http://ubuntuforums.org/showthread.php?t=46341](http://ubuntuforums.org/showthread.php?t=46341) 

```
Failed to open /etc/rc.d/init.d/webmin :  No such file or directory
``` 

Well I'm not linux guru, I just wanted to solve this problem for myself as well. 
It seems Webmin-1.220 doesn't have an option for choosing an appropriate "Operating System and Environment " under https://<server ip>:<port #>/webmin/
It detect Ubuntu as  "Generic Linux" and when choosing to set webmin to start at boot up it has "/etc/rc.d/init.d/" set as the defualt path.

well I tried setting the system and environment to debian, no luck.

To make a long story short this is what worked for me.
make sure webmin is stopped
$ sudo /etc/webmin/stop

Follow these instructions for d/l and install. [http://ubuntuforums.org/showthread.php?t=7507&highlight=webmin](http://ubuntuforums.org/showthread.php?t=7507&highlight=webmin)

You NEED to login as root (it will not work with sudo)
instruction to enable root login [http://ubuntuforums.org/showthread.php?t=31053&highlight=enable+root+login](http://ubuntuforums.org/showthread.php?t=31053&highlight=enable+root+login) 

Make a copy of the config file
# cp /etc/webmin/init/config  /etc/webmin/init/config.orig

edit webmin config file (use leafpad or gedit)
#leafpad /etc/webmin/init/config

modify the first two lines
init_base=/etc/rc.d/
init_dir=/etc/rc.d/init.d

change them to
init_base=/etc/
init_dir=/etc/init.d

save the file after you've made the changes.

restart webmin
#/etc/webmin/start

goto 
https://<server_ip>:<port #>/webmin/
choose start at boot time.

log out as root. 
restart ubuntu.

This worked for me, hope this is usefull, if someone else wouldn't mind checking this out for thmselves to make sure this is a fix that'd be great. 
I even loged into my webmin from a window$ system on my network

---

### Post by nerrick on 2005-09-24
I have to thank you, you solved my issue.

Here are my stats:

Ubuntu 5.04
Webmin 1.230

I followed your steps with a minor twist.

I installed webmin to /usr/local/webmin
My config dir is /etc/webmin
My log dir is /var/webmin

Since I am sort of a noob at getting webmin to run on ubuntu, I just ran the install again, but as if I were performing an upgrade. This starts webmin and verified that the change to the config was successful.

I then logged into webmin and selected the option to start at boot under the webmin configuration section and it worked like a charm.

Again I want to thank you as I was  ](*,)  prior to reading your post. Now I am  :grin: 

I give your post props.

Nerrick

---

