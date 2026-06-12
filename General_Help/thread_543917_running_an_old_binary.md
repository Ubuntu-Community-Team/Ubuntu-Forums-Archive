---
title: "running an old binary"
date: 2007-09-05
forum: General Help
---

### Post by destructchaos on 2007-09-05
i am trying to avoid having to reinstall windows on my laptop, but it looks like i may have no choice.  i need to run a program for class and for once, the teacher has a linux version, but the company that made it only supports red hat 5; i'm running feisty on this machine.  my guess is that the binary was compiled for the 2.4 kernel, or earlier.  is there any way for me to run it?

---

### Post by pmg on 2007-09-05
I really doubt they mean the old, old RedHat 5 (which I think ran the 1.2 kernel - even before the 2.0 series.)  I suspect they mean RedHat Enterprise Server 5 (RHEL 5) which became available earlier this year.  Have you tried running the binary?  What errors do you get?  Or are you having troubles installing it?

---

### Post by destructchaos on 2007-09-06
i'm trying to install it using the provided binary named "setup".  when i run ./setup, nothing happens:
```

rick@DeepThought:~/xilinx/ise/bin/lin$ ./setup
rick@DeepThought:~/xilinx/ise/bin/lin$

```
there is also a _setup that i tried running, but it fails with an error stating that it can't find a *.so file that's in the same directory as the binary.

thanks for the help.

---

### Post by pmg on 2007-09-06
What types of files are in the directory?  Are there .rpm files?  If so, RedHat manages packages using **rpm** (the Redhat Packages Manager) which is different the Ubuntu (which uses Debian packages.)  The good news it it's usually possible to get rpms installed on Ubuntu with a little work.

