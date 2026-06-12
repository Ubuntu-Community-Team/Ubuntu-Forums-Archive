---
title: "Cannot login because no free space"
date: 2007-08-24
forum: General Help
---

### Post by Il Capitano on 2007-08-24
When I try to login on ubuntu, i get the error message "GDM could not write to your authorization file. This could mean that you are out of disc space or that your home directory could not be opened for writing. In any case, it is not possible to log in. Please contact your administrator."

And my disk is full. According to df -h from a live cd I have no space left:
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                1014M   33M  981M   4% /lib/modules/2.6.20-15-generic/volatile
tmpfs                1014M   33M  981M   4% /lib/modules/2.6.20-15-generic/volatile
varrun               1014M  104K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M  148K 1014M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
tmpfs                1014M   24K 1014M   1% /tmp
/dev/sda1             456G  437G     0 100% /media/disk

However, as you can see, there is a big gap between the size of the fs and the used space. I am trying to get some of that space available, so i can cleanup my disk.

I have deleted a lot of files (10 GB in total)m but the available space doesnt increase.
Both the .Trash from home and root is empty. 

Any ideas?

---

### Post by heimo on 2007-08-24
If you boot like usually, but then change to virtual console (ctrl+alt+F2), log in and run 
```
sudo apt-get clean
```... it will clear your package cache (some software packages that can be downloaded when needed) and it may be enough to free some space (so that you can log in). Use ctrl+alt+F7 to get back to gdm.

---

### Post by Il Capitano on 2007-08-24
Wow, i heard this forum was fast, but i didn't think it would be this fast...

But anyhow, i had already used the apt-get clean command to free up some space. The problem isn't that i don't have free space, the problem is that it is not available.

---

### Post by Il Capitano on 2007-08-24
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/gdm/+bug/35217/comments/10](https://bugs.launchpad.net/gdm/+bug/35217/comments/10) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I would like to add that my problem is the same as the one here:
[https://bugs.launchpad.net/gdm/+bug/35217/comments/10]("https://bugs.launchpad.net/gdm/+bug/35217/comments/10")

Except for the fact that it still isn't working on my computer.

---

### Post by heimo on 2007-08-24
> **Il Capitano said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/gdm/+bug/35217/comments/10](https://bugs.launchpad.net/gdm/+bug/35217/comments/10) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
                I would like to add that my problem is the same as the one here:
[https://bugs.launchpad.net/gdm/+bug/35217/comments/10](https://bugs.launchpad.net/gdm/+bug/35217/comments/10)

Except for the fact that it still isn't working on my computer.

456-437=19, which is under 5%. I bet your disk is reported full because of there's 5% reserved for keeping your "core" system running when users fill up your disks. You can reduce this share with tune2fs command. (Sorry I'm too sleepy to try to find exact parameters, try searching forum, I know there are examples.)

---

### Post by Il Capitano on 2007-08-25
I already went to sleep :-)

But when i woke up and saw your post, i have deleted some more files untill i got above 5%, and it worked!! Thanks a lot

---

