---
title: "sshfs, bash script help"
date: 2007-02-01
forum: General Help
---

### Post by hunter186 on 2007-02-01
I'm using sshfs to mount several directories, and I'm tying to write a little bash script to automate mounting.  Here is what I have so far:


#!/bin/bash
sshfs <server ip>:/home/hunter186 /media/Home_remote
echo Mounting Home
sshfs <server ip>:/media/Seagate /media/Seagate_remote
echo Mounting Seagate

The problem is that this prompts me for my password twice.  I'd like to only enter it once (its a long password:) )  I'm not sure how to use one sshfs command to mount two (or more) directories.

This is my first attempt at any bash scripting, and I'm most definately a noob.  Any help would be appreciated.

---

### Post by chriscando on 2007-02-01
Can you put sudo infront of the commands? This way it will usually only ask you for a password once.
```
#!/bin/bash
sudo sshfs <server ip>:/home/hunter186 /media/Home_remote
echo Mounting Home
sudo sshfs <server ip>:/media/Seagate /media/Seagate_remote
echo Mounting Seagate
```

---

### Post by hunter186 on 2007-02-01
Using sudo, sshfs tries to ssh into the root account, rather than my user.  I just want to mount two directories with one sshfs command.

---

### Post by hunter186 on 2007-02-01
N/M about this one.  I ended up using password-less RSA authentication.  Works even better!

---

### Post by SeanTater on 2007-02-01
Having no password on your ssh key can be dangerous. Have you considered using ssh-add instead? ssh-add will remember your passphrase so you only need to enter it once per reboot, regardless of how many times you use it..

---

