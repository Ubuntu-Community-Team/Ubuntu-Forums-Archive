---
title: "What are the default groups for user?"
date: 2019-04-02
forum: General Help
---

### Post by warren3 on 2019-04-02
Hi.

I was testing out creating a new group and adding myself.  I must have messed something up as my username was removed from all the groups apart from the test group I had setup.  When I tried to update Lubuntu I was not in the sudoers file.

Anyway I have added myself to sudo so now I need to know what else I should add myself too.  I know one is sambashare but what are the rest?

Cheers.

---

### Post by SeijiSensei on 2019-04-02
Depends entirely on the software you have installed.  For instance, if you use VirtualBox, you'll be assigned to the "vboxusers" group. Look at /etc/group to see.

---

### Post by deadflowr on 2019-04-02
What command did you run to add the user to the new group?
The result posted seems like what happen when you run the usermod command without the -a(append ) flag like
```
sudo usermod -G Groupname Username
```
this wipes out the user's old group listing and starts the user off with a new list.
in order to prevent that you add the flag like
```
sudo usermod -aG Groupname Username
```

---

### Post by warren3 on 2019-04-03
Hi.

I ran 

```
sudo usermod -G Groupname Username
```

I read in a book that was safe and it was -g that was unsafe.  Perhaps not.  

My installation is pretty much stock with no added software.  So what groups should I add myself to?

---

### Post by deadflowr on 2019-04-03
Add sudo and you (you = you're user which should have a groupname) to start.
others would be plugdev adm dip lpadmin cdrom.

Unfortunately you need to do this from recovery mode.
And you need to reset recovery mode to read/write, it defaults to read-only so any chnages set without resetting r/w will be lost and reboot.
in recovery mode run
```
mount -o remount,rw /
```
that should reset to r/w.


Edit: remembered this:
[https://askubuntu.com/questions/219083/default-groups-for-user-in-ubuntu]("https://askubuntu.com/questions/219083/default-groups-for-user-in-ubuntu")

---

