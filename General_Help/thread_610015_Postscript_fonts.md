---
title: "Postscript fonts"
date: 2007-11-11
forum: General Help
---

### Post by ianmckeever on 2007-11-11
Ii am trying to install fonts for APL and the printer fonts are postscript. This appears to involve amending a file called fonts.scale. The software comes with a  utility program which does the necessary. However even if i run it as root it reports back as permission denied.

strace reports as follows. I moved the relevant files 
root@ian-laptop:/home/ian/aplxpe/fonts# strace ./addfonts fonts.scale.aplx fonts.scale
execve("./addfonts", ["./addfonts", "fonts.scale.aplx", "fonts.scale"], [/* 16 vars */]) = -1 EACCES (Permission denied)
dup(2)                                  = 3
fcntl64(3, F_GETFL)                     = 0x2 (flags O_RDWR)
fstat64(3, {st_mode=S_IFCHR|0600, st_rdev=makedev(136, 0), ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f9f000
_llseek(3, 0, 0xbf8f5c54, SEEK_CUR)     = -1 ESPIPE (Illegal seek)
write(3, "strace: exec: Permission denied\n", 32strace: exec: Permission denied
) = 32
close(3)                                = 0
munmap(0xb7f9f000, 4096)                = 0
exit_group(1)           
exit_group(1)                           = ?
Process 24259 detached
root@ian-laptop:/home/ian/aplxpe/fonts# 

Any help would be appreciated

---

