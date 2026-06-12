---
title: "Automating sshfs mount via bash script"
date: 2022-07-12
forum: General Help
---

### Post by veedub67 on 2022-07-12
Hello,

I'm using Ubuntu 22.04

I'm able to perform an sshfs mount within terminal, but when I try to perform the identical command in a bash script (via sudo) it fails.

I'm hoping for some troubleshooting suggestions

Note: I'm using keys rather than user/pass for authentication

Here is the command
```
sudo sshfs fqdn_of_remote_host:/share/ /tmp/droplet/ -o rw,noatime
```

From terminal this works 

In the bash script I use
```
[FONT=Verdana]sshfs fqdn_of_remote_host:/share/ /tmp/droplet/ -o rw,noatime[/FONT]
```

I launch the script with sudo

And I get:
```
No such file or directory
```

---

### Post by QIII on 2022-07-12
Is ```
/tmp/droplet/
``` an actual mount point, or is that an obfuscation for the sake of the question?  That is, do you really want this mounted in /tmp?

---

### Post by veedub67 on 2022-07-12
> **QIII said:**
> Is ```
/tmp/droplet/
``` an actual mount point, or is that an obfuscation for the sake of the question?  That is, do you really want this mounted in /tmp?

@QIII

That is the actual mount point, currently.

I only need it mounted for a short time, so it seemed fine to use.

I don't think that is the issue, because it works via the terminal.

The issue that I have is that it's not mounting via the bash script and that's a problem because I want to automate the process.

---

### Post by SeijiSensei on 2022-07-12
I use sshfs to connect between remote servers. I put the command in /etc/rc.local so it runs at boot. However, rc.local is deprecated in recent Ubuntu releases, so you have to do a bit of scrambling to make it work. See [https://marsown.com/wordpress/how-to-enable-etc-rc-local-with-systemd-on-ubuntu-20-04/](https://marsown.com/wordpress/how-to-enable-etc-rc-local-with-systemd-on-ubuntu-20-04/) for details.

In my /etc/rc.local on the client:
```
su -c 'sshfs -o reconnect remote_server:/home/username /mount/point' username
```

I use this formulation to have the remote share mounted as user "username." To mount it as root, just use the command inside the quotation marks.

I assume the bash script has the execute permission set, yes?

---

### Post by ActionParsnip on 2022-07-12
You can also add it in /etc/fstab to mount at boot

---

### Post by veedub67 on 2022-07-12
> **ActionParsnip said:**
> You can also add it in /etc/fstab to mount at boot

Thanks for the suggestion.

But I don't want the directory mounted at boot, I wanted it mounted at script runtime.

My question really relates to how to troubleshoot a command that executes via terminal, but then fails when used via a bash script. That is, how to identify the reason for the error when trying to execute the same command via a bash script.

---

### Post by veedub67 on 2022-07-12
Hello,

I've worked this out through trial and error

I made a couple of changes and I don't know which one was the answer and I don't care either.

So I'm just updating the thread with what worked for me, for future reference.

I set a variable with the mount argument
```
MOUNT_REMOTE_FILE_SYSTEM_COMMAND="sshfs fqdn:$BACKUP_PATH $MOUNT_POINT -o rw,noatime"
```

To execute the mount, I use
```
eval "$MOUNT_REMOTE_FILE_SYSTEM_COMMAND"
```

I changed the mount point to
```
REMOTE_MOUNT_POINT="/tmp/outputfs"
```

Bottom line. I wasn't able to perform diagnostics on why the previous command wasn't working in the bash script. 

Instead, I went looking for examples where an sshfs mount was being successfully performed via a bash script and then modified my previous command to "match" the working example.

---

### Post by Skaperen on 2022-07-12
> **veedub67 said:**
> 
I launch the script with sudo

And I get:
```
No such file or directory
```

in what directory is the script located?

take a peek at root's PATH environment variable:
```

sudo env | grep PATH=

```

is the script's parent in PATH?  if not, either add that parent to PATH or run it using its full path.  if it is in PATH then tell us the output of (using the script's basename in place of "foo":
```

sudo which foo

```

to temporarily add a path to PATH, do it via bash with -c:
```

sudo bash -c 'export PATH="/path/to/the/script:$PATH";command line to run the script'

```

---

### Post by TheFu on 2022-07-13
When using sudo with sshfs, you've effectively said that you want remote root ssh logins. That isn't how Ubuntu is setup, so you'd need to go out of your way to allow that.  

Remote root isn't generally needed, though I have something like it setup for backups (I use "pulled" network backups) that allow remote ssh from 1 system into each client to be backed up, but the root account isn't used for this. I consider it too much of a security fail to allow remote root.  The 'root' name is just too well-known.

---

