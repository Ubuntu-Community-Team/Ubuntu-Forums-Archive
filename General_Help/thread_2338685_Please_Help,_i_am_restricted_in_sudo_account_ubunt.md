---
title: "Please Help, i am restricted in sudo account ubuntu 16.0.4"
date: 2016-09-30
forum: General Help
---

### Post by heisenburger2 on 2016-09-30
hi all.

i am new to ubuntu and linux and i have ubuntu 16.0.4 installed.

I only had one account on my pc and just single boot ubuntu .

Everything was smooth,until i tried to install open vpn on it, and  trying to make a vpn connection
i made a few other users unknowingly.

after that i uninstalled openvpn and deleted other openvpn accounts. 

now i cant create a document on desktop.
 i get permission denied error

.

i tried to install wine mono , which is in my downloads folder, and i couldnt

so to troubleshoot this i accidentally enabled root and later disabled root account.

then i did this.


```
heisenberg@minibook:~$ sudo ls -l /home
[sudo] password for heisenberg: 
total 4
drwxr-xr-x 28 root root 4096 Sep 30 23:53 heisenberg
heisenberg@minibook:~$
```

i tried to add my username in sudo list in recovery mode and it said i am already sudo.

please help , i am really confused.

---

### Post by deadflowr on 2016-09-30
Being or not being sudo isn't the problem
The problem is your home folder is now somehow owned by root.
It shouldn't be, so you need to re-apply your ownership to it.
easy enough.
Since you know how to get into recovery mode repeat that process, but this time, run
```
chown -R heisenberg:heisenberg /home/heisenberg
```
this changes ownership, the -R runs the command recursively, so the files and folders within the directory also change, the first name is the user and the second is the group. And the the lasst part is the location to change.

Hope it helps.

---

