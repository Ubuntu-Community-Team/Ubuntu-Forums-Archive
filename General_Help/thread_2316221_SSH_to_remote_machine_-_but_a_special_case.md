---
title: "SSH to remote machine - but a special case"
date: 2016-03-06
forum: General Help
---

### Post by Tis_Ugol on 2016-03-06
Running ubuntu server 14.04
I have installed openhab which is runnuing under openhab user
Now i need openhab to send remote ssh commands as a REMOTEUSER@REMOTEMACHINE.

This is what it looks like in passwd
```
openhab:x:112:121:openHAB runtime user,,,:/var/lib/openhab:/bin/false

```

What i have tried is running
```
#sudo -u openhab ssh-keygen
#sudo -u openhab ssh-copy-id -n -i /var/lib/openhab/.ssh/id_rsa.pub REMOTEUSER@REMOTEMACHINE
```
and get the following error
mktemp: failed to create file via template ‘/home/MYUSER/.ssh/ssh-copy-id_id.XXXXXXXXXX’: Permission denied
mktemp failed


So i wonder if this can be done and steps involved

---

### Post by TheFu on 2016-03-06
Don't use sudo when you are already root.

You must be able to login to the remote machine **BEFORE** you can ssh-copy-id to it.  Get that working first.

Turn up the debug messages for the connection to show any issues.   -vvv added to ssh will work.  

It is helpful to always say which machine and userid you are using for all commands like this.  For example, which passwd file did you show above? Not clear as it is today, but I shouldn't matter for the remote ssh if that is the client.

ssh-copy-id is a convenience tool. You can always do it manually with copy/paste and other accounts.  Just be certain to set the ownership and permissions correct in the ~/.ssh/ directory on the remove machine.

---

