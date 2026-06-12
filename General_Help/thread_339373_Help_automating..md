---
title: "Help automating."
date: 2007-01-15
forum: General Help
---

### Post by Phr34Ck on 2007-01-15
Hey, each time I log-in I have to do these steps in order to get connected: 
sudo ifconfig eth0 down 
sudo ifconfig eth0 hw ether "macaddress"
sudo ifconfig eth0 up 
sudo network-admin and I choose eth0 as my default gateway 

Is there a way to automate this at boot-up or at login? I'm getting sick of doing it each time I login.

---

### Post by Rippey on 2007-01-15
you can put all the commands you use in a textfile , but don't put sudo in front of them. put this on the first line "#!/bin/bash" below that 1 command per line.
save it somewhere (/etc/init.d would be a good place, but it's up to you)
now check what runlevel you're in with "runlevel" (typicly it should be 2).
in your /etc folder find a folder called rc#.d where # is your runlevel.
open it and create a symlink to the file you made (sudo ln -s /etc/init.d/yourfile s99yourfile)
and your done.

---

### Post by Phr34Ck on 2007-01-16
Great, thanks. Now how can I automated the last part? I don't know what command I should use in the terminal. I have to go to the network-admin interface to choose my default gateway.

Thanks.

---

### Post by phossal on 2007-01-16
Even simpler, you could open up your .bashrc file and make a little function at the bottom:
```

#Copy me at bottom of .bashrc
function c () {
     sudo ifconfig eth0 down
     sudo ifconfig eth0 hw ether "macaddress"
     sudo ifconfig eth0 up
     sudo network-admin and I choose eth0
}
#End Copy

```

Then, as soon as you've signed in, you press c (or whatever you name the function). Although pressing "c" may be a drag, backing up your .bashrc file with all of your configuration for your *next* install is a lot easier than chasing down all your configuration scripts (assuming you have a bunch littered around).

[edit] A lot of people seem to run through a bunch of the networking commands not really knowing what they (the people *and* the commands) are doing. They use a tutorial the first time, and then continue using the last set of functions that seems to get them up and running. Many times, your hardware is already configured, and you  just need to force it to ask the network for an IP. Often, none of the ifconfig/ifup/ifdown stuff is necessary. Issue dhclient like so:
```
sudo dhclient eth0
```

---

