---
title: "Mixxx segfault"
date: 2005-07-30
forum: General Help
---

### Post by SherlokK on 2005-07-30
Hi !

I would need some help because I've been trying to use Mixxx (DJ software, [http://mixxx.sourceforge.net/)](http://mixxx.sourceforge.net/)), but I always have segfaults during its initialisation :(

I didn't find any package, so I tried to install it from the binaries and from the sources available on the mixxx website. I use Hoary.

I tried to build it with and without jack support.

But I always have this segfault :

```
yannick@shagshag:~/mixxx-1.4.2$ mixxx
Debug: Starting up...
Debug: MidiObjectOSS: Open of MIDI device /dev/midi failed.
Debug: Alsa getapi
Debug: Track: /home/yannick/.mixxxtrack.xml does not exists.
Debug: MidiObjectOSS: Open of MIDI device /dev/midi failed.
Debug: id 0, sr 96000, ch 2, bufsize 16, bufno 120
Erreur de segmentation
```

Anyone would have an idea ?

---

### Post by SherlokK on 2005-07-31
Here is what I get with a strace, from the last line written to the standard output (Debug: id 0, sr 96000, ch 2, ....) :

```
write(2, "Debug: id 0, sr 96000, ch 2, buf"..., 51Debug: id 0, sr 96000, ch 2, bufsize 16, bufno 120
) = 51
open("/dev/dsp", O_WRONLY|O_NONBLOCK)   = 7
close(7)                                = 0
open("/dev/dsp", O_WRONLY)              = 7
ioctl(7, SNDCTL_DSP_SETFRAGMENT, 0xbffff618) = 0
ioctl(7, SNDCTL_DSP_SETFMT or SOUND_PCM_READ_BITS, 0xbffff618) = 0
ioctl(7, SOUND_PCM_READ_CHANNELS, 0xbffff634) = 0
ioctl(7, SNDCTL_DSP_SPEED or SOUND_PCM_READ_RATE, 0xbffff618) = 0
mmap2(NULL, 8392704, PROT_READ|PROT_WRITE|PROT_EXEC, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb4477000
mprotect(0xb4477000, 4096, PROT_NONE)   = 0
clone(child_stack=0xb4c77b28, flags=CLONE_VM|CLONE_FS|CLONE_FILES|CLONE_SIGHAND|CLONE_THREAD|CLONE_SYSVSEM|CLONE_SETTLS|CLONE_PARENT_SETTID|CLONE_CHILD_CLEARTID|CLONE_DETACHED, parent_tidptr=0xb4c77bf8, {entry_number:6, base_addr:0xb4c77bb0, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}, child_tidptr=0xb4c77bf8) = 18604
socket(PF_INET, SOCK_STREAM, IPPROTO_IP) = 8
getsockname(8, {sa_family=AF_INET, sin_port=htons(0), sin_addr=inet_addr("0.0.0.0")}, [16]) = 0
getpeername(8, 0xbffff620, [128])       = -1 ENOTCONN (Transport endpoint is not connected)
setsockopt(8, SOL_SOCKET, SO_REUSEADDR, [1], 4) = 0
bind(8, {sa_family=AF_INET, sin_port=htons(33033), sin_addr=inet_addr("127.0.0.1")}, 16) = 0
getsockname(8, {sa_family=AF_INET, sin_port=htons(33033), sin_addr=inet_addr("127.0.0.1")}, [16]) = 0
getpeername(8, 0xbffff5e0, [128])       = -1 ENOTCONN (Transport endpoint is not connected)
listen(8, 1)                            = 0
ioctl(5, FIONREAD, [1])                 = 0
ioctl(5, FIONREAD, [1])                 = 0
futex(0x81e4d9c, FUTEX_WAKE, 1)         = 1
futex(0x81e4dbc, FUTEX_WAKE, 1)         = 1
ioctl(5, FIONREAD, [1])                 = 0
ioctl(5, FIONREAD, [1])                 = 0
ioctl(5, FIONREAD, [1])                 = 0
ioctl(5, FIONREAD, [1])                 = 0
ioctl(5, FIONREAD, [1])                 = 0
ioctl(5, FIONREAD, [1])                 = 0
ioctl(5, FIONREAD, [1])                 = 0
futex(0x81e4d9c, FUTEX_WAKE, 1)         = 1
futex(0x81e4dbc, FUTEX_WAKE, 1)         = 1
ioctl(5, FIONREAD, [1])                 = 0
ioctl(5, FIONREAD, [1])                 = 0
ioctl(5, FIONREAD, [1])                 = 0
ioctl(5, FIONREAD, [1])                 = 0
ioctl(5, FIONREAD, [1])                 = 0
ioctl(5, FIONREAD, [1])                 = 0
ioctl(5, FIONREAD, [1])                 = 0
ioctl(5, FIONREAD, [1])                 = 0
gettimeofday({1122804484, 871748}, NULL) = 0
ioctl(5, FIONREAD, [1])                 = 0
ioctl(5, FIONREAD, [1])                 = 0
gettimeofday({1122804484, 883275}, NULL) = 0
ioctl(5, FIONREAD, [1])                 = 0
ioctl(5, FIONREAD, [1])                 = 0
gettimeofday({1122804484, 893036}, NULL) = 0
ioctl(5, FIONREAD, [1])                 = 0
ioctl(5, FIONREAD, [1])                 = 0
gettimeofday({1122804484, 901455}, NULL) = 0
ioctl(5, FIONREAD, [1])                 = 0
ioctl(5, FIONREAD, [1])                 = 0
gettimeofday({1122804484, 901912}, NULL) = 0
gettimeofday({1122804484, 959304}, NULL) = 0
--- SIGSEGV (Segmentation fault) @ 0 (0) ---

```

---

### Post by SherlokK on 2005-08-02
I was told that the ioctl calls could be related to problems on rights on the sound devices in /dev so I changed them (/dev/midi and /dev/snd/*) to the group audio, in which I am too.

I don't have /dev/midi errors anymore, but I still have the same segfault issue :(

---

