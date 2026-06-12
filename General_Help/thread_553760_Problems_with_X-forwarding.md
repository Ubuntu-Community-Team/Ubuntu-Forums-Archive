---
title: "Problems with X-forwarding"
date: 2007-09-18
forum: General Help
---

### Post by tdn on 2007-09-18
I have problems starting Firefox over SSH with X-forwarding.
I have three hosts: A, B and C.
Host A is local to me. 
I SSH with ssh -YC to B.
From B I SSH with ssh-YC to C.
From C I start Firefox.
When nothing happens I strace the Firefox process and get this:

read(4, 0xbffa9bbc, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\"^\7\0\0\0\0M\0\0\0M\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\230"..., 32) = 32
write(4, "\24\0\6\0y\2\300\3\r\2\0\0\37\0\0\0\0\0\0\0\0@\0\0", 24) = 24
read(4, 0xbffa9c9c, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\0_\7\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(4, "\24\0\6\0x\2\300\3\215\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 24) = 24
read(4, 0xbffa9c3c, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\0`\7\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(4, "\17\0\2\0x\2\300\3", 8)       = 8
read(4, 0xbffa9bbc, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\"a\7\0\0\0\0M\0\0\0M\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\230"..., 32) = 32
write(4, "\24\0\6\0x\2\300\3\r\2\0\0\37\0\0\0\0\0\0\0\0@\0\0", 24) = 24
read(4, 0xbffa9c9c, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\0b\7\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(4, "\24\0\6\0e\2\300\3\215\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 24) = 24
read(4, 0xbffa9c3c, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\0c\7\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(4, "\17\0\2\0e\2\300\3", 8)       = 8
read(4, 0xbffa9bbc, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\"d\7\4\0\0\0M\0\0\0M\0\0\0\4\0\0\0\0\0\0\0\0\0\0\0\230"..., 32) = 32
read(4, "f\2\300\3g\2\300\3h\2\300\3i\2\300\3", 16) = 16
write(4, "\24\0\6\0f\2\300\3\215\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 24) = 24
read(4, 0xbffa9bbc, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\0e\7\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(4, "\24\0\6\0g\2\300\3\215\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 24) = 24
read(4, 0xbffa9bbc, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\0f\7\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(4, "\24\0\6\0h\2\300\3\215\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 24) = 24
read(4, 0xbffa9bbc, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\0g\7\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(4, "\24\0\6\0i\2\300\3\215\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 24) = 24
read(4, 0xbffa9bbc, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\0h\7\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(4, "\17\0\2\0f\2\300\3", 8)       = 8
read(4, 0xbffa9b3c, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\"i\7\0\0\0\0M\0\0\0e\2\300\3\0\0\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(4, "\17\0\2\0g\2\300\3", 8)       = 8
read(4, 0xbffa9b3c, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\"j\7\0\0\0\0M\0\0\0e\2\300\3\0\0\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(4, "\17\0\2\0h\2\300\3", 8)       = 8
read(4, 0xbffa9b3c, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\"k\7\0\0\0\0M\0\0\0e\2\300\3\0\0\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(4, "\17\0\2\0i\2\300\3", 8)       = 8
read(4, 0xbffa9b3c, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\"l\7\0\0\0\0M\0\0\0e\2\300\3\0\0\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(4, "\24\0\6\0e\2\300\3\r\2\0\0\37\0\0\0\0\0\0\0\0@\0\0", 24) = 24
read(4, 0xbffa9c9c, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\0m\7\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(4, "\24\0\6\0S\2\300\3\215\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 24) = 24
read(4, 0xbffa9c3c, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\0n\7\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(4, "\17\0\2\0S\2\300\3", 8)       = 8
read(4, 0xbffa9bbc, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\"o\7\1\0\0\0M\0\0\0M\0\0\0\1\0\0\0\0\0\0\0\0\0\0\0\230"..., 32) = 32
read(4, "T\2\300\3", 4)                 = 4
write(4, "\24\0\6\0T\2\300\3\215\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 24) = 24
read(4, 0xbffa9bbc, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\0p\7\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(4, "\17\0\2\0T\2\300\3", 8)       = 8
read(4, 0xbffa9b3c, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\"q\7\n\0\0\0M\0\0\0S\2\300\3\n\0\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
read(4, "U\2\300\3V\2\300\3c\2\300\3v\2\300\3\203\2\300\3\204\2"..., 40) = 40
write(4, "\24\0\6\0U\2\300\3\215\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 24) = 24
read(4, 0xbffa9b3c, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\0r\7\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(4, "\24\0\6\0V\2\300\3\215\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 24) = 24
read(4, 0xbffa9b3c, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\0s\7\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(4, "\24\0\6\0c\2\300\3\215\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 24) = 24
read(4, 0xbffa9b3c, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\0t\7\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(4, "\24\0\6\0v\2\300\3\215\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 24) = 24
read(4, 0xbffa9b3c, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\0u\7\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(4, "\24\0\6\0\203\2\300\3\215\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 24) = 24
read(4, 0xbffa9b3c, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\0v\7\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(4, "\24\0\6\0\204\2\300\3\215\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 24) = 24
read(4, 0xbffa9b3c, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\0w\7\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(4, "\24\0\6\0\214\2\300\3\215\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 24) = 24
read(4, 0xbffa9b3c, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\0x\7\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(4, "\24\0\6\0\215\2\300\3\215\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 24) = 24
read(4, 0xbffa9b3c, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\0y\7\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(4, "\24\0\6\0\225\2\300\3\215\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 24) = 24
read(4, 0xbffa9b3c, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\0z\7\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(4, "\24\0\6\0\226\2\300\3\215\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 24) = 24
read(4, 0xbffa9b3c, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\0{\7\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(4, "\17\0\2\0U\2\300\3", 8)       = 8
read(4, 0xbffa9abc, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\"|\7\0\0\0\0M\0\0\0T\2\300\3\0\0\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(4, "\17\0\2\0V\2\300\3", 8)       = 8
read(4, 0xbffa9abc, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\"}\7\0\0\0\0M\0\0\0T\2\300\3\0\0\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(4, "\17\0\2\0c\2\300\3", 8)       = 8
read(4, 0xbffa9abc, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\"~\7\17\0\0\0M\0\0\0T\2\300\3\17\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
read(4, "X\2\300\3Y\2\300\3Z\2\300\3[\2\300\3\\\2\300\3]\2\300\3"..., 60) = 60
write(4, "\24\0\6\0X\2\300\3\215\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 24) = 24
read(4, 0xbffa9abc, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\0\177\7\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(4, "\24\0\6\0Y\2\300\3\215\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 24) = 24
read(4, 0xbffa9abc, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\0\200\7\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(4, "\24\0\6\0Z\2\300\3\215\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 24) = 24
read(4, 0xbffa9abc, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\0\201\7\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(4, "\24\0\6\0[\2\300\3\215\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 24) = 24
read(4, 0xbffa9abc, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\0\202\7\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(4, "\24\0\6\0\\\2\300\3\215\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 24) = 24
read(4, 0xbffa9abc, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\0\203\7\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(4, "\24\0\6\0]\2\300\3\215\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 24) = 24
read(4, 0xbffa9abc, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\0\204\7\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(4, "\24\0\6\0^\2\300\3\215\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 24) = 24
read(4, 0xbffa9abc, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\0\205\7\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(4, "\24\0\6\0d\2\300\3\215\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 24) = 24
read(4, 0xbffa9abc, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\0\206\7\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(4, "\24\0\6\0{\2\300\3\215\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 24) = 24
read(4, 0xbffa9abc, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\0\207\7\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(4, "\24\0\6\0|\2\300\3\215\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 24) = 24
read(4, 0xbffa9abc, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\0\210\7\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(4, "\24\0\6\0}\2\300\3\215\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 24) = 24
read(4, 0xbffa9abc, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\0\211\7\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(4, "\24\0\6\0~\2\300\3\215\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 24) = 24
read(4, 0xbffa9abc, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\0\212\7\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(4, "\24\0\6\0\177\2\300\3\215\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 24) = 24
read(4, 0xbffa9abc, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\0\213\7\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(4, "\24\0\6\0\201\2\300\3\215\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 24) = 24
read(4, 0xbffa9abc, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\0\214\7\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(4, "\24\0\6\0\202\2\300\3\215\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 24) = 24
read(4, 0xbffa9abc, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\0\215\7\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(4, "\17\0\2\0X\2\300\3", 8)       = 8
read(4, 0xbffa9a3c, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\"\216\7\0\0\0\0M\0\0\0c\2\300\3\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(4, "\17\0\2\0Y\2\300\3", 8)       = 8
read(4, 0xbffa9a3c, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\"\217\7\1\0\0\0M\0\0\0c\2\300\3\1\0\0\0\0\0\0\0\0\0"..., 32) = 32
read(4, "_\2\300\3", 4)                 = 4
write(4, "\24\0\6\0_\2\300\3\215\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 24) = 24
read(4, 0xbffa9a3c, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\0\220\7\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(4, "\17\0\2\0_\2\300\3", 8)       = 8
read(4, 0xbffa99bc, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\"\221\7\0\0\0\0M\0\0\0Y\2\300\3\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(4, "\17\0\2\0Z\2\300\3", 8)       = 8
read(4, 0xbffa9a3c, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\"\222\7\1\0\0\0M\0\0\0c\2\300\3\1\0\0\0\0\0\0\0\0\0"..., 32) = 32
read(4, "\273\5\300\3", 4)              = 4
write(4, "\24\0\6\0\273\5\300\3\215\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 24) = 24
read(4, 0xbffa9a3c, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\0\223\7\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(4, "\17\0\2\0\273\5\300\3", 8)    = 8
read(4, 0xbffa99bc, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\"\224\7\0\0\0\0M\0\0\0Z\2\300\3\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(4, "\17\0\2\0[\2\300\3", 8)       = 8
read(4, 0xbffa9a3c, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\"\225\7\0\0\0\0M\0\0\0c\2\300\3\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(4, "\17\0\2\0\\\2\300\3", 8)      = 8
read(4, 0xbffa9a3c, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\"\226\7\0\0\0\0M\0\0\0c\2\300\3\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(4, "\17\0\2\0]\2\300\3", 8)       = 8
read(4, 0xbffa9a3c, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\"\227\7\0\0\0\0M\0\0\0c\2\300\3\0\0\0\0009\33\f\10\250"..., 32) = 32
write(4, "\17\0\2\0^\2\300\3", 8)       = 8
read(4, 0xbffa9a3c, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\"\230\7\0\0\0\0M\0\0\0c\2\300\3\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(4, "\17\0\2\0d\2\300\3", 8)       = 8
read(4, 0xbffa9a3c, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\"\231\7\1\0\0\0M\0\0\0c\2\300\3\1\0\0\0\0\0\0\0\0\0"..., 32) = 32
read(4, "k\2\300\3", 4)                 = 4
write(4, "\24\0\6\0k\2\300\3\215\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 24) = 24
read(4, 0xbffa9a3c, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\0\232\7\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(4, "\17\0\2\0k\2\300\3", 8)       = 8
read(4, 0xbffa99bc, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\"\233\7\0\0\0\0M\0\0\0d\2\300\3\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(4, "\17\0\2\0{\2\300\3", 8)       = 8
read(4, 0xbffa9a3c, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\"\234\7\0\0\0\0M\0\0\0c\2\300\3\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(4, "\17\0\2\0|\2\300\3", 8)       = 8
read(4, 0xbffa9a3c, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\"\235\7\0\0\0\0M\0\0\0c\2\300\3\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(4, "\17\0\2\0}\2\300\3", 8)       = 8
read(4, 0xbffa9a3c, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\"\236\7\0\0\0\0M\0\0\0c\2\300\3\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(4, "\17\0\2\0~\2\300\3", 8)       = 8
read(4, 0xbffa9a3c, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\"\237\7\0\0\0\0M\0\0\0c\2\300\3\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(4, "\17\0\2\0\177\2\300\3", 8)    = 8
read(4, 0xbffa9a3c, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\"\240\7\0\0\0\0M\0\0\0c\2\300\3\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(4, "\17\0\2\0\201\2\300\3", 8)    = 8
read(4, 0xbffa9a3c, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\"\241\7\0\0\0\0M\0\0\0c\2\300\3\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(4, "\17\0\2\0\202\2\300\3", 8)    = 8
read(4, 0xbffa9a3c, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\"\242\7\0\0\0\0M\0\0\0c\2\300\3\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(4, "\17\0\2\0v\2\300\3", 8)       = 8
read(4, 0xbffa9abc, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(4, "\1\"\243\7\2\0\0\0M\0\0\0T\2\300\3\2\0\0\0\0\0\0\0\0\0"..., 32) = 32
read(4, "\336\2\300\3w\2\300\3", 8)     = 8
write(4, "\24\0\6\0\336\2\300\3\215\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 24) = 24
read(4, 0xbffa9abc, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll( <unfinished ...>
Process 4470 detached

---

### Post by tdn on 2007-09-18
Problem solved.
/proc/4470/fd/4: symbolic link to `/root/.mozilla/firefox/3c913j7e.default/.parentlock'

I deleted the file and started Firefox again.

---

