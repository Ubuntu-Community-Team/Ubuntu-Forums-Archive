---
title: "/var/log/acpid file size: 2 GB"
date: 2007-12-29
forum: General Help
---

### Post by hexion on 2007-12-29
No matter how many times I delete that file, 3 or 4 days after that its size is again 2 GB.

This lines repeats in the whole file:
```
[Thu Dec 27 20:48:51 2007] ERR: can't accept client: Too many open files
[Thu Dec 27 20:48:51 2007] ERR: can't accept client: Too many open files
[Thu Dec 27 20:48:51 2007] ERR: can't accept client: Too many open files
[Thu Dec 27 20:48:51 2007] ERR: can't accept client: Too many open files
[Thu Dec 27 20:48:51 2007] ERR: can't accept client: Too many open files
```Note, all the dates are exactly the same. From the line 6500 to 2 GB there's only 7 minutes!!!!.

```
$ head -n 6500 acpid
[Thu Dec 27 20:31:58 2007] client connected from 25218[1000:1000]
[Thu Dec 27 20:31:58 2007] 1 client rule loaded
[Thu Dec 27 20:31:58 2007] client connected from 25219[1000:1000]
[Thu Dec 27 20:31:58 2007] 1 client rule loaded
[Thu Dec 27 20:36:58 2007] client connected from 25278[1000:1000]
[Thu Dec 27 20:36:58 2007] 1 client rule loaded
[Thu Dec 27 20:36:58 2007] client connected from 25279[1000:1000]
[Thu Dec 27 20:36:58 2007] 1 client rule loaded
[Thu Dec 27 20:36:58 2007] client connected from 25280[1000:1000]
[Thu Dec 27 20:36:58 2007] 1 client rule loaded
[Thu Dec 27 20:36:58 2007] client connected from 25281[1000:1000]
[Thu Dec 27 20:36:58 2007] 1 client rule loaded
[Thu Dec 27 20:36:58 2007] client connected from 25282[1000:1000]
[Thu Dec 27 20:36:58 2007] 1 client rule loaded
[Thu Dec 27 20:41:58 2007] client connected from 25309[1000:1000]
[Thu Dec 27 20:41:58 2007] 1 client rule loaded
[Thu Dec 27 20:41:58 2007] client connected from 25310[1000:1000]
[Thu Dec 27 20:41:58 2007] 1 client rule loaded
[Thu Dec 27 20:41:58 2007] client connected from 25311[1000:1000]
[Thu Dec 27 20:41:58 2007] 1 client rule loaded
[Thu Dec 27 20:41:58 2007] client connected from 25312[1000:1000]
[Thu Dec 27 20:41:58 2007] 1 client rule loaded
[Thu Dec 27 20:41:58 2007] ERR: can't accept client: Too many open files
[Thu Dec 27 20:41:58 2007] ERR: can't accept client: Too many open files
[Thu Dec 27 20:41:58 2007] ERR: can't accept client: Too many open files
[Thu Dec 27 20:41:58 2007] ERR: can't accept client: Too many open files
[Thu Dec 27 20:41:58 2007] ERR: can't accept client: Too many open files
[Thu Dec 27 20:41:58 2007] ERR: can't accept client: Too many open files

```When the file reaches 2 GB it stops logging, but this time I wont delete it since I suspect this issue is related to certain kernel freezes I've been having since Edgy.

```
/var/log$ ls -lh acpid 
-rw-r----- 1 root adm 2,0G 2007-12-27 20:48 acpid 
```



Any idea about what's happening in my Gutsy box?

---

### Post by Keith_Beef on 2007-12-29
Are you running Gutsy on a laptop?

Try reading the man page for acpi and looking in your /etc/acpi/events directory for configuration files that match your hardware.

When I look in my own /var/log/acpid file, I only see a few lines at each startup:

```
[Sat Dec 29 09:38:13 2007] starting up
[Sat Dec 29 09:38:13 2007] 72 rules loaded
[Sat Dec 29 09:38:14 2007] client connected from 5888[107:116]
[Sat Dec 29 09:38:14 2007] 1 client rule loaded
[Sat Dec 29 09:38:18 2007] client connected from 6343[0:0]
[Sat Dec 29 09:38:18 2007] 1 client rule loaded
[Sat Dec 29 09:38:20 2007] client connected from 6343[0:0]
[Sat Dec 29 09:38:20 2007] 1 client rule loaded
```

The start of your own file should look similar, and show how many configuration files are being read.


Beef.

---

### Post by hexion on 2007-12-29
No, it's a desktop.

Here's the starting of that file:

```
# head -n 10 acpid 
[Mon Dec 24 17:19:36 2007] starting up
[Mon Dec 24 17:19:36 2007] 74 rules loaded
[Mon Dec 24 17:19:37 2007] client connected from 5355[106:110]
[Mon Dec 24 17:19:37 2007] 1 client rule loaded
[Mon Dec 24 17:19:40 2007] client connected from 5391[0:0]
[Mon Dec 24 17:19:40 2007] 1 client rule loaded
[Mon Dec 24 17:19:42 2007] client connected from 5443[0:0]
[Mon Dec 24 17:19:42 2007] 1 client rule loaded
[Mon Dec 24 17:19:47 2007] client connected from 5614[0:0]
[Mon Dec 24 17:19:47 2007] 1 client rule loaded
```


I've been reading, and now I'm playing with bum (boot up manager).
Should I deactive "laptop-mode" and "acpi-support"?

