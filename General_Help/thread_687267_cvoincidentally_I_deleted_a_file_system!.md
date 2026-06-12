---
title: "cvoincidentally I deleted a file system!"
date: 2008-02-04
forum: General Help
---

### Post by mathutu on 2008-02-04
Hello

I, somewhat strangely, managed to delete my file system "/bin/sh"! Well you can imagine that my ubuntu 7.10 did not load anymore.

What I did to recover the file was as follows: I used the ubuntu gutsy live CD to boot. I continued until that lovely ubuntu desktop came up, that one before real installation.

I used what was offered by the CD, browsed places/computer, mounted the old ubuntu partition and issued:
```
sudo cp /bin/sh /media/disk/bin/ 
```

It worked and I was able to load ubuntu once more. But it, during the last few hours, failed three times to load: it stopped before starting xserver. I restarted and everything was then fine. This happed two more times.

Now my question is the following: was my solution a canonical and correct one? (I doubt it). 

Of course I can not verify that my new /bin/sh is the same as what I had before and strictly speaking it is not: because the original one is a link to a x-executable whereas the new one is a real file.

Any idea about these? I really do not want to reinstall ubuntu, as I had to work hard to get everything (vide card, monitor, scientific programs, multimedia softwares and players) work.

Maybe I should ask: if there is a way to reset the filesystems to their correct original ones.

I thank you in advance. 
Regards, 
mathutu

---

### Post by danwood76 on 2008-02-04
How did you manage to delete /bin/sh?
That is just a link to /bin/bash, the command line interpreter I thought.
But no command you issue should delete this.

The only way to truley restore your system is to either make a backup of the system and restore it (you can tar your entire system buen to a DVD and restore it very easily) or do a complete re install.

regards,
Danny

---

### Post by mathutu on 2008-02-04
thanks for the reply,

how did i deleted?:
```
sudo rm -f /bin/sh
```
yes! I knew what that means, but I was doing some experiment with other linux distribution packages.

I think still i have the original file: /bin/bash, should i delete the new /bin/sh and make a symbolic link to /bin/bash?

regards,
mathutu

---

### Post by erginemr on 2008-02-04
Hold on!

I have attached a screenshot of my system, where /bin/sh surprisingly points to "dash", an entirely different executable, in lieu of "bash" (which I also thought would be the case).

I think you should google for this "dash", and alsocheck its existence in your Ubuntu system  before taking any further steps.

---

### Post by danwood76 on 2008-02-04
No, if you copied the one from the live CD it should be the same, as that is essentially a ubuntu environment.
If as you say it is not a sym link, the original links to /bin/dash (my comment about bash in my last post was wrong) and it is just a sym link so you could try that.

The strange non starts would worry me, but it may be caused by the fact that /bin/sh is modified for the Live CD version.

regards,
Danny

---

### Post by mathutu on 2008-02-04
> **erginemr said:**
> Hold on!

I have attached a screenshot of my system, where /bin/sh surprisingly points to "dash", an entirely different executable, in lieu of "bash" (which I also thought would be the case).

I think you should google for this "dash", and alsocheck its existence in your Ubuntu system  before taking any further steps.
thanks erginemr,

strange! i have the file /bin/dash. shoulod i simply issue the following :```
sudo ln -S /bin/dash /bin/sh
```

---

### Post by erginemr on 2008-02-04
I believe you should go for it, but should be careful to refer to your mounted file system and use lowercase "-s" as the argument to "ln":
```
sudo ln -s /media/disk/bin/dash /media/disk/bin/sh
```

---

### Post by mathutu on 2008-02-04
> **erginemr said:**
> I believe you should go for it, but should be careful to refer to your mounted file system and use lowercase "-s" as the argument to "ln":
```
sudo ln -s /media/disk/bin/dash /media/disk/bin/sh
```

Thanks again, once I am at home tonight, i try this and will let you know the result.

---

### Post by erginemr on 2008-02-04
You are welcome. 

Alternatively, you can fix this problem without the Live CD by following these steps:

1. Boot your machine without the Live CD.
2. At the Grub prompt, select "Recovery Mode", press "e" to edit it.
3. Go to the line with "kernel /boot/...", press "e" again and write "init=/bin/bash" to the end of the line.
4. Press "b" to boot with these options.
5. The system will load to a text-only environment, with root permissions, but with a read-only file system.
6. To make it rewriteable, mount the root file system with: "mount -o remount,rw /"
7. Create the link: "ln -s /bin/dash /bin/sh" as usual.
8. Remount the drive as read-only again "mount -o remount,ro /" to make sure that changes have been reflected.
9. Finally, reboot with "Ctrl+Alt+Del" to say welcome back to your system.

---

### Post by mathutu on 2008-02-10
Hello,
Sorry for delay. I just wanted to add a line that the problem on start-up did not happen again and it seems creating a link to bin/dash  works.

Thanks,
mathutu

---

