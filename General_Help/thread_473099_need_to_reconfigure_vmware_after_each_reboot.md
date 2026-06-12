---
title: "need to reconfigure vmware after each reboot"
date: 2007-06-13
forum: General Help
---

### Post by brazzmonkey on 2007-06-13
hi there, 
i'm trying to use vmware workstation on feisty, but every time i reboot ubuntu, i then have to invoke sudo /usr/bin/vmware-config.pl to get a functional vmware. otherwise i get:
```
$ vmware
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.
```

is there any way to prevent such behaviour ? it didn't happen when i was using vmware-server.

thx

---

### Post by hardyn on 2007-06-13
All i can think is file permissions, make sure that you have permissions to the directory where the file is being saved.

or

sudo ./usr/bin/vmware-config.pl

---

### Post by brazzmonkey on 2007-06-14
i don't know if this is permission-related, but browsing the web i figured out that it occurs because of a /etc/vmware/not_configured file being present.
Removing this file is a temporary workaround because it re-appears upon reboot.
I have to find out why this file is created.

---

### Post by brazzmonkey on 2007-06-14
any hint ?

---

### Post by brazzmonkey on 2007-06-14
*bump*

---

### Post by A_POET on 2007-06-14
good bump perhaps a couple of emails to vmware on this issue? maybe they have an irc channel....i thought this was because i use the "lowlatency" kernel but it compiles correctly using latest vmware, its just that i have to sudo config just like the others in this thread....hmm... hopefully somone can chime in. *shrugs*

---

### Post by brazzmonkey on 2007-06-14
the culprit is actuall this not_configured file being present. removing it is a temporary workaround. i found several user reporting similar issue, but any solution i've read so far didn't work for me.
or maybe i should edit the startup script to remove this not_configured file during startup. dirty hack if you ask me.

---

### Post by jjmurre on 2007-06-20
I ran into the same problem. I found another post that was helpful to me, saying that an older installation of vmware-player left something in my /etc/init.d/.

See: 
[http://www.debuntu.org/vmware-server-not-starting-after-reboot](http://www.debuntu.org/vmware-server-not-starting-after-reboot)

---

### Post by brazzmonkey on 2007-06-20
yes, i came across this webpage as well, but that didn"t sort it out, not_configured is still created upon reboot. i used to have a vmware-server installation, which i believe i cleaned up by using similar commands to the ones debuntu's webpage mentions.

still not solved...

---

### Post by total wormage on 2007-06-20
i'm sorry for asking, but you did try to do as hardyn said? running the configure with root permission?

---

### Post by brazzmonkey on 2007-06-20
yes, of course i did. but i have to run it again after reboot, or remove this not_configured file (the latter is much faster, i added kdesu rm /etc/vmware/not_configured to my shortcut).

---

### Post by brazzmonkey on 2007-07-05
my previous post can sometimes lead to errors (missing modules or equivalent).

i figured out that the following process can help:
```
sudo /etc/init.d/vmware stop
sudo rm /etc/vmware/not_configured
sudo /etc/init.d/vmware start
```

so that makes me think that maybe vmware service start too early at boot time, cannot find what it needs (modules ?) and generates not_configured. later on, (modules ?) are loaded, but the program is not aware.

---

