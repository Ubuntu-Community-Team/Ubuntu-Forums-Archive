---
title: "sshfs and keeping connection going after switching wireless networks"
date: 2007-10-15
forum: General Help
---

### Post by Scotty562 on 2007-10-15
Right now I connect to a dedicated box via sshfs.  What I am trying to do is keep my sshfs share connected after I connect to a different wireless network. I'm a college student so I'm constantly moving around so this is pretty important.  What happens right now is when I go to a new location I have to do the umount nonsense or restart the machine and restart my sshfs connection. I run a script ./ssh and it connects two shares, and they are /hda1 and /hdb1. 

I would like to make it clear that the sshfs connection works just fine until I change networks.

A few things I've thought about are the autossh I found on the forums.  I don't really understand how it works or if it will solve the problem. The other thing I thought about is using the scripts that are run when a network device goes up or down. Maybe I could have it run the mount script when it goes up and the unmount script when it goes down? If this works, that is just great, but I have no idea how to do this.

And just for anyone that is interested sftpDrive does this nicely in Windows.

---

### Post by Jussi Kukkonen on 2007-10-15
> The other thing I thought about is using the scripts that are run when a network device goes up or down. Maybe I could have it run the mount script when it goes up and the unmount script when it goes down? If this works, that is just great, but I have no idea how to do this.

That should work nicely. Take a look at */etc/network/* and put your executable mount and umount scripts in */etc/network/if-up.d/* and  */etc/network/if-down.d/*.

---

### Post by Scotty562 on 2007-10-15
I put my script in that folder, but it doesn't seem to be running. I did chmod +x on as well.

Does this script get executed as root? It's important because this script will only work correctly run as my regular user.

---

### Post by Jussi Kukkonen on 2007-10-15
> Does this script get executed as root? It's important because this script will only work correctly run as my regular user.
Yes, that's your problem. You could make the commands run as your regular user, but the "correct" thing is to fix you script so root can run it...

---

### Post by Scotty562 on 2007-10-15
The script runs a fuse command which I thought I remember being told I didn't want to be run as root. I don't mind the script running as root though, I just want the thing to work whether it be a hack-job or not :).

---

### Post by Scotty562 on 2007-10-18
Bump. I'm excited to get this working. :)

---

### Post by tkharris on 2007-10-18
> **Scotty562 said:**
> The script runs a fuse command which I thought I remember being told I didn't want to be run as root. I don't mind the script running as root though, I just want the thing to work whether it be a hack-job or not :).

You can do:

```

su [user] -c'/home/youruser/wireless_script'

```

That will execute the script as whatever user you replace [user] with.  :)

---