What does the setup program do?  It is probably a script and so readable.  It may be depending on the layout of directories/programs on RedHat, which is somewhat different then on Ubuntu.  In that case it may just be a matter of tweaking the script to make it understand Ubuntu (but then again, maybe not.)   Can you post the script (if it's not copyrighted) and the list of files you got with it, and maybe we can help?

---

### Post by destructchaos on 2007-09-10
unfortunately, it's neither rpm or deb:

```

rick@DeepThought:~/xilinx/image/ise/bin/lin$ ls -l
total 21996
---xr--r-- 1 rick rick 2645284 2006-12-01 12:09 libgui_gq.so
---xr--r-- 1 rick rick   42876 2006-12-01 12:09 libminizip.so
---xr--r-- 1 rick rick 1044120 2006-12-01 12:09 libportability.so
---xr--r-- 1 rick rick    9480 2006-12-01 12:09 libport_execloader.so
---xr--r-- 1 rick rick 8992284 2006-12-01 12:09 libqt_qt.so
---xr--r-- 1 rick rick  153560 2006-12-01 12:09 libqt_solutions.so
---xr--r-- 1 rick rick  882632 2006-12-01 12:09 libstl.so
---xr--r-- 1 rick rick   39444 2006-12-01 12:09 libthread.so
---xr--r-- 1 rick rick  350188 2006-12-01 12:09 libtutilities.so
---xr--r-- 1 rick rick  237012 2006-12-01 12:09 libutilc_messagedispatcher.so
---xr--r-- 1 rick rick  984096 2006-12-01 12:09 libwiclient.so
---xr--r-- 1 rick rick 3932976 2006-12-01 12:09 libxercesc.so
---xr--r-- 1 rick rick   72664 2006-12-01 12:09 libzlib.so
---xr--r-- 1 rick rick   16968 2006-12-01 12:09 setup
---xr--r-- 1 rick rick 2787167 2006-12-01 12:09 _setup
---xr--r-- 1 rick rick   16904 2006-12-01 12:09 xinfo
---xr--r-- 1 rick rick  214569 2006-12-01 12:09 _xinfo
---xr--r-- 1 rick rick     731 2006-12-01 12:09 xinfoenv

```

setup is a binary file, not a script.  i really have no idea what to do.

---

### Post by Maestro23 on 2007-09-10
> **destructchaos said:**
> unfortunately, it's neither rpm or deb:

```

rick@DeepThought:~/xilinx/image/ise/bin/lin$ ls -l
total 21996
---xr--r-- 1 rick rick 2645284 2006-12-01 12:09 libgui_gq.so
---xr--r-- 1 rick rick   42876 2006-12-01 12:09 libminizip.so
---xr--r-- 1 rick rick 1044120 2006-12-01 12:09 libportability.so
---xr--r-- 1 rick rick    9480 2006-12-01 12:09 libport_execloader.so
---xr--r-- 1 rick rick 8992284 2006-12-01 12:09 libqt_qt.so
---xr--r-- 1 rick rick  153560 2006-12-01 12:09 libqt_solutions.so
---xr--r-- 1 rick rick  882632 2006-12-01 12:09 libstl.so
---xr--r-- 1 rick rick   39444 2006-12-01 12:09 libthread.so
---xr--r-- 1 rick rick  350188 2006-12-01 12:09 libtutilities.so
---xr--r-- 1 rick rick  237012 2006-12-01 12:09 libutilc_messagedispatcher.so
---xr--r-- 1 rick rick  984096 2006-12-01 12:09 libwiclient.so
---xr--r-- 1 rick rick 3932976 2006-12-01 12:09 libxercesc.so
---xr--r-- 1 rick rick   72664 2006-12-01 12:09 libzlib.so
---xr--r-- 1 rick rick   16968 2006-12-01 12:09 setup
---xr--r-- 1 rick rick 2787167 2006-12-01 12:09 _setup
---xr--r-- 1 rick rick   16904 2006-12-01 12:09 xinfo
---xr--r-- 1 rick rick  214569 2006-12-01 12:09 _xinfo
---xr--r-- 1 rick rick     731 2006-12-01 12:09 xinfoenv

```

setup is a binary file, not a script.  i really have no idea what to do.

.bin file?  Try:

> chmod a+x filename.bin

./filename.bin

---

### Post by destructchaos on 2007-09-11
it's not a *.bin file.  it's just called "setup" and is binary.  if i try to open it in kate, i get the following error:

"The file setup is a binary, saving it will result in a corrupt file."

---

### Post by tgalati4 on 2007-09-11
>sudo chmod a+x setup
>./setup

---

### Post by Maestro23 on 2007-09-11
> **tgalati4 said:**
> >sudo chmod a+x setup
>./setup

What he said.

---

### Post by destructchaos on 2007-09-12
same effect as before:

```

rick@DeepThought:~/xilinx/image/ise/bin/lin$ sudo chmod a+x setup
Password:
rick@DeepThought:~/xilinx/image/ise/bin/lin$ ls -l
total 21996
---xr--r-- 1 rick rick 2645284 2006-12-01 12:09 libgui_gq.so
---xr--r-- 1 rick rick   42876 2006-12-01 12:09 libminizip.so
---xr--r-- 1 rick rick 1044120 2006-12-01 12:09 libportability.so
---xr--r-- 1 rick rick    9480 2006-12-01 12:09 libport_execloader.so
---xr--r-- 1 rick rick 8992284 2006-12-01 12:09 libqt_qt.so
---xr--r-- 1 rick rick  153560 2006-12-01 12:09 libqt_solutions.so
---xr--r-- 1 rick rick  882632 2006-12-01 12:09 libstl.so
---xr--r-- 1 rick rick   39444 2006-12-01 12:09 libthread.so
---xr--r-- 1 rick rick  350188 2006-12-01 12:09 libtutilities.so
---xr--r-- 1 rick rick  237012 2006-12-01 12:09 libutilc_messagedispatcher.so
---xr--r-- 1 rick rick  984096 2006-12-01 12:09 libwiclient.so
---xr--r-- 1 rick rick 3932976 2006-12-01 12:09 libxercesc.so
---xr--r-- 1 rick rick   72664 2006-12-01 12:09 libzlib.so
---xr-xr-x 1 rick rick   16968 2006-12-01 12:09 setup
---xr--r-- 1 rick rick 2787167 2006-12-01 12:09 _setup
---xr--r-- 1 rick rick   16904 2006-12-01 12:09 xinfo
---xr--r-- 1 rick rick  214569 2006-12-01 12:09 _xinfo
---xr--r-- 1 rick rick     731 2006-12-01 12:09 xinfoenv
rick@DeepThought:~/xilinx/image/ise/bin/lin$ ./setup
rick@DeepThought:~/xilinx/image/ise/bin/lin$ 

```

it just doesn't seem to do anything.

---

### Post by Maestro23 on 2007-09-12
Can you provide a link to the program's website.

---

### Post by pmg on 2007-09-13
Have you tried "./setup -h" or "./setup --help" to see if that makes it say anything?

You could try running it under strace (strace setup) and look at what system calls it's making.  That would show such things as what files it may be opening which might give some hits as to what it's trying to do.

---

### Post by dougfractal on 2007-09-14
from [http://www.xilinx.com/xlnx/xil_ans_display.jsp?BV_UseBVCookie=yes&getPagePath=25384&iCountryID=1&iLanguageID=1](http://www.xilinx.com/xlnx/xil_ans_display.jsp?BV_UseBVCookie=yes&getPagePath=25384&iCountryID=1&iLanguageID=1)
> Installation Instructions for Red Hat Linux and Sun Solaris Users

1. Download "9_2_0xi_<platform>.zip from:
[http://www.xilinx.com/xlnx/xil_sw_updates_home.jsp](http://www.xilinx.com/xlnx/xil_sw_updates_home.jsp)

2. Move the zip file to an empty "staging" area and unzip the downloaded file.

For example:
mv 9_2_0xi_<platform>.zip /home/<staging_dir>
cd /home/<staging_dir>
unzip 9_2_0xi_<platform>.zip
cd 9_2_0xi_<platform>
chmod -R 775 * (in case the file permissions are incorrect)

3. Run "./setup"

NOTE: WebUpdate can also be used to download and install ISE Service Packs.

this is just a sample page from [http://www.xilinx.com/](http://www.xilinx.com/)

just list the missing libarays
do
use the ubuntu package finder (in firefox search) to find the ****-dev.deb.
use synaptic to install.
repeat till all depenences are installed
done

good luck. Any missing files. I'l help find them ;-)

---

### Post by destructchaos on 2007-09-16
pmg:
./setup -h and ./setup --help did nothing.  strace to follow in a moment.

dougfractal:
the ubuntu package finder turns up nothing when i search for a few of the missing files.

here's the strace:

```

rick@DeepThought:~/xilinx/image/ise/bin/lin$ strace ./setup
execve("./setup", ["./setup"], [/* 33 vars */]) = 0
brk(0)                                  = 0x804d000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap2(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7fce000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=73342, ...}) = 0
mmap2(NULL, 73342, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7fbc000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libdl.so.2", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0P\n\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=9684, ...}) = 0
mmap2(NULL, 12412, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7fb8000
mmap2(0xb7fba000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1) = 0xb7fba000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libpthread.so.0", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\20H\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=112362, ...}) = 0
mmap2(NULL, 90592, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7fa1000
mmap2(0xb7fb4000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x13) = 0xb7fb4000
mmap2(0xb7fb6000, 4576, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7fb6000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libstdc++.so.5", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\320\276"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=737416, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7fa0000
mmap2(NULL, 760960, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7ee6000
mmap2(0xb7f96000, 20480, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xaf) = 0xb7f96000
mmap2(0xb7f9b000, 19584, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7f9b000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libm.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0P4\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=153424, ...}) = 0
mmap2(NULL, 155776, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7ebf000
mmap2(0xb7ee4000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x24) = 0xb7ee4000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libgcc_s.so.1", O_RDONLY)    = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0000\34\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=42796, ...}) = 0
mmap2(NULL, 45892, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7eb3000
mmap2(0xb7ebe000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xa) = 0xb7ebe000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libc.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\0`\1\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=1307104, ...}) = 0
mmap2(NULL, 1312164, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7d72000
mmap2(0xb7ead000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x13b) = 0xb7ead000
mmap2(0xb7eb0000, 9636, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7eb0000
close(3)                                = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7d71000
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7d70000
set_thread_area({entry_number:-1 -> 6, base_addr:0xb7d706c0, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}) = 0
mprotect(0xb7ead000, 4096, PROT_READ)   = 0
munmap(0xb7fbc000, 73342)               = 0
set_tid_address(0xb7d70708)             = 17049
sendto(-1210644720, umovestr: Input/output error
0xc, 3086700532, MSG_EOR|MSG_DONTWAIT|MSG_FIN|MSG_SYN|0xb7d70000, {sa_family=AF_DECnet, sa_data="\0\0\320=\0\0\r\0\0\0p\362\0\0"}, 3214602536) = 0
rt_sigaction(SIGRTMIN, {0xb7fa53f0, [], SA_SIGINFO}, NULL, 8) = 0
rt_sigaction(SIGRT_1, {0xb7fa5300, [], SA_RESTART|SA_SIGINFO}, NULL, 8) = 0
rt_sigprocmask(SIG_UNBLOCK, [RTMIN RT_1], NULL, 8) = 0
getrlimit(RLIMIT_STACK, {rlim_cur=8192*1024, rlim_max=RLIM_INFINITY}) = 0
uname({sys="Linux", node="DeepThought", ...}) = 0
brk(0)                                  = 0x804d000
brk(0x806e000)                          = 0x806e000
readlink("/proc/17049/exe", "/home/rick/xilinx/image/ise/bin/lin/setup", 4096) = 41
execve("/home/rick/xilinx/image/ise/bin/lin/setup", ["./setup"], [/* 36 vars */]) = 0
brk(0)                                  = 0x804d000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap2(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f7f000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/home/rick/xilinx/image/ise/bin/lin/tls/i686/sse2/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/home/rick/xilinx/image/ise/bin/lin/tls/i686/sse2/cmov", 0xbffdbe28) = -1 ENOENT (No such file or directory)
open("/home/rick/xilinx/image/ise/bin/lin/tls/i686/sse2/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/home/rick/xilinx/image/ise/bin/lin/tls/i686/sse2", 0xbffdbe28) = -1 ENOENT (No such file or directory)
open("/home/rick/xilinx/image/ise/bin/lin/tls/i686/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/home/rick/xilinx/image/ise/bin/lin/tls/i686/cmov", 0xbffdbe28) = -1 ENOENT (No such file or directory)
open("/home/rick/xilinx/image/ise/bin/lin/tls/i686/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/home/rick/xilinx/image/ise/bin/lin/tls/i686", 0xbffdbe28) = -1 ENOENT (No such file or directory)
open("/home/rick/xilinx/image/ise/bin/lin/tls/sse2/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/home/rick/xilinx/image/ise/bin/lin/tls/sse2/cmov", 0xbffdbe28) = -1 ENOENT (No such file or directory)
open("/home/rick/xilinx/image/ise/bin/lin/tls/sse2/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/home/rick/xilinx/image/ise/bin/lin/tls/sse2", 0xbffdbe28) = -1 ENOENT (No such file or directory)
open("/home/rick/xilinx/image/ise/bin/lin/tls/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/home/rick/xilinx/image/ise/bin/lin/tls/cmov", 0xbffdbe28) = -1 ENOENT (No such file or directory)
open("/home/rick/xilinx/image/ise/bin/lin/tls/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/home/rick/xilinx/image/ise/bin/lin/tls", 0xbffdbe28) = -1 ENOENT (No such file or directory)
open("/home/rick/xilinx/image/ise/bin/lin/i686/sse2/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/home/rick/xilinx/image/ise/bin/lin/i686/sse2/cmov", 0xbffdbe28) = -1 ENOENT (No such file or directory)
open("/home/rick/xilinx/image/ise/bin/lin/i686/sse2/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/home/rick/xilinx/image/ise/bin/lin/i686/sse2", 0xbffdbe28) = -1 ENOENT (No such file or directory)
open("/home/rick/xilinx/image/ise/bin/lin/i686/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/home/rick/xilinx/image/ise/bin/lin/i686/cmov", 0xbffdbe28) = -1 ENOENT (No such file or directory)
open("/home/rick/xilinx/image/ise/bin/lin/i686/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/home/rick/xilinx/image/ise/bin/lin/i686", 0xbffdbe28) = -1 ENOENT (No such file or directory)
open("/home/rick/xilinx/image/ise/bin/lin/sse2/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/home/rick/xilinx/image/ise/bin/lin/sse2/cmov", 0xbffdbe28) = -1 ENOENT (No such file or directory)
open("/home/rick/xilinx/image/ise/bin/lin/sse2/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/home/rick/xilinx/image/ise/bin/lin/sse2", 0xbffdbe28) = -1 ENOENT (No such file or directory)
open("/home/rick/xilinx/image/ise/bin/lin/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/home/rick/xilinx/image/ise/bin/lin/cmov", 0xbffdbe28) = -1 ENOENT (No such file or directory)
open("/home/rick/xilinx/image/ise/bin/lin/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/home/rick/xilinx/image/ise/bin/lin", {st_mode=S_IFDIR|0775, st_size=4096, ...}) = 0
open("/home/rick/xilinx/image/ise/lib/lin/tls/i686/sse2/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/home/rick/xilinx/image/ise/lib/lin/tls/i686/sse2/cmov", 0xbffdbe28) = -1 ENOENT (No such file or directory)
open("/home/rick/xilinx/image/ise/lib/lin/tls/i686/sse2/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/home/rick/xilinx/image/ise/lib/lin/tls/i686/sse2", 0xbffdbe28) = -1 ENOENT (No such file or directory)
open("/home/rick/xilinx/image/ise/lib/lin/tls/i686/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/home/rick/xilinx/image/ise/lib/lin/tls/i686/cmov", 0xbffdbe28) = -1 ENOENT (No such file or directory)
open("/home/rick/xilinx/image/ise/lib/lin/tls/i686/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/home/rick/xilinx/image/ise/lib/lin/tls/i686", 0xbffdbe28) = -1 ENOENT (No such file or directory)
open("/home/rick/xilinx/image/ise/lib/lin/tls/sse2/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/home/rick/xilinx/image/ise/lib/lin/tls/sse2/cmov", 0xbffdbe28) = -1 ENOENT (No such file or directory)
open("/home/rick/xilinx/image/ise/lib/lin/tls/sse2/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/home/rick/xilinx/image/ise/lib/lin/tls/sse2", 0xbffdbe28) = -1 ENOENT (No such file or directory)
open("/home/rick/xilinx/image/ise/lib/lin/tls/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/home/rick/xilinx/image/ise/lib/lin/tls/cmov", 0xbffdbe28) = -1 ENOENT (No such file or directory)
open("/home/rick/xilinx/image/ise/lib/lin/tls/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/home/rick/xilinx/image/ise/lib/lin/tls", 0xbffdbe28) = -1 ENOENT (No such file or directory)
open("/home/rick/xilinx/image/ise/lib/lin/i686/sse2/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/home/rick/xilinx/image/ise/lib/lin/i686/sse2/cmov", 0xbffdbe28) = -1 ENOENT (No such file or directory)
open("/home/rick/xilinx/image/ise/lib/lin/i686/sse2/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/home/rick/xilinx/image/ise/lib/lin/i686/sse2", 0xbffdbe28) = -1 ENOENT (No such file or directory)
open("/home/rick/xilinx/image/ise/lib/lin/i686/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/home/rick/xilinx/image/ise/lib/lin/i686/cmov", 0xbffdbe28) = -1 ENOENT (No such file or directory)
open("/home/rick/xilinx/image/ise/lib/lin/i686/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/home/rick/xilinx/image/ise/lib/lin/i686", 0xbffdbe28) = -1 ENOENT (No such file or directory)
open("/home/rick/xilinx/image/ise/lib/lin/sse2/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/home/rick/xilinx/image/ise/lib/lin/sse2/cmov", 0xbffdbe28) = -1 ENOENT (No such file or directory)
open("/home/rick/xilinx/image/ise/lib/lin/sse2/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/home/rick/xilinx/image/ise/lib/lin/sse2", 0xbffdbe28) = -1 ENOENT (No such file or directory)
open("/home/rick/xilinx/image/ise/lib/lin/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/home/rick/xilinx/image/ise/lib/lin/cmov", 0xbffdbe28) = -1 ENOENT (No such file or directory)
open("/home/rick/xilinx/image/ise/lib/lin/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/home/rick/xilinx/image/ise/lib/lin", 0xbffdbe28) = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=73342, ...}) = 0
mmap2(NULL, 73342, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7f6d000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libdl.so.2", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0P\n\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=9684, ...}) = 0
mmap2(NULL, 12412, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7f69000
mmap2(0xb7f6b000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1) = 0xb7f6b000
close(3)                                = 0
open("/home/rick/xilinx/image/ise/bin/lin/libpthread.so.0", O_RDONLY) = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libpthread.so.0", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\20H\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=112362, ...}) = 0
mmap2(NULL, 90592, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7f52000
mmap2(0xb7f65000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x13) = 0xb7f65000
mmap2(0xb7f67000, 4576, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7f67000
close(3)                                = 0
open("/home/rick/xilinx/image/ise/bin/lin/libstdc++.so.5", O_RDONLY) = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libstdc++.so.5", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\320\276"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=737416, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f51000
mmap2(NULL, 760960, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7e97000
mmap2(0xb7f47000, 20480, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xaf) = 0xb7f47000
mmap2(0xb7f4c000, 19584, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7f4c000
close(3)                                = 0
open("/home/rick/xilinx/image/ise/bin/lin/libm.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libm.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0P4\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=153424, ...}) = 0
mmap2(NULL, 155776, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7e70000
mmap2(0xb7e95000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x24) = 0xb7e95000
close(3)                                = 0
open("/home/rick/xilinx/image/ise/bin/lin/libgcc_s.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libgcc_s.so.1", O_RDONLY)    = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0000\34\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=42796, ...}) = 0
mmap2(NULL, 45892, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7e64000
mmap2(0xb7e6f000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xa) = 0xb7e6f000
close(3)                                = 0
open("/home/rick/xilinx/image/ise/bin/lin/libc.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libc.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\0`\1\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=1307104, ...}) = 0
mmap2(NULL, 1312164, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7d23000
mmap2(0xb7e5e000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x13b) = 0xb7e5e000
mmap2(0xb7e61000, 9636, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7e61000
close(3)                                = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7d22000
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7d21000
set_thread_area({entry_number:-1 -> 6, base_addr:0xb7d216c0, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}) = 0
mprotect(0xb7e5e000, 4096, PROT_READ)   = 0
munmap(0xb7f6d000, 73342)               = 0
set_tid_address(0xb7d21708)             = 17049
sendto(-1210968304, umovestr: Input/output error
0xc, 3086376948, MSG_EOR|MSG_DONTWAIT|MSG_FIN|MSG_SYN|MSG_RST|0xb7d20000, {sa_family=AF_DECnet, sa_data="\0\0\320=\0\0\r\0\0\0p\362\0\0"}, 3221079656) = 0
rt_sigaction(SIGRTMIN, {0xb7f563f0, [], SA_SIGINFO}, NULL, 8) = 0
rt_sigaction(SIGRT_1, {0xb7f56300, [], SA_RESTART|SA_SIGINFO}, NULL, 8) = 0
rt_sigprocmask(SIG_UNBLOCK, [RTMIN RT_1], NULL, 8) = 0
getrlimit(RLIMIT_STACK, {rlim_cur=8192*1024, rlim_max=RLIM_INFINITY}) = 0
uname({sys="Linux", node="DeepThought", ...}) = 0
brk(0)                                  = 0x804d000
brk(0x806e000)                          = 0x806e000
readlink("/proc/17049/exe", "/home/rick/xilinx/image/ise/bin/lin/setup", 4096) = 41
futex(0xb7f6c070, FUTEX_WAKE, 2147483647) = 0
open("/home/rick/xilinx/image/ise/bin/lin/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=73342, ...}) = 0
mmap2(NULL, 73342, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7f6d000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/sse2/cmov/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/tls/i686/sse2/cmov", 0xbffdb01c) = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/sse2/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/tls/i686/sse2", 0xbffdb01c) = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/tls/i686/cmov", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/lib/tls/i686/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/tls/i686", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/lib/tls/sse2/cmov/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/tls/sse2/cmov", 0xbffdb01c) = -1 ENOENT (No such file or directory)
open("/lib/tls/sse2/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/tls/sse2", 0xbffdb01c)     = -1 ENOENT (No such file or directory)
open("/lib/tls/cmov/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/tls/cmov", 0xbffdb01c)     = -1 ENOENT (No such file or directory)
open("/lib/tls/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/tls", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/lib/i686/sse2/cmov/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i686/sse2/cmov", 0xbffdb01c) = -1 ENOENT (No such file or directory)
open("/lib/i686/sse2/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i686/sse2", 0xbffdb01c)    = -1 ENOENT (No such file or directory)
open("/lib/i686/cmov/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i686/cmov", 0xbffdb01c)    = -1 ENOENT (No such file or directory)
open("/lib/i686/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i686", 0xbffdb01c)         = -1 ENOENT (No such file or directory)
open("/lib/sse2/cmov/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/sse2/cmov", 0xbffdb01c)    = -1 ENOENT (No such file or directory)
open("/lib/sse2/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/sse2", 0xbffdb01c)         = -1 ENOENT (No such file or directory)
open("/lib/cmov/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/cmov", 0xbffdb01c)         = -1 ENOENT (No such file or directory)
open("/lib/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/usr/lib/tls/i686/sse2/cmov/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/tls/i686/sse2/cmov", 0xbffdb01c) = -1 ENOENT (No such file or directory)
open("/usr/lib/tls/i686/sse2/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/tls/i686/sse2", 0xbffdb01c) = -1 ENOENT (No such file or directory)
open("/usr/lib/tls/i686/cmov/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/tls/i686/cmov", 0xbffdb01c) = -1 ENOENT (No such file or directory)
open("/usr/lib/tls/i686/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/tls/i686", 0xbffdb01c) = -1 ENOENT (No such file or directory)
open("/usr/lib/tls/sse2/cmov/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/tls/sse2/cmov", 0xbffdb01c) = -1 ENOENT (No such file or directory)
open("/usr/lib/tls/sse2/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/tls/sse2", 0xbffdb01c) = -1 ENOENT (No such file or directory)
open("/usr/lib/tls/cmov/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/tls/cmov", 0xbffdb01c) = -1 ENOENT (No such file or directory)
open("/usr/lib/tls/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/tls", 0xbffdb01c)      = -1 ENOENT (No such file or directory)
open("/usr/lib/i686/sse2/cmov/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i686/sse2/cmov", 0xbffdb01c) = -1 ENOENT (No such file or directory)
open("/usr/lib/i686/sse2/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i686/sse2", 0xbffdb01c) = -1 ENOENT (No such file or directory)
open("/usr/lib/i686/cmov/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i686/cmov", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/usr/lib/i686/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i686", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/usr/lib/sse2/cmov/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/sse2/cmov", 0xbffdb01c) = -1 ENOENT (No such file or directory)
open("/usr/lib/sse2/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/sse2", 0xbffdb01c)     = -1 ENOENT (No such file or directory)
open("/usr/lib/cmov/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/cmov", 0xbffdb01c)     = -1 ENOENT (No such file or directory)
open("/usr/lib/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib", {st_mode=S_IFDIR|0755, st_size=69632, ...}) = 0
open("/lib/i486-linux-gnu/tls/i686/sse2/cmov/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i486-linux-gnu/tls/i686/sse2/cmov", 0xbffdb01c) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/tls/i686/sse2/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i486-linux-gnu/tls/i686/sse2", 0xbffdb01c) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/tls/i686/cmov/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i486-linux-gnu/tls/i686/cmov", 0xbffdb01c) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/tls/i686/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i486-linux-gnu/tls/i686", 0xbffdb01c) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/tls/sse2/cmov/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i486-linux-gnu/tls/sse2/cmov", 0xbffdb01c) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/tls/sse2/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i486-linux-gnu/tls/sse2", 0xbffdb01c) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/tls/cmov/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i486-linux-gnu/tls/cmov", 0xbffdb01c) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/tls/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i486-linux-gnu/tls", 0xbffdb01c) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/i686/sse2/cmov/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i486-linux-gnu/i686/sse2/cmov", 0xbffdb01c) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/i686/sse2/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i486-linux-gnu/i686/sse2", 0xbffdb01c) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/i686/cmov/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i486-linux-gnu/i686/cmov", 0xbffdb01c) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/i686/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i486-linux-gnu/i686", 0xbffdb01c) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/sse2/cmov/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i486-linux-gnu/sse2/cmov", 0xbffdb01c) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/sse2/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i486-linux-gnu/sse2", 0xbffdb01c) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/cmov/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i486-linux-gnu/cmov", 0xbffdb01c) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i486-linux-gnu", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/usr/lib/i486-linux-gnu/tls/i686/sse2/cmov/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i486-linux-gnu/tls/i686/sse2/cmov", 0xbffdb01c) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/tls/i686/sse2/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i486-linux-gnu/tls/i686/sse2", 0xbffdb01c) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/tls/i686/cmov/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i486-linux-gnu/tls/i686/cmov", 0xbffdb01c) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/tls/i686/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i486-linux-gnu/tls/i686", 0xbffdb01c) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/tls/sse2/cmov/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i486-linux-gnu/tls/sse2/cmov", 0xbffdb01c) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/tls/sse2/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i486-linux-gnu/tls/sse2", 0xbffdb01c) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/tls/cmov/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i486-linux-gnu/tls/cmov", 0xbffdb01c) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/tls/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i486-linux-gnu/tls", 0xbffdb01c) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/i686/sse2/cmov/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i486-linux-gnu/i686/sse2/cmov", 0xbffdb01c) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/i686/sse2/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i486-linux-gnu/i686/sse2", 0xbffdb01c) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/i686/cmov/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i486-linux-gnu/i686/cmov", 0xbffdb01c) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/i686/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i486-linux-gnu/i686", 0xbffdb01c) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/sse2/cmov/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i486-linux-gnu/sse2/cmov", 0xbffdb01c) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/sse2/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i486-linux-gnu/sse2", 0xbffdb01c) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/cmov/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i486-linux-gnu/cmov", 0xbffdb01c) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/libPort_ExecLoader.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i486-linux-gnu", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
munmap(0xb7f6d000, 73342)               = 0
exit_group(1)                           = ?
Process 17049 detached

