---
title: "Thunderbird 78 now crashes on startup"
date: 2021-09-20
forum: General Help
---

### Post by pabc on 2021-09-20
18.04.06 LTS fully updated.

I get the crash reporter when starting thunderbird from gnome.

from the command line i get:

[12130, Main Thread] WARNING: failed to open shm: Permission denied: file /build/thunderbird-xTXOo3/thunderbird-78.13.0+build1/ipc/chromium/src/base/shared_memory_posix.cc, line 246
ExceptionHandler::GenerateDump cloned child 12146
ExceptionHandler::SendContinueSignalToChild sent continue signal to child
ExceptionHandler::WaitForContinueSignal waiting for continue signal...


then when I close the crash reporter:

phil@phil-desktop:~$ Failed to open curl lib from binary, use libcurl.so instead




I've apt purged and reinstalled, removed the .thunderbird folder and no change. I'm a bit stumped.,

Any ideas?

---

### Post by vanadium on 2021-09-20
What does "which thunderbird" and "file $(which thunderbird)" reveal? Just to double check whether you do not have another instance of thunderbird installed in another way.

---

### Post by ActionParsnip on 2021-09-20
> **vanadium said:**
> What does "which thunderbird" and "file $(which thunderbird)" reveal? Just to double check whether you do not have another instance of thunderbird installed in another way.

I'm suspecting an "install" by extracting the tarball....let's see

---

### Post by TheFu on 2021-09-20
78.13.0  crashed on me today with an out of memory error, which I've never seen before.  The suggested RAM for the system is listed as 512MB.  The system has 4G and 'free' said just a little over 1G was being used at the time.  The system is stable and still running:
```
$ free -h
              total        used        free      shared  buff/cache   available
Mem:          3.8Gi       701Mi       1.2Gi       8.0Mi       1.9Gi       2.9Gi
Swap:         4.1Gi          0B       4.1Gi

```

I run thunderbird on a 20.04 system inside a firejail with memory constraints (3.7G limit), using X11 forwarded through an ssh connection to an 18.04 server with a lite-window manager, fvwm.  It refused to startup with a 3.5G RAM limit.  After the OOM error, I bumped the RAM limit to 4.7G and restarted.  Here's the process table entry:
```
tf        357708  357700  0 09:52 ?        00:00:00 /usr/bin/firejail --dns=172.22.22.80 --rlimit-as=4700000000 /usr/bin/thunderbird -no-remote
```

Only posting because it happened just a few minutes before I saw this thread.  May or may not be related.  I only have the Canonical repo version of thunderbird.
On another system here, 18.04, I run TB locally and haven't seen the same issue - or any others recently. It also runs inside a memory constrained firejail.
```
tf        4265  4264  0 07:50 ?        00:00:00 /usr/bin/firejail --dns=172.22.22.80 --rlimit-as=3700000000 /usr/bin/thunderbird -no-remote
```
rlimit is just a limit on virtual memory.

---

### Post by pabc on 2021-09-21
sudo apt-get purge thunderbird
rm -rf ~/.thunderbird
sudo apt-get install thunderbird

no tarball in site.

---

### Post by pabc on 2021-09-21
/usr/bin/thunderbird

/usr/bin/thunderbird: symbolic link to ../lib/thunderbird/thunderbird.sh

---

