---
title: "Running a script with mixed privilages"
date: 2014-12-12
forum: General Help
---

### Post by diyhouse on 2014-12-12
Trying to automate the install of a tuner card driver,....  the problem is some of the script is run as root,.. some as user.

How can I run the different parts of the build process within the script as root, without changing sudo stuff and affecting all other 'make' or 'modprobe' executions on my system.

This is the list of commands I run,.. I appreciate I can drop the sudo if I run the set of commands within a script as root,.. but that defeats what I want to do as some of the script needs to run as user,. and not root.

------------------------------------------------------------
&#8203;    sudo rm -r -f /lib/modules/$(uname -r)/kernel/drivers/media
    cd ~/Downloads/tbs-linux-drivers_v140113/linux-tbs-drivers
    sudo make clean
    sudo make distclean
    sudo ./v4l/tbs-x86_64.sh
    make -j5
    sudo make install
    sudo modprobe -v tbs62x0fe
-------------------------------------------------------------

Hope that makes sense,.. and some out there has some ideas for me that escape my limited knowledge..

many thanks

---

### Post by schragge on 2014-12-12
sudo before a command affects only that one command whether you do it manually or inside a script, so I don't quite understand what do you mean.

Your script would look like (with my comments in [COLOR=red]red[/COLOR])
```

#!/bin/sh
sudo rm -r -f /lib/modules/$(uname -r)/kernel/drivers/media [COLOR=red]# I suppose you know what you're doing[/COLOR]
cd ~/Downloads/tbs-linux-drivers_v140113/linux-tbs-drivers
make clean [COLOR=red] # no need to be root for this[/COLOR]
make distclean [COLOR=red] # neither for this one[/COLOR]
./v4l/tbs-x86_64 [COLOR=red] # nor for this one[/COLOR]
make -j5
sudo make install
sudo modprobe -v tbs62x0fe

```
You run this script as normal user. When executing the first command that is prefixed with sudo it will ask your for password. Then each further command in the script prefixed with sudo will be executed with root privileges.

---

### Post by diyhouse on 2014-12-12
That's great,.. I was not aware that running sudo within a script worked as though one was typing in at the command line,..  ( I assumed it would prompt for the password at each sudo command ).
Many Thanks

---

### Post by Lars Noodén on 2014-12-12
> **diyhouse said:**
> That's great,.. I was not aware that running sudo within a script worked as though one was typing in at the command line,..  ( I assumed it would prompt for the password at each sudo command ).
Many Thanks

The [default timeout](http://manpages.ubuntu.com/manpages/trusty/en/man5/sudoers.5.html) is 15 minutes per tty.  You can change that, if needed.

---

### Post by HermanAB on 2014-12-12
Howdy,

The reason why these things are usually not scripted, is because invariably, something will go wrong, requiring human intervention somewhere along the line.  So your script requires error handling after *every* step to make it robust.

---

