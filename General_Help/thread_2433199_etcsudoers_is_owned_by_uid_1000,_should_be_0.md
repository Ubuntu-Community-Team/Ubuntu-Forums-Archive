---
title: "/etc/sudoers is owned by uid 1000, should be 0"
date: 2019-12-15
forum: General Help
---

### Post by ejr32123 on 2019-12-15
hello!

Now sure why this is happening. All I did was update my computer after rebooting, I get errors when trying to use sudo. How can I just randomly use those privileges? This is the second time it happened to me. The first time I just reinstalled (Because it was a fresh install of ubuntu)  and I wasn't sure what to do. Everytime I use sudo it says:  
sudo: /etc/sudoers is owned by uid 1000, should be 0
sudo: no valid sudoers sources found, quitting
sudo: unable to initialize policy plugin
any help would be amazing, thanks

edit, I did see some other posts like this, but the solutions either didn't work or i didn't understand what to do.

edit 2, I used the command chown recursively for /etc because I needed to access a file there to which I didn't have permission. Could that have caused the problem?

---

### Post by CatKiller on 2019-12-15
> **ejr32123 said:**
> I used the command chown recursively for /etc because I needed to access a file there to which I didn't have permission. Could that have caused the problem?

That's exactly what caused it. The only fix is a reinstall. Don't do it again.

---

### Post by ejr32123 on 2019-12-15
RIP :( well, thanks. Next time, if I need to have permission to access a folder/file I cant, which command should I use?

---

### Post by CatKiller on 2019-12-15
[https://www.howtoforge.com/tutorial/sudo-beginners-guide/](https://www.howtoforge.com/tutorial/sudo-beginners-guide/)

---

### Post by sisco311 on 2019-12-15
Next time when you need to do something as root use sudo:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

You can still make your installation functional. Most of the files in /etc must be owned by root:root. In theory you should be able to use pkexec (a command similar to sudo) to fix the issue:
```
pkexec chown -R root:root /etc
```

If you can't use pkexec you can boot into recovery mode to fix the ownership of the files or boot into a live cd/usb mount the partition and fix the problem.

---

### Post by The Cog on 2019-12-15
> **CatKiller said:**
> That's exactly what caused it. The only fix is a reinstall. Don't do it again.
CatKiller's reply is blunt but absolutely correct. The damage to the permissions system is pretty-much impossible to undo, and reinstalling is the only safe way to go. This is because of the number of files that have special permissions and ownerships - individually finding and fixing them all would take days. If /home is on a separate partition then you can probably reinstall without affecting the user settings (don't reformat it). If it's all one partition then take a backup of /home before reinstalling so you can restore it afterwards.  But a backup would be a good idea anyway. You will probally have to use a live installer USB (or boot into single-user mode) to take the backup because you can't sudo any more.

In future, remember you can use sudo to gain root privileges when needed (I often do "sudo -i" in a command prompt and do my work as root before exiting that terminal) - you don't need to try to subvert the system permissions. This comes down to understanding the difference between being a user and being an admin, and becoming an admin only when cecessary. Recent Windows has started to have the same kind of role separation, with a "run as administrator" option. But it doesn't come naturally to long-time windows users.

---

### Post by ejr32123 on 2019-12-15
hey, thanks everyone for the replies! all very helpful.

---

