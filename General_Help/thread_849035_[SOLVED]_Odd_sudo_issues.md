---
title: "[SOLVED] Odd sudo issues"
date: 2008-07-04
forum: General Help
---

### Post by Plasma_NZ on 2008-07-04
Ok just noticed something odd happeing..

Commands like "sudo gedit" respond with nothing, gedit doesnt launch..

"sudo nautilus" takes agesto load and even then it doesnt load correctly,

Makin it extremely hard to edit anything, and i dont like using nano, which 

seems to not be effected..


Anyone got and ideas why this is happening or howto fix it.?

---

### Post by kornhead127 on 2008-07-04
Try using gksudo for graphical apps.

---

### Post by Plasma_NZ on 2008-07-04
> **kornhead127 said:**
> Try using gksudo for graphical apps.

makes no difference.. nothings opeing in gedit with the sudo in front..

same goes for gksudo on things like nautilus or anything else..

---

### Post by iaculallad on 2008-07-04
Let's try to trace the application when it's running:

Open your terminal and issue the two commands below, one-at-a-time:

```
sudo -s
strace gedit
```

When the gedit window hangs, copy the last line of texts on your strace window and try to post it. This might help.

---

### Post by Plasma_NZ on 2008-07-04
well it filled my terminal buffer completely..

but here's a small portion, i had to ctrl + c cause it just hung..


```
lseek(15, 0, SEEK_SET)                  = 0
read(15, "Xcur\20\0\0\0\0\0\1\0\3\0\0\0\2\0\375\377\30\0\0\0004\0"..., 4096) = 4096
close(15)                               = 0
munmap(0x7f175c223000, 4096)            = 0
select(4, [3], [3], NULL, NULL)         = 1 (out [3])
writev(3, [{"\201\2\5\0\0\0@\2J\0@\2\0\0\0\0\0\0\0\0\201\2\5\0\0\0@"..., 3384}], 1) = 3384
select(4, [3], [], NULL, NULL)          = 1 (in [3])
read(3, "\23\0r\1=\0@\2=\0@\2\0\177\0\0x\33\177\0\0\0\0\0\0\0\0"..., 4096) = 300
read(3, 0x6d0d04, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
select(4, [3], [3], NULL, NULL)         = 1 (out [3])
writev(3, [{"\2\0\4\0\36\0@\2\0\10\0\0\363\200b\0\f\0\4\0U\0@\2@\0\0"..., 108}], 1) = 108
select(4, [3], [], NULL, NULL)          = 1 (in [3])
read(3, "\23\0&\2U\0@\2U\0@\2\0\177\0\0x\33\177\0\0\0\0\0\0\0\0"..., 4096) = 108
read(3, 0x6d0d04, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
open("/home/physics/.icons/DMZ-Black/cursors/bottom_right_corner", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/home/physics/.icons/DMZ-Black/index.theme", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/icons/DMZ-Black/cursors/bottom_right_corner", O_RDONLY) = 15
fstat(15, {st_mode=S_IFREG|0644, st_size=15776, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f175c223000
read(15, "Xcur\20\0\0\0\0\0\1\0\3\0\0\0\2\0\375\377\30\0\0\0004\0"..., 4096) = 4096
lseek(15, 0, SEEK_SET)                  = 0
read(15, "Xcur\20\0\0\0\0\0\1\0\3\0\0\0\2\0\375\377\30\0\0\0004\0"..., 4096) = 4096
close(15)                               = 0
munmap(0x7f175c223000, 4096)            = 0
getuid()                                = 0
access("/tmp/.esd-0/socket", R_OK|W_OK) = -1 ENOENT (No such file or directory)
socket(PF_INET6, SOCK_STREAM, IPPROTO_IP) = 15
close(15)                               = 0
socket(PF_NETLINK, SOCK_RAW, 0)         = 15
bind(15, {sa_family=AF_NETLINK, pid=0, groups=00000000}, 12) = 0
getsockname(15, {sa_family=AF_NETLINK, pid=7568, groups=00000000}, [7224338126645231628]) = 0
sendto(15, "\24\0\0\0\26\0\1\3R\311mH\0\0\0\0\0\0\0\0", 20, 0, {sa_family=AF_NETLINK, pid=0, groups=00000000}, 12) = 20
recvmsg(15, {msg_name(12)={sa_family=AF_NETLINK, pid=0, groups=00000000}, msg_iov(1)=[{"<\0\0\0\24\0\2\0R\311mH\220\35\0\0\2\30\200\0\2\0\0\0\10"..., 4096}], msg_controllen=0, msg_flags=0}, 0) = 60
recvmsg(15, {msg_name(12)={sa_family=AF_NETLINK, pid=0, groups=00000000}, msg_iov(1)=[{"@\0\0\0\24\0\2\0R\311mH\220\35\0\0\n@\200\375\2\0\0\0\24"..., 4096}], msg_controllen=0, msg_flags=0}, 0) = 64
recvmsg(15, {msg_name(12)={sa_family=AF_NETLINK, pid=0, groups=00000000}, msg_iov(1)=[{"\24\0\0\0\3\0\2\0R\311mH\220\35\0\0\0\0\0\0\2\0\0\0\24"..., 4096}], msg_controllen=0, msg_flags=0}, 0) = 20
close(15)                               = 0
socket(PF_FILE, SOCK_STREAM, 0)         = 15
fcntl(15, F_SETFL, O_RDWR|O_NONBLOCK)   = 0
connect(15, {sa_family=AF_FILE, path="/var/run/nscd/socket"}, 110) = -1 ENOENT (No such file or directory)
close(15)                               = 0
socket(PF_FILE, SOCK_STREAM, 0)         = 15
fcntl(15, F_SETFL, O_RDWR|O_NONBLOCK)   = 0
connect(15, {sa_family=AF_FILE, path="/var/run/nscd/socket"}, 110) = -1 ENOENT (No such file or directory)
close(15)                               = 0
open("/etc/resolv.conf", O_RDONLY)      = 15
fstat(15, {st_mode=S_IFREG|0644, st_size=23, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f175c223000
read(15, "nameserver 192.168.0.1\n", 4096) = 23
read(15, "", 4096)                      = 0
close(15)                               = 0
munmap(0x7f175c223000, 4096)            = 0
uname({sys="Linux", node="physics", ...}) = 0
open("/etc/hosts", O_RDONLY|0x80000 /* O_??? */) = 15
fcntl(15, F_GETFD)                      = 0x1 (flags FD_CLOEXEC)
fstat(15, {st_mode=S_IFREG|0644, st_size=239, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f175c223000
read(15, "127.0.0.1 localhost\n127.0.1.1 ph"..., 4096) = 239
close(15)                               = 0
munmap(0x7f175c223000, 4096)            = 0
socket(PF_INET, SOCK_STREAM, IPPROTO_IP) = 15
fcntl(15, F_SETFD, FD_CLOEXEC)          = 0
setsockopt(15, SOL_SOCKET, SO_REUSEADDR, [1], 4) = 0
connect(15, {sa_family=AF_INET, sin_port=htons(16001), sin_addr=inet_addr("127.0.0.1")}, 16 <unfinished ...>

```

---

### Post by Plasma_NZ on 2008-07-04
I've tried re-installing gedit - problem still persists..

---

### Post by nikgare on 2008-07-04
Do the commends work with out **sudo** - ie is it a sudo problem?

---

### Post by Plasma_NZ on 2008-07-04
Problem fixed..

I had edited the /etc/network/interfaces - and added a incorrect line which had adverse effects..

Since have fixed it and everything if working fine now..

Ta for the help guys..

---