```

i seem to be missing quite a few files.

---

### Post by dougfractal on 2007-09-16
> open("/home/rick/xilinx/image/ise/bin/lin/tls/i686/sse2/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
is there really no file here

**/home/rick/xilinx/image/ise/bin/lin/tls/i686/sse2/cmov/libdl.so.2**

can you browse your cd and see if it has been placed in the wrong folder.

the closest thing to libPort_ExecLoader.so i found is **hflash-1.0-beta RPM for i386** libport.so , so it must be on your disk.

---

### Post by destructchaos on 2007-09-16
there aren't any other directories in the "lin" folder.  if you jump to the previous page in this thread, i've posted an ls of the "lin" folder.  the whole "tls/i686/sse2/cmov" type structure is typically found in the "/lib" folder, so is it possible that i'm supposed to have all those already installed, but it's just looking in a relative path?  could it be an ubuntu vs. red hat thing?

---

### Post by dougfractal on 2007-09-17
> mkdir -p /home/rick/xilinx/image/ise/bin/lin/tls/i686/sse2/cmov/
cd  /home/rick/xilinx/image/ise/bin/lin
cp *.so /home/rick/xilinx/image/ise/bin/lin/tls/i686/sse2/cmov/

does this do any good?
I saw you have libport_execloader.so
you might have to > ln -s libport_execloader.so libPort_ExecLoader.so

You might have to put other files in the correct place and they will be case sensitive.

There probably a export LIB_PATH setting to make it use the ./ folder but I don't know it.

---

### Post by pmg on 2007-09-18
Have you tried **export LD_LIBRARY_PATH=/home/rick/xilinx/image/ise/bin/lin** before running the setup program.  Since it's trying to access libPort_ExecLoader.so and your directory has libport_execloader.so, I suspect you'll also have to make the symlink dougfractal mentioned.

---

### Post by lognok on 2007-10-03
Hi destructchaos, I think it's strange that you don't get any error messages when running ./setup. My systems reported a "./setup: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory" and would not run until I installed libstdc++5 via synaptic.

Try installing libstdc++5, run ./setup again and see what happens. I think this is the cause of your frustrations, although I guess by the last post in this thread that you may have moved on to install windows on your laptop again.

Everything will install, but the cable drivers for programming devices. This only works out of the box on Red Hat and Fedora systems. For this to work on Ubuntu, look elsewhere in this forum.

Take care

---

