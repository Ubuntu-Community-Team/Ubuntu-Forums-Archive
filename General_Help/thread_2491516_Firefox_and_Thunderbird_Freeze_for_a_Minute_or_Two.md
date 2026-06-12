---
title: "Firefox and Thunderbird Freeze for a Minute or Two When Trying to Access Any Menu, Me"
date: 2023-10-11
forum: General Help
---

### Post by tk83 on 2023-10-11
**Firefox and Thunderbird Freeze for a Minute or Two When Trying to Access Any Menu, Menus Fail to Load**

Posting here in case it helps anyone since this issue was really frustrating. It made both Firefox and Thunderbird unusable. 

It wasn't anything to do with the usual causes (corrupt profile, delete places DB, refresh Firefox, turn off hardware acceleration) as I troubleshooted with all that and got nowhere. I even created a new Linux user on the same machine with a blank home directory, started firefox (so totally new profile) when logged in as that user and immediately had the same problem.

strace output on Firefox shows:

```
readlink("/run", 0x7ffda95e9ad0, 1023)  = -1 EINVAL (Invalid argument)
readlink("/run/user", 0x7ffda95e9ad0, 1023) = -1 EINVAL (Invalid argument)
readlink("/run/user/1000", 0x7ffda95e9ad0, 1023) = -1 EINVAL (Invalid argument)
readlink("/run/user/1000/pulse", 0x7ffda95e9ad0, 1023) = -1 EINVAL (Invalid argument)
socket(AF_UNIX, SOCK_STREAM|SOCK_CLOEXEC, 0) = 147
fcntl(147, F_GETFD)                     = 0x1 (flags FD_CLOEXEC)
setsockopt(147, SOL_SOCKET, SO_PRIORITY, [6], 4) = 0
fcntl(147, F_GETFL)                     = 0x2 (flags O_RDWR)
fcntl(147, F_SETFL, O_RDWR|O_NONBLOCK)  = 0
connect(147, {sa_family=AF_UNIX, sun_path="/run/user/1000/pulse/native"}, 110) = 0
sendto(96, "W", 1, MSG_NOSIGNAL, NULL, 0) = -1 ENOTSOCK (Socket operation on non-socket)
write(96, "W", 1)                       = 1
write(96, "W", 1)                       = 1
mmap(NULL, 8392704, PROT_NONE, MAP_PRIVATE|MAP_ANONYMOUS|MAP_STACK, -1, 0) = 0x7f7c38fff000
mprotect(0x7f7c39000000, 8388608, PROT_READ|PROT_WRITE) = 0
rt_sigprocmask(SIG_BLOCK, ~[], [], 8)   = 0
clone3({flags=CLONE_VM|CLONE_FS|CLONE_FILES|CLONE_SIGHAND|CLONE_THREAD|CLONE_SYSVSEM|CLONE_SETTLS|CLONE_PARENT_SETTID|CLONE_CHILD_CLEARTID, child_tid=0x7f7c397ff910, parent_tid=0x7f7c397ff910, exit_signal=0, stack=0x7f7c38fff000, stack_size=0x7ffec0, tls=0x7f7c397ff640} => {parent_tid=[30608]}, 88) = 30608
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
futex(0x7f7c4e57b6a0, FUTEX_UNLOCK_PI_PRIVATE) = 0
futex(0x7f7c4e57b6a0, FUTEX_UNLOCK_PI_PRIVATE) = 0
futex(0x7f7c4e57b6a0, FUTEX_UNLOCK_PI_PRIVATE) = 0
futex(0x7f7c4e57b8d8, FUTEX_WAIT_BITSET_PRIVATE|FUTEX_CLOCK_REALTIME, 0, NULL, FUTEX_BITSET_MATCH_ANY
```


Workaround/Fix:
Only happened with Pipewire installed on Ubuntu 22.04. Possibly related to a bad interaction between Pipewire and the likely broken sound hardware on the desktop computer I was using, which hasn't been upgraded since 2016. Didn't happen on a Framework laptop that has the same setup, but that Framework laptop has of course working sound hardware.

Fix was just to remove Pipewire and go back to default Pulseaudio:

```
sudo apt purge pipewire-audio-client-libraries libspa-0.2-bluetooth libspa-0.2-jack wireplumber pipewire-media-session-
sudo rm /etc/alsa/conf.d/99-pipewire-default.conf
sudo apt purge pipewire-pulse
sudo reboot
```

---

