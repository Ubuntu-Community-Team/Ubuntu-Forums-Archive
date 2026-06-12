---
title: "setuid flag not having any effect?"
date: 2007-04-18
forum: General Help
---

### Post by Peter Howard on 2007-04-18
That is the immediate conclusion for my problem.  Which is . . . 

I installed vmware server on my Dapper machine.  Install went ok, and I can talk to the server fine using the vmware client, can create vms, configure, stop, delete.  But I can't start them.  After a 5 minute timeout I get a message telling me to try a commandline invocation on the server.  

I try said invocation and it exits immediately (with no output).  Unless I run it with "sudo", then it works and connects fine with the client and all is well.  This is what I get from using strace:

[FONT="Fixedsys"]strace /usr/local/lib/vmware/bin/vmware-vmx  /var/vm/VirtualMachines/Debian-sid/Debian-sid.vmx
execve("/usr/local/lib/vmware/bin/vmware-vmx", ["/usr/local/lib/vmware/bin/vmware"..., "/var/vm/VirtualMachines/Debian-s"...], [/* 15 vars */]) = 0
uname({sys="Linux", node="rhuiden", ...}) = 0
brk(0)                                  = 0x84db000
old_mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7fd9000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
old_mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7fd8000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
old_mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7fd7000
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=27144, ...}) = 0
old_mmap(NULL, 27144, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7fd0000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libm.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0@3\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=136368, ...}) = 0
old_mmap(NULL, 138800, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7fae000
old_mmap(0xb7fcf000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x20000) = 0xb7fcf000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libdl.so.2", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\260\v\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=8204, ...}) = 0
old_mmap(NULL, 11016, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7fab000
old_mmap(0xb7fad000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1000) = 0xb7fad000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libpthread.so.0", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0`H\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0755, st_size=86580, ...}) = 0
old_mmap(NULL, 71064, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7f99000
old_mmap(0xb7fa8000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xe000) = 0xb7fa8000
old_mmap(0xb7fa9000, 5528, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7fa9000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libX11.so.6", O_RDONLY)  = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0000I\1\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=938112, ...}) = 0
old_mmap(NULL, 938412, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7eb3000
old_mmap(0xb7f94000, 16384, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xe1000) = 0xb7f94000
old_mmap(0xb7f98000, 428, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7f98000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libXtst.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\240\17"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=17184, ...}) = 0
old_mmap(NULL, 20144, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7eae000
old_mmap(0xb7eb2000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x3000) = 0xb7eb2000
close(3)                                = 0

[large amount cut]

stat64("/usr/local/lib/vmware/settings", 0xbffeb760) = -1 ENOENT (No such file or directory)
stat64("/home/pjh/.vmware/config", 0xbffeb760) = -1 ENOENT (No such file or directory)
setresuid32(-1, 0, -1)                  = -1 EPERM (Operation not permitted)
geteuid32()                             = 501
write(2, "\n\nVMware Server Error:\nVMware Se"..., 269

VMware Server Error:
VMware Server must be set-UID root, "/usr/local/lib/vmware/bin/vmware-vmx" is not.  Are you running /usr/local/lib/vmware/bin/vmware-vmx from its distribution directory?  That copy of the program is not set-UID root.

Press "Enter" to continue...) = 269
fstat64(0, {st_mode=S_IFCHR|0620, st_rdev=makedev(136, 0), ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7fd5000
read(0, 

[/FONT]

Note I didn't get the error output outside strace.  
/usr/local/lib/vmware/bin/vmware-vmx is setuid:

[FONT="Fixedsys"]pjh@rhuiden:~$ ls -l /usr/local/lib/vmware/bin/vmware-vmx
-r-sr-xr-x 1 root root 4385956 2007-04-09 09:00 /usr/local/lib/vmware/bin/vmware-vmx[/FONT]

So, can anyone give me a hint from the abouve why the setuid would not be occuring?

Thanks

PJH

---

### Post by fanatik on 2007-04-19
is the filesystem mounted with the nosuid option?

$ mount

will show you.

---

### Post by Peter Howard on 2007-04-19
Not to my knowledge.  The only options from "mount" are (rw).  The options from /etc/fstab is "defaults".

---

