---
title: "amarok suddently stopped working with my user"
date: 2005-04-25
forum: General Help
---

### Post by negatory on 2005-04-25
Amarok just doesn't work with my current user, if I switch to another user it works properly but not with mine.I've tryed reinstalling but no luck there.I've removed ~/.kde/share/apps/amarok and ~/.kde/share/config/amarok and still no luck.I've removed every trace of amarok files from my system and reinstalled it but it still doesn't start! It was working properly and now it just doesn't start.

strace says:
```
~$ strace amarok
execve("/usr/bin/amarok", ["amarok"], [/* 30 vars */]) = 0
uname({sys="Linux", node="matrix", ...}) = 0
brk(0)                                  = 0x50a000
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2a9556a000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2a9556b000
open("/etc/ld.so.preload", O_RDONLY)    = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=66798, ...}) = 0
mmap(NULL, 66798, PROT_READ, MAP_PRIVATE, 3, 0) = 0x2a9556d000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libqt-mt.so.3", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\0\270(\0"..., 640) = 640
fstat(3, {st_mode=S_IFREG|0644, st_size=8429616, ...}) = 0
mmap(NULL, 9500336, PROT_READ|PROT_EXEC, MAP_PRIVATE, 3, 0) = 0x2a9566c000
mprotect(0x2a95d72000, 2135728, PROT_NONE) = 0
mmap(0x2a95e6c000, 1089536, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED, 3, 0x700000) = 0x2a95e6c000
mmap(0x2a95f76000, 22192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x2a95f76000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libpng12.so.0", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\0|\0\0\0"..., 640) = 640
fstat(3, {st_mode=S_IFREG|0644, st_size=159064, ...}) = 0
mmap(NULL, 1205920, PROT_READ|PROT_EXEC, MAP_PRIVATE, 3, 0) = 0x2a95f7c000
mprotect(0x2a95f9f000, 1062560, PROT_NONE) = 0
mmap(0x2a9607c000, 159744, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED, 3, 0) = 0x2a9607c000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libz.so.1", O_RDONLY)    = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\200!\0\0"..., 640) = 640
fstat(3, {st_mode=S_IFREG|0644, st_size=80872, ...}) = 0
mmap(NULL, 1127808, PROT_READ|PROT_EXEC, MAP_PRIVATE, 3, 0) = 0x2a960a3000
mprotect(0x2a960b6000, 1049984, PROT_NONE) = 0
mmap(0x2a961a3000, 81920, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED, 3, 0) = 0x2a961a3000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/X11R6/lib/libXext.so.6", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\0009\0\0"..., 640) = 640
fstat(3, {st_mode=S_IFREG|0644, st_size=67312, ...}) = 0
mmap(NULL, 1114856, PROT_READ|PROT_EXEC, MAP_PRIVATE, 3, 0) = 0x2a961b7000
mprotect(0x2a961c5000, 1057512, PROT_NONE) = 0
mmap(0x2a962b7000, 69632, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED, 3, 0) = 0x2a962b7000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/X11R6/lib/libX11.so.6", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\200\227"..., 640) = 640
fstat(3, {st_mode=S_IFREG|0644, st_size=908400, ...}) = 0
mmap(NULL, 1957120, PROT_READ|PROT_EXEC, MAP_PRIVATE, 3, 0) = 0x2a962c8000
mprotect(0x2a96392000, 1129728, PROT_NONE) = 0
mmap(0x2a963c8000, 909312, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED, 3, 0) = 0x2a963c8000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/X11R6/lib/libSM.so.6", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0@<\0\0\0"..., 640) = 640
fstat(3, {st_mode=S_IFREG|0644, st_size=41536, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2a964a6000
mmap(NULL, 1088496, PROT_READ|PROT_EXEC, MAP_PRIVATE, 3, 0) = 0x2a964a7000
mprotect(0x2a964b0000, 1051632, PROT_NONE) = 0
mmap(0x2a965a7000, 40960, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED, 3, 0) = 0x2a965a7000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/X11R6/lib/libICE.so.6", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\0R\0\0\0"..., 640) = 640
fstat(3, {st_mode=S_IFREG|0644, st_size=96880, ...}) = 0
mmap(NULL, 1158368, PROT_READ|PROT_EXEC, MAP_PRIVATE, 3, 0) = 0x2a965b1000
mprotect(0x2a965c6000, 1072352, PROT_NONE) = 0
mmap(0x2a966b1000, 98304, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED, 3, 0) = 0x2a966b1000
mmap(0x2a966c9000, 11488, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x2a966c9000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libpthread.so.0", O_RDONLY)  = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\220U\0\0"..., 640) = 640
fstat(3, {st_mode=S_IFREG|0644, st_size=93506, ...}) = 0
mmap(NULL, 1129792, PROT_READ|PROT_EXEC, MAP_PRIVATE, 3, 0) = 0x2a966cc000
mprotect(0x2a966da000, 1072448, PROT_NONE) = 0
mmap(0x2a967cc000, 65536, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED, 3, 0) = 0x2a967cc000
mmap(0x2a967dc000, 15680, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x2a967dc000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libstdc++.so.5", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\200\333"..., 640) = 640
fstat(3, {st_mode=S_IFREG|0644, st_size=830608, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2a967e0000
mmap(NULL, 1950528, PROT_READ|PROT_EXEC, MAP_PRIVATE, 3, 0) = 0x2a967e1000
mprotect(0x2a9688e000, 1241920, PROT_NONE) = 0
mmap(0x2a968e1000, 831488, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED, 3, 0) = 0x2a968e1000
mmap(0x2a969ac000, 70464, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x2a969ac000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libm.so.6", O_RDONLY)        = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\300@\0\0"..., 640) = 640
fstat(3, {st_mode=S_IFREG|0644, st_size=550208, ...}) = 0
mmap(NULL, 1596072, PROT_READ|PROT_EXEC, MAP_PRIVATE, 3, 0) = 0x2a969be000
mprotect(0x2a96a41000, 1059496, PROT_NONE) = 0
mmap(0x2a96abe000, 548864, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED, 3, 0) = 0x2a96abe000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libgcc_s.so.1", O_RDONLY)    = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0 \"\0\0\0"..., 640) = 640
fstat(3, {st_mode=S_IFREG|0644, st_size=54656, ...}) = 0
mmap(NULL, 1101632, PROT_READ|PROT_EXEC, MAP_PRIVATE, 3, 0) = 0x2a96b44000
mprotect(0x2a96b50000, 1052480, PROT_NONE) = 0
mmap(0x2a96c44000, 53248, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED, 3, 0) = 0x2a96c44000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libc.so.6", O_RDONLY)        = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0`\324\1\0"..., 640) = 640
fstat(3, {st_mode=S_IFREG|0644, st_size=1295392, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2a96c51000
mmap(NULL, 2354792, PROT_READ|PROT_EXEC, MAP_PRIVATE, 3, 0) = 0x2a96c52000
mprotect(0x2a96d74000, 1166952, PROT_NONE) = 0
mmap(0x2a96e52000, 241664, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED, 3, 0x100000) = 0x2a96e52000
mmap(0x2a96e8d000, 15976, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x2a96e8d000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libfontconfig.so.1", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\200\0\1"..., 640) = 640
fstat(3, {st_mode=S_IFREG|0644, st_size=202368, ...}) = 0
mmap(NULL, 1256288, PROT_READ|PROT_EXEC, MAP_PRIVATE, 3, 0) = 0x2a96e91000
mprotect(0x2a96ebb000, 1084256, PROT_NONE) = 0
mmap(0x2a96f91000, 200704, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED, 3, 0) = 0x2a96f91000
mmap(0x2a96fc2000, 7008, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x2a96fc2000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libaudio.so.2", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\300_\0\0"..., 640) = 640
fstat(3, {st_mode=S_IFREG|0644, st_size=97552, ...}) = 0
mmap(NULL, 1145000, PROT_READ|PROT_EXEC, MAP_PRIVATE, 3, 0) = 0x2a96fc4000
mprotect(0x2a96fd9000, 1058984, PROT_NONE) = 0
mmap(0x2a970c4000, 98304, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED, 3, 0) = 0x2a970c4000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/X11R6/lib/libXt.so.6", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\0009\1\0"..., 640) = 640
fstat(3, {st_mode=S_IFREG|0644, st_size=394832, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2a970dc000
mmap(NULL, 1445184, PROT_READ|PROT_EXEC, MAP_PRIVATE, 3, 0) = 0x2a970dd000
mprotect(0x2a97130000, 1105216, PROT_NONE) = 0
mmap(0x2a971dd000, 393216, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED, 3, 0) = 0x2a971dd000
mmap(0x2a9723d000, 3392, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x2a9723d000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libXrender.so.1", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\300\34\0"..., 640) = 640
fstat(3, {st_mode=S_IFREG|0644, st_size=37952, ...}) = 0
mmap(NULL, 1084920, PROT_READ|PROT_EXEC, MAP_PRIVATE, 3, 0) = 0x2a9723e000
mprotect(0x2a97246000, 1052152, PROT_NONE) = 0
mmap(0x2a9733e000, 36864, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED, 3, 0) = 0x2a9733e000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/X11R6/lib/libXrandr.so.2", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0@\23\0\0"..., 640) = 640
fstat(3, {st_mode=S_IFREG|0644, st_size=13512, ...}) = 0
mmap(NULL, 1060552, PROT_READ|PROT_EXEC, MAP_PRIVATE, 3, 0) = 0x2a97347000
mprotect(0x2a9734a000, 1048264, PROT_NONE) = 0
mmap(0x2a97447000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED, 3, 0) = 0x2a97447000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libXcursor.so.1", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\3004\0\0"..., 640) = 640
fstat(3, {st_mode=S_IFREG|0644, st_size=40808, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2a9744a000
mmap(NULL, 1087768, PROT_READ|PROT_EXEC, MAP_PRIVATE, 3, 0) = 0x2a9744b000
mprotect(0x2a97454000, 1050904, PROT_NONE) = 0
mmap(0x2a9754b000, 40960, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED, 3, 0) = 0x2a9754b000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/X11R6/lib/libXinerama.so.1", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\200\16\0"..., 640) = 640
fstat(3, {st_mode=S_IFREG|0644, st_size=9504, ...}) = 0
mmap(NULL, 1056472, PROT_READ|PROT_EXEC, MAP_PRIVATE, 3, 0) = 0x2a97555000
mprotect(0x2a97557000, 1048280, PROT_NONE) = 0
mmap(0x2a97655000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED, 3, 0) = 0x2a97655000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libXft.so.2", O_RDONLY)  = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\300Q\0\0"..., 640) = 640
fstat(3, {st_mode=S_IFREG|0644, st_size=79632, ...}) = 0
mmap(NULL, 1126632, PROT_READ|PROT_EXEC, MAP_PRIVATE, 3, 0) = 0x2a97657000
mprotect(0x2a97669000, 1052904, PROT_NONE) = 0
mmap(0x2a97757000, 81920, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED, 3, 0) = 0x2a97757000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libfreetype.so.6", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\0007\2\0"..., 640) = 640
fstat(3, {st_mode=S_IFREG|0644, st_size=582952, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2a9776b000
mmap(NULL, 1629888, PROT_READ|PROT_EXEC, MAP_PRIVATE, 3, 0) = 0x2a9776c000
mprotect(0x2a977e4000, 1138368, PROT_NONE) = 0
mmap(0x2a9786c000, 581632, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED, 3, 0) = 0x2a9786c000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libdl.so.2", O_RDONLY)       = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\0\36\0\0"..., 640) = 640
fstat(3, {st_mode=S_IFREG|0644, st_size=12072, ...}) = 0
mmap(NULL, 1058728, PROT_READ|PROT_EXEC, MAP_PRIVATE, 3, 0) = 0x2a978fa000
mprotect(0x2a978fd000, 1046440, PROT_NONE) = 0
mmap(0x2a979fa000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED, 3, 0) = 0x2a979fa000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libexpat.so.1", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\300>\0\0"..., 640) = 640
fstat(3, {st_mode=S_IFREG|0644, st_size=143232, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2a979fd000
mmap(NULL, 1190168, PROT_READ|PROT_EXEC, MAP_PRIVATE, 3, 0) = 0x2a979fe000
mprotect(0x2a97a1c000, 1067288, PROT_NONE) = 0
mmap(0x2a97afe000, 143360, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED, 3, 0) = 0x2a97afe000
close(3)                                = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2a97b21000
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2a97b22000
arch_prctl(0x1002, 0x2a97b21b60)        = 0
munmap(0x2a9556d000, 66798)             = 0
set_tid_address(0x2a97b21bf0)           = 7806
rt_sigaction(SIGRTMIN, {0x2a966d14f0, [], SA_SIGINFO|0x4000000}, NULL, 8) = 0
rt_sigprocmask(SIG_UNBLOCK, [RTMIN], NULL, 8) = 0
getrlimit(0x3, 0x7fbffff6d0)            = 0
brk(0)                                  = 0x50a000
brk(0x52b000)                           = 0x52b000
socketpair(PF_FILE, SOCK_STREAM, 0, [3, 4]) = 0
socketpair(PF_FILE, SOCK_STREAM, 0, [5, 6]) = 0
socketpair(PF_FILE, SOCK_STREAM, 0, [7, 8]) = 0
pipe([9, 10])                           = 0
access("/usr/lib/qt3/plugins", F_OK)    = 0
access("/usr/lib/qt3/plugins/codecs/.", F_OK) = -1 ENOENT (No such file or directory)
socketpair(PF_FILE, SOCK_STREAM, 0, [11, 12]) = 0
pipe([13, 14])                          = 0
fcntl(13, F_SETFD, FD_CLOEXEC)          = 0
fcntl(14, F_SETFD, FD_CLOEXEC)          = 0
rt_sigaction(SIGCHLD, {0x2a95952050, [CHLD], SA_RESTART|SA_NOCLDSTOP|0x4000000}, {SIG_DFL}, 8) = 0
rt_sigaction(SIGPIPE, {SIG_IGN}, {SIG_DFL}, 8) = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x2a97b21bf0) = 7807close(10)                               = 0
read(9, "", 1)                          = 0
close(9)                                = 0
close(3)                                = 0
fcntl(4, F_GETFL)                       = 0x2 (flags O_RDWR|O_LARGEFILE)
fcntl(4, F_SETFL, O_RDWR|O_NONBLOCK)    = 0
close(8)                                = 0
close(6)                                = 0
wait4(7807, 0x7fbffff31c, WNOHANG, NULL) = 0
nanosleep({0, 100000}, NULL)            = 0
wait4(7807, 0x7fbffff31c, WNOHANG, NULL) = 0
nanosleep({0, 100000}, NULL)            = 0
wait4(7807, 0x7fbffff31c, WNOHANG, NULL) = 0
nanosleep({0, 100000}, NULL)            = 0
wait4(7807, 0x7fbffff31c, WNOHANG, NULL) = 0
nanosleep({0, 100000}, NULL)            = 0
wait4(7807, 0x7fbffff31c, WNOHANG, NULL) = 0
nanosleep({0, 100000}, NULL)            = 0
wait4(7807, 0x7fbffff31c, WNOHANG, NULL) = 0
nanosleep({0, 100000}, NULL)            = 0
wait4(7807, 0x7fbffff31c, WNOHANG, NULL) = 0
nanosleep({0, 100000}, NULL)            = 0
wait4(7807, 0x7fbffff31c, WNOHANG, NULL) = 0
nanosleep({0, 100000}, NULL)            = 0
wait4(7807, 0x7fbffff31c, WNOHANG, NULL) = 0
nanosleep({0, 100000}, NULL)            = 0
wait4(7807, 0x7fbffff31c, WNOHANG, NULL) = 0
nanosleep({0, 100000}, NULL)            = 0
wait4(7807, 0x7fbffff31c, WNOHANG, NULL) = 0
nanosleep({0, 100000}, 0)               = ? ERESTART_RESTARTBLOCK (To be restarted)
--- SIGCHLD (Child exited) @ 0 (0) ---
write(11, "\1", 1)                      = 1
rt_sigreturn(0xb)                       = -1 EINTR (Interrupted system call)
wait4(7807, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], WNOHANG, NULL) = 7807
select(13, [12], NULL, NULL, {0, 0})    = 1 (in [12], left {0, 0})
read(12, "\1", 1)                       = 1
ioctl(7, FIONREAD, [54])                = 0
read(7, "amarok\nkded\nknotify\nkio_uiserver"..., 4096) = 54
select(8, [7], NULL, NULL, {0, 0})      = 1 (in [7], left {0, 0})
read(7, "", 4096)                       = 0
ioctl(5, FIONREAD, [0])                 = 0
close(7)                                = 0
close(5)                                = 0
close(4)                                = 0
socketpair(PF_FILE, SOCK_STREAM, 0, [3, 4]) = 0
socketpair(PF_FILE, SOCK_STREAM, 0, [5, 6]) = 0
socketpair(PF_FILE, SOCK_STREAM, 0, [7, 8]) = 0
pipe([9, 10])                           = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x2a97b21bf0) = 7808close(10)                               = 0
read(9, "", 1)                          = 0
close(9)                                = 0
close(3)                                = 0
fcntl(4, F_GETFL)                       = 0x2 (flags O_RDWR|O_LARGEFILE)
fcntl(4, F_SETFL, O_RDWR|O_NONBLOCK)    = 0
close(8)                                = 0
close(6)                                = 0
wait4(7808, 0x7fbffff3fc, WNOHANG, NULL) = 0
nanosleep({0, 100000}, NULL)            = 0
wait4(7808, 0x7fbffff3fc, WNOHANG, NULL) = 0
nanosleep({0, 100000}, NULL)            = 0
wait4(7808, 0x7fbffff3fc, WNOHANG, NULL) = 0
nanosleep({0, 100000}, NULL)            = 0
...
``` 
and continues repeating those last lines forever...
This is getting on my nerve because one of the reasons that I use linux is because I don't wan't nothing to slip out of my control...and I hadn't made upgrades or something like that and it just stopped working.

Thanks for any of your help!
Pedro Carrico

---

### Post by negatory on 2005-04-26
Solved it.
I had some processes related to sound and amarok running and killing those solved the whole problem.
Thanks

---

