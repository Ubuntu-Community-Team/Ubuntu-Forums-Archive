---
title: "Home directory inaccesible following re-install of another OS."
date: 2007-08-06
forum: General Help
---

### Post by PaulFXH on 2007-08-06
This is a problem I've had a number of times.
I have three Linux OSes (one of which is Ubuntu) on my internal drive in addition to Windows XP.
If I need to re-install either of the other two Linux OSes, the HOME directory of my Ubuntu sometimes gets messed up and I can't find how to get out of this problem other than to re-install Ubuntu including re-formatting of the HOME partition which means I lose all my stuff.
Well, yesterday I had to re-install Debian and now I can't boot into GUI Ubuntu and get the following error messages in TTY1
> fsck.ext3: Unable to resolve 'UUID=1c07d162...........510
fsck died with exit status 8.
File system check failed
A log is being prepared in /var/log/fsck/checkfs if that location is writable
Please repair the file system manually
Prior to this the GUI boot fails complaining that the home directory does not exist.
Nothing other than the above is available in the logs mentioned.

Can anybody tell me how I can manually repair the file system associated with the home directory.

Thanks
Paul

---

### Post by confused57 on 2007-08-06
> **PaulFXH said:**
> This is a problem I've had a number of times.
I have three Linux OSes (one of which is Ubuntu) on my internal drive in addition to Windows XP.
If I need to re-install either of the other two Linux OSes, the HOME directory of my Ubuntu sometimes gets messed up and I can't find how to get out of this problem other than to re-install Ubuntu including re-formatting of the HOME partition which means I lose all my stuff.
Well, yesterday I had to re-install Debian and now I can't boot into GUI Ubuntu and get the following error messages in TTY1

Prior to this the GUI boot fails complaining that the home directory does not exist.
Nothing other than the above is available in the logs mentioned.

Can anybody tell me how I can manually repair the file system associated with the home directory.

Thanks
Paul

I believe what has happened is that the UUID's have changed on the partitions that you are changing(reinstalling, resizing, etc).  What you need to do is boot the Ubuntu live cd, open a terminal, then run the command:
```
blkid
```

Then mount your Feisty root partition:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

Compare the blkid UUID's with the UUID's listed in your /etc/fstab...if they are different, then you can just copy & paste the new UUID's into your fstab...or you can place a # in front of the entry in fstab, if you'd rather these partitions not be mounted at boot.

Obviously, you wouldn't want to comment your /home partition; however, I've received the same error message when it really had nothing to do with the /home partition...UUID(s) had changed on other partitions that were being mounted at boot.

---

### Post by PaulFXH on 2007-08-06
Thanks for your reply.
You are correct in your diagnosis. Indeed, this seems to be a known problem in Ubuntu (not sure if it's just Feisty but I never had this problem in earlier versions). It is detailed [here]("https://bugs.launchpad.net/ubuntu/+bug/106209").
Actually, my /etc/fstab was totally messed up which made it seem like my /home partition was no longer there -- but it was.
To recover, I just edited the /etc/fstab through another OS (actually Zenwalk that I have on the same drive) and commented out all of the garbage created by this bug. Then I added lines for the /, /home and swap partitions of Ubuntu and that solved the problem.
Cheers
Paul

---

