---
title: "I am stuck / cannot log in!?"
date: 2007-04-03
forum: General Help
---

### Post by Joey French on 2007-04-03
Hello, long time Kubuntu user. After a number of updates, it seems that I am now unable to log in anymore. So, I tried my usual tricks such as sudo dpkg reconfigure xserver-xorg, reinstalling packages and so on. No help. So, at this point, I get to a login screen, put in my name and password, it sends me to a black screen, and then back. I can access the root account, and am in recovery mode as I type this. I fiddled with permissions, deleting the ~/.kde/tmp, /socket and /cache files like I have in the past. I am out of ideas, and need my machine up badly.

Anyone have any ideas what to do next?

Joey

---

### Post by taurus on 2007-04-03
What's the output of this command while you are still in the recovery mode?

```
df -h
```

---

### Post by Joey French on 2007-04-03
```
root@cnidaria:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             227G   56G  160G  26% /
varrun                503M   16K  502M   1% /var/run
varlock               503M     0  503M   0% /var/lock
procbususb            503M  104K  502M   1% /proc/bus/usb
udev                  503M  104K  502M   1% /dev
devshm                503M     0  503M   0% /dev/shm
lrm                   503M   13M  490M   3% /lib/modules/2.6.20-13-generic/volatile
root@cnidaria:~#

```

Thanks!
Joey

---

### Post by Joey French on 2007-04-04
I have seen in other threads problems regarding /var/lock(?). Is this what you are referring to? As an aside, I am using my box in recovery mode until I get my problems fixed, is this much of a problem? Thanks again for the help! 

Joey

---

### Post by Joey French on 2007-04-04
Also, it seems that only the root account can log in. I have set up another user, which can't log in either.

---

### Post by Joey French on 2007-04-05
So, to go along with my problem, when I try to login as a regular user from console, I cannot, and it says it cannot "lock" various things??

Anyone have a clue what's going on? I have only been doing regular updates, and don't really know how this problem has arisen. I haven't rebooted in a very long time, so hey, who knows...

Joey French

---

### Post by Joey French on 2007-04-06
Bump? I guess if I don't hear anything by tonight, I will be forced to reinstall...

:( 

Joey French

---

### Post by taurus on 2007-04-06
What's the output of this command from a prompt?

```
ls -la /home
```

---

### Post by Joey French on 2007-04-06
root@cnidaria:~# ls -la /home
total 16
drwx------  4 root  root  4096 2007-04-03 04:55 .
drwxr-xr-x 26 root  root  4096 2007-04-05 22:31 ..
lrwxrwxrwx  1 root  root    44 2007-03-09 23:37 .directory -> /etc/kubuntu-defau                                                 lt-settings/directory-home
drwx------ 69 joey  joey  4096 2007-04-05 19:34 joey
root@cnidaria:~#

---