---

### Post by hexion on 2007-12-29
No can do...
After deleting (again) that file, my system keeps doing the same:
Exactly each 5 minutes, new clients (of whatever they are clients) are connected. That will keep happening until certain limit is reached, and then the file will be flooded until it will reach 2 GB size.

```
[Sat Dec 29 18:00:30 2007] starting up
[Sat Dec 29 18:00:30 2007] 74 rules loaded
[Sat Dec 29 18:00:33 2007] client connected from 5394[106:110]
[Sat Dec 29 18:00:33 2007] 1 client rule loaded
[Sat Dec 29 18:00:34 2007] client connected from 5411[0:0]
[Sat Dec 29 18:00:34 2007] 1 client rule loaded
[Sat Dec 29 18:00:36 2007] client connected from 5467[0:0]
[Sat Dec 29 18:00:36 2007] 1 client rule loaded
[Sat Dec 29 18:00:40 2007] client connected from 5634[0:0]
[Sat Dec 29 18:00:40 2007] 1 client rule loaded
[Sat Dec 29 18:01:09 2007] client connected from 6464[1000:1000]
[Sat Dec 29 18:01:09 2007] 1 client rule loaded
[Sat Dec 29 18:01:09 2007] client connected from 6465[1000:1000]
[Sat Dec 29 18:01:09 2007] 1 client rule loaded
[Sat Dec 29 18:01:09 2007] client connected from 6466[1000:1000]
[Sat Dec 29 18:01:09 2007] 1 client rule loaded
[Sat Dec 29 18:01:09 2007] client connected from 6467[1000:1000]
[Sat Dec 29 18:01:09 2007] 1 client rule loaded
[Sat Dec 29 18:01:09 2007] client connected from 6468[1000:1000]
[Sat Dec 29 18:01:09 2007] 1 client rule loaded
[Sat Dec 29 18:06:09 2007] client connected from 7169[1000:1000]
[Sat Dec 29 18:06:09 2007] 1 client rule loaded
[Sat Dec 29 18:06:09 2007] client connected from 7170[1000:1000]
[Sat Dec 29 18:06:09 2007] 1 client rule loaded
[Sat Dec 29 18:06:09 2007] client connected from 7171[1000:1000]
[Sat Dec 29 18:06:09 2007] 1 client rule loaded
[Sat Dec 29 18:06:09 2007] client connected from 7172[1000:1000]
[Sat Dec 29 18:06:09 2007] 1 client rule loaded
[Sat Dec 29 18:06:09 2007] client connected from 7173[1000:1000]
[Sat Dec 29 18:06:09 2007] 1 client rule loaded
[Sat Dec 29 18:11:09 2007] client connected from 7658[1000:1000]
[Sat Dec 29 18:11:09 2007] 1 client rule loaded
[Sat Dec 29 18:11:09 2007] client connected from 7659[1000:1000]
[Sat Dec 29 18:11:09 2007] 1 client rule loaded
[Sat Dec 29 18:11:09 2007] client connected from 7660[1000:1000]

```

I think I will have to deactive acpid itself unless someone knows what's happening here :(

---

### Post by Keith_Beef on 2007-12-29
I really don't know what's going on here...

I don't understand why you are getting so many "clients" connecting.

From looking at the man pages, I thought that you'd get a client for each of the shell scripts activated (these are in /etc/acpi/) by the config files (in /etc/acpi/events/).

From reading man acpid again, I think that maybe other apps are connecting to the acpi daemon... 

What could be causing that?

UPS? Watchdog card?

Beef.

---

### Post by ghostdog74 on 2007-12-29
search for  the /etc/init.d/acpid (or elsewhere) and open the file
at the line where it says $ACPID_BIN=/sbin/acpid (or at the case, esac for "start")
change it to 
```

$ACPID_BIN=/sbin/acpid -l /dev/null

```

---

### Post by hexion on 2007-12-30
> **ghostdog74 said:**
> search for  the /etc/init.d/acpid (or elsewhere) and open the file
at the line where it says $ACPID_BIN=/sbin/acpid (or at the case, esac for "start")
change it to 
```

$ACPID_BIN=/sbin/acpid -l /dev/null

```

That would make acpid not to log so it will solve my file problem, but I still wont know why each 5 minutes some clients try to connect to the acpi daemon :(

I have no idea what's happening.. it's not a fresh install and I've tuned some things, but I've never touched anything relative to this problem.
Anyway, I have deactived the acpi daemon with bum (bootup manager) and nothing seems to fail since then. I thought my athlon power management wouldn't work without acpi but I cannot find anything not working without it..

Thank you both for your help :)

---

### Post by ghostdog74 on 2007-12-30
> **hexion said:**
> That would make acpid not to log so it will solve my file problem, but I still wont know why each 5 minutes some clients try to connect to the acpi daemon :(

I have no idea what's happening.. it's not a fresh install and I've tuned some things, but I've never touched anything relative to this problem.
Anyway, I have deactived the acpi daemon with bum (bootup manager) and nothing seems to fail since then. I thought my athlon power management wouldn't work without acpi but I cannot find anything not working without it..

Thank you both for your help :)

another possible solution is to look for a newer version of acpid , if there is, and install it. ie upgrading. well I leave it to you then.

---

### Post by hexion on 2007-12-30
I know that sometimes works, but considering I have this problem since Edgy, I don't think that upgrading is the solution. The version of acpid has changed a couple of times since Edgy to Gutsy.

---

