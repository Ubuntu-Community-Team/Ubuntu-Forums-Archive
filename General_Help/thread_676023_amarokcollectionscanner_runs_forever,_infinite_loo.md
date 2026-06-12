---
title: "amarokcollectionscanner runs forever, infinite loop?"
date: 2008-01-23
forum: General Help
---

### Post by gumpish on 2008-01-23
Hello.

I'm running Gutsy AMD64.

I've tried using both MySQL and Postgresql as backends, but either way once the "Building Collection" progress bar gets 95% of the way done, the process monitor changes from showing activity in the database engine to showing amarokcollectionscanner maxing out the CPU.

I have a modest collection of music (under 5 GB) and left it running for over 2 hours, and it never stopped.
There isn't anything suspicious in the console output, but strace appeared to reveal a problem. Up until it hit the 95% mark the number kept changing but once it hit 95% it was basically this block over and over...

```

ioctl(3, FIONREAD, [0])                 = 0
select(30, [3 4 5 7 9 12 17 18 21 22 23 25 27 28 29], [], [], {0, 15580}) = 0 (Timeout)
write(3, ">\3\7\0\316\5`\4\315\5`\4\276\5`\4\0\0\0\0\0\0\0\0\352"..., 16380) = 16380
write(3, ">\3\7\0\335\1`\4\315\5`\4\276\5`\4\0\0\0\0h\1%\0\4\0\2"..., 5180) = 5180
ioctl(3, FIONREAD, [0])                 = 0
select(30, [3 4 5 7 9 12 17 18 21 22 23 25 27 28 29], [], [], {0, 13780}) = 0 (Timeout)
write(3, ">\3\7\0\316\5`\4\315\5`\4\276\5`\4\0\0\0\0\0\0\0\0\352"..., 16380) = 16380
write(3, ">\3\7\0\335\1`\4\315\5`\4\276\5`\4\0\0\0\0h\1%\0\4\0\2"..., 5180) = 5180
ioctl(3, FIONREAD, [0])                 = 0
select(30, [3 4 5 7 9 12 17 18 21 22 23 25 27 28 29], [], [], {0, 15230}) = 0 (Timeout)
write(3, ">\3\7\0\316\5`\4\315\5`\4\276\5`\4\0\0\0\0\0\0\0\0\352"..., 16380) = 16380
write(3, ">\3\7\0\335\1`\4\315\5`\4\276\5`\4\0\0\0\0h\1%\0\4\0\2"..., 32) = 32
read(3, 0x7fff567f3f80, 32)             = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(3, "\1\2L7\0\0\0\0!\0 \4\0\0\0\0\244\266~\0\0\0\0\0\360\201"..., 32) = 32
write(3, ">\3\7\0\335\1`\4\315\5`\4\276\5`\4\0\0\0\0m\1%\0\4\0\2"..., 5152) = 5152
ioctl(3, FIONREAD, [0])                 = 0
select(30, [3 4 5 7 9 12 17 18 21 22 23 25 27 28 29], [], [], {0, 3904}) = 0 (Timeout)
ioctl(3, FIONREAD, [0])                 = 0
select(30, [3 4 5 7 9 12 17 18 21 22 23 25 27 28 29], [], [], {0, 9727}) = 0 (Timeout)
write(3, ">\3\7\0\316\5`\4\315\5`\4\276\5`\4\0\0\0\0\0\0\0\0\352"..., 16380) = 16380
write(3, ">\3\7\0\335\1`\4\315\5`\4\276\5`\4\0\0\0\0h\1%\0\4\0\2"..., 5180) = 5180
ioctl(3, FIONREAD, [0])                 = 0

```

---

