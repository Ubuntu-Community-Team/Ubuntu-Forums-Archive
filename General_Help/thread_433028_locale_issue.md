---
title: "locale issue"
date: 2007-05-04
forum: General Help
---

### Post by frenky on 2007-05-04
Hi *,
i have quite weird locale problem...

I have in /etc/environment:

```
LANG="en_US.UTF-8"
LANGUAGE="en_US:en"
```

and locale returns:

```
frenky@fdd:~$ locale
[COLOR="Red"]locale: Cannot set LC_ALL to default locale: No such file or directory[/COLOR]
LANG=en_US.UTF-8
LANGUAGE=en_US:en
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=
/etc [0]
frenky@fdd:~$ 

```

When I do strace (to see what is missing,,,) I get 

```

10492 execve("/usr/bin/locale", ["locale"], [/* 33 vars */]) = 0
10492 brk(0)                            = 0x8050000
10492 access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
10492 mmap2(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f22000
10492 access("/etc/ld.so.preload", R_OK) = -1 ENOENT (No such file or directory)
10492 open("/etc/ld.so.cache", O_RDONLY) = 3
10492 fstat64(3, {st_mode=S_IFREG|0644, st_size=68880, ...}) = 0
10492 mmap2(NULL, 68880, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7f11000
10492 close(3)                          = 0
10492 access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
10492 open("/lib/tls/i686/cmov/libc.so.6", O_RDONLY) = 3
10492 read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\20Z\1\000"..., 512) = 512
10492 fstat64(3, {st_mode=S_IFREG|0755, st_size=1248904, ...}) = 0
10492 mmap2(NULL, 1258876, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7ddd000
10492 mmap2(0xb7f0a000, 16384, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x12c) = 0xb7f0a000
10492 mmap2(0xb7f0e000, 9596, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7f0e000
10492 close(3)                          = 0
10492 mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7ddc000
10492 set_thread_area({entry_number:-1 -> 6, base_addr:0xb7ddc6b0, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}) = 0
10492 mprotect(0xb7f0a000, 8192, PROT_READ) = 0
10492 munmap(0xb7f11000, 68880)         = 0
10492 brk(0)                            = 0x8050000
10492 brk(0x8071000)                    = 0x8071000
10492 open("/usr/lib/locale/locale-archive", O_RDONLY|O_LARGEFILE) = -1 ENOENT (No such file or directory)
10492 open("/usr/share/locale/locale.alias", O_RDONLY) = 3
10492 fstat64(3, {st_mode=S_IFREG|0644, st_size=2586, ...}) = 0
10492 mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f21000
10492 read(3, "# Locale name alias data base.\n#"..., 4096) = 2586
10492 read(3, "", 4096)                 = 0
10492 close(3)                          = 0
10492 munmap(0xb7f21000, 4096)          = 0
10492 open("/usr/lib/locale/en_US.utf8/LC_CTYPE", O_RDONLY) = 3
10492 fstat64(3, {st_mode=S_IFREG|0644, st_size=208336, ...}) = 0
10492 mmap2(NULL, 208336, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7da9000
10492 close(3)                          = 0
10492 open("/usr/lib/gconv/gconv-modules.cache", O_RDONLY) = 3
10492 fstat64(3, {st_mode=S_IFREG|0644, st_size=25460, ...}) = 0
10492 mmap2(NULL, 25460, PROT_READ, MAP_SHARED, 3, 0) = 0xb7f1b000
10492 close(3)                          = 0
10492 open("/usr/lib/locale/en_US.utf8/LC_MESSAGES", O_RDONLY) = 3
10492 fstat64(3, {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
10492 close(3)                          = 0
10492 open("/usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES", O_RDONLY) = 3
10492 fstat64(3, {st_mode=S_IFREG|0644, st_size=52, ...}) = 0
10492 mmap2(NULL, 52, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7f1a000
10492 close(3)                          = 0
10492 open("/usr/lib/locale/en_US.utf8/LC_IDENTIFICATION", O_RDONLY) = 3
10492 fstat64(3, {st_mode=S_IFREG|0644, st_size=391, ...}) = 0
10492 mmap2(NULL, 391, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7f19000
10492 close(3)                          = 0
10492 open("/usr/lib/locale/en_US.utf8/LC_MEASUREMENT", O_RDONLY) = 3
10492 fstat64(3, {st_mode=S_IFREG|0644, st_size=23, ...}) = 0
10492 mmap2(NULL, 23, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7f18000
10492 close(3)                          = 0
10492 open("/usr/lib/locale/en_US.utf8/LC_TELEPHONE", O_RDONLY) = 3
10492 fstat64(3, {st_mode=S_IFREG|0644, st_size=59, ...}) = 0
10492 mmap2(NULL, 59, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7f17000
10492 close(3)                          = 0
10492 open("/usr/lib/locale/en_US.utf8/LC_ADDRESS", O_RDONLY) = 3
10492 fstat64(3, {st_mode=S_IFREG|0644, st_size=155, ...}) = 0
10492 mmap2(NULL, 155, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7f16000
10492 close(3)                          = 0
10492 open("/usr/lib/locale/en_US.utf8/LC_NAME", O_RDONLY) = 3
10492 fstat64(3, {st_mode=S_IFREG|0644, st_size=77, ...}) = 0
10492 mmap2(NULL, 77, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7f15000
10492 close(3)                          = 0
10492 open("/usr/lib/locale/en_US.utf8/LC_PAPER", O_RDONLY) = 3
10492 fstat64(3, {st_mode=S_IFREG|0644, st_size=34, ...}) = 0
10492 mmap2(NULL, 34, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7f14000
10492 close(3)                          = 0
10492 munmap(0xb7f14000, 34)            = 0
10492 open("/usr/lib/locale/en_US/LC_PAPER", O_RDONLY) = -1 ENOENT (No such file or directory)
10492 open("/usr/lib/locale/en.utf8/LC_PAPER", O_RDONLY) = -1 ENOENT (No such file or directory)
10492 open("/usr/lib/locale/en/LC_PAPER", O_RDONLY) = -1 ENOENT (No such file or directory)
10492 open("/usr/share/locale-langpack/en_US.utf8/LC_PAPER", O_RDONLY) = -1 ENOENT (No such file or directory)
10492 open("/usr/share/locale-langpack/en_US/LC_PAPER", O_RDONLY) = -1 ENOENT (No such file or directory)
10492 open("/usr/share/locale-langpack/en.utf8/LC_PAPER", O_RDONLY) = -1 ENOENT (No such file or directory)
10492 open("/usr/share/locale-langpack/en/LC_PAPER", O_RDONLY) = -1 ENOENT (No such file or directory)
10492 open("/usr/share/locale/en_US.utf8/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
10492 open("/usr/share/locale/en_US/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
10492 open("/usr/share/locale/en.utf8/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
10492 open("/usr/share/locale/en/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
10492 open("/usr/share/locale-langpack/en_US.utf8/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
10492 open("/usr/share/locale-langpack/en_US/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
10492 open("/usr/share/locale-langpack/en.utf8/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
10492 open("/usr/share/locale-langpack/en/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
10492 write(2, "locale: ", 8)           = 8
10492 write(2, "Cannot set LC_ALL to default loc"..., 35) = 35
10492 write(2, ": No such file or directory", 27) = 27
10492 write(2, "\n", 1)                 = 1
10492 fstat64(1, {st_mode=S_IFCHR|0620, st_rdev=makedev(136, 0), ...}) = 0
10492 mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f14000
10492 write(1, "LANG=en_US.utf8\n", 16) = 16
10492 write(1, "LC_CTYPE=\"en_US.utf8\"\n", 22) = 22
10492 write(1, "LC_NUMERIC=\"en_US.utf8\"\n", 24) = 24
10492 write(1, "LC_TIME=\"en_US.utf8\"\n", 21) = 21
10492 write(1, "LC_COLLATE=\"en_US.utf8\"\n", 24) = 24
10492 write(1, "LC_MONETARY=\"en_US.utf8\"\n", 25) = 25
10492 write(1, "LC_MESSAGES=\"en_US.utf8\"\n", 25) = 25
10492 write(1, "LC_PAPER=\"en_US.utf8\"\n", 22) = 22
10492 write(1, "LC_NAME=\"en_US.utf8\"\n", 21) = 21
10492 write(1, "LC_ADDRESS=\"en_US.utf8\"\n", 24) = 24
10492 write(1, "LC_TELEPHONE=\"en_US.utf8\"\n", 26) = 26
10492 write(1, "LC_MEASUREMENT=\"en_US.utf8\"\n", 28) = 28
10492 write(1, "LC_IDENTIFICATION=\"en_US.utf8\"\n", 31) = 31
10492 write(1, "LC_ALL=\n", 8)          = 8
10492 exit_group(0)                     = ?

```

So I assume I'm missing one of the files with ENOENT status for open, but....
Where to get them? Do I really  miss them or... 
I honestly do not know...

Help anyone?

---

