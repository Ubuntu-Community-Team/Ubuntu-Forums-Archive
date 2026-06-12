---
title: "Long Pauses Starting Firefox and Abiword in Feisty"
date: 2007-07-16
forum: General Help
---

### Post by Jaguar0616 on 2007-07-16
Hello all, I'll appreciate any help with this:

In Feisty, Firefox hangs up for 30 sec in the middle of it's startup sequence and then finishes launching and runs without any further issues.
Here's a snip from "strace firefox":

open("/usr/lib/gconv/UTF-16.so", O_RDONLY) = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\20\4\0"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0644, st_size=9488, ...}) = 0
mmap2(NULL, 12328, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0xb72a4000
mmap2(0xb72a6000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x1) = 0xb72a6000
close(4)                                = 0
stat64("/home/tyilk/.mozilla/firefox/evoevsi8.default", {st_mode=S_IFDIR|0700, st_size=4096, ...}) = 0
open("/home/tyilk/.mozilla/firefox/evoevsi8.default/.parentlock", O_WRONLY|O_CREAT|O_TRUNC, 0666) = 4
fcntl64(4, F_GETLK, {type=F_UNLCK, whence=SEEK_SET, start=0, len=0, pid=3217434952}) = 0
[B]fcntl64(4, F_SETLK, {type=F_WRLCK, whence=SEEK_SET, start=0, len=0}
[/B]

It's the second fcntl that it hangs on.


Abiword starts up okay, hangs for 60 sec. with the first character entry but then runs without any delays after that.
Here's a snip from "strace abiword":

munmap(0xb6fd6000, 4096)                = 0
close(8)                                = 0
read(7, "", 4096)                       = 0
close(7)                                = 0
munmap(0xb7f9d000, 4096)                = 0
close(6)                                = 0
stat64("/home/tyilk/.aspell.en.pws", {st_mode=S_IFREG|0644, st_size=22, ...}) = 0
access("/home/tyilk/.aspell.en.pws", F_OK) = 0
open("/home/tyilk/.aspell.en.pws", O_RDONLY) = 6
**fcntl64(6, F_SETLKW, {type=F_RDLCK, whence=SEEK_SET, start=0, len=0}) = -1 ENOLCK (No locks available)**
fstat64(6, {st_mode=S_IFREG|0644, st_size=22, ...}) = 0
mmap2(NULL, 32768, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb5f0d000
read(6, "personal_ws-1.1 en 0 \n", 32768) = 22
read(6, "", 32768)                      = 0
fstat64(6, {st_mode=S_IFREG|0644, st_size=22, ...}) = 0
fstat64(6, {st_mode=S_IFREG|0644, st_size=22, ...}) = 0
close(6)                                = 0
munmap(0xb5f0d000, 32768)               = 0
stat64("/home/tyilk/.aspell.en.prepl", {st_mode=S_IFREG|0644, st_size=24, ...}) = 0
access("/home/tyilk/.aspell.en.prepl", F_OK) = 0
open("/home/tyilk/.aspell.en.prepl", O_RDONLY) = 6
**fcntl64(6, F_SETLKW, {type=F_RDLCK, whence=SEEK_SET, start=0, len=0}**

It hangs on each fcntl64 call for 30 sec.


The /home directory that both of these access is shared over a network using nfs and, since I don't get these hang ups logged in as the machine's root, the problem seems to be there somehow.

Anyone have any further ideas on the cause and a fix?

Thank you!

---

### Post by stchman on 2007-07-16
> **Jaguar0616 said:**
> Hello all, I'll appreciate any help with this:

In Feisty, Firefox hangs up for 30 sec in the middle of it's startup sequence and then finishes launching and runs without any further issues.
Here's a snip from "strace firefox":

open("/usr/lib/gconv/UTF-16.so", O_RDONLY) = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\20\4\0"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0644, st_size=9488, ...}) = 0
mmap2(NULL, 12328, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0xb72a4000
mmap2(0xb72a6000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x1) = 0xb72a6000
close(4)                                = 0
stat64("/home/tyilk/.mozilla/firefox/evoevsi8.default", {st_mode=S_IFDIR|0700, st_size=4096, ...}) = 0
open("/home/tyilk/.mozilla/firefox/evoevsi8.default/.parentlock", O_WRONLY|O_CREAT|O_TRUNC, 0666) = 4
fcntl64(4, F_GETLK, {type=F_UNLCK, whence=SEEK_SET, start=0, len=0, pid=3217434952}) = 0
[B]fcntl64(4, F_SETLK, {type=F_WRLCK, whence=SEEK_SET, start=0, len=0}
[/B]

It's the second fcntl that it hangs on.


Abiword starts up okay, hangs for 60 sec. with the first character entry but then runs without any delays after that.
Here's a snip from "strace abiword":

munmap(0xb6fd6000, 4096)                = 0
close(8)                                = 0
read(7, "", 4096)                       = 0
close(7)                                = 0
munmap(0xb7f9d000, 4096)                = 0
close(6)                                = 0
stat64("/home/tyilk/.aspell.en.pws", {st_mode=S_IFREG|0644, st_size=22, ...}) = 0
access("/home/tyilk/.aspell.en.pws", F_OK) = 0
open("/home/tyilk/.aspell.en.pws", O_RDONLY) = 6
**fcntl64(6, F_SETLKW, {type=F_RDLCK, whence=SEEK_SET, start=0, len=0}) = -1 ENOLCK (No locks available)**
fstat64(6, {st_mode=S_IFREG|0644, st_size=22, ...}) = 0
mmap2(NULL, 32768, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb5f0d000
read(6, "personal_ws-1.1 en 0 \n", 32768) = 22
read(6, "", 32768)                      = 0
fstat64(6, {st_mode=S_IFREG|0644, st_size=22, ...}) = 0
fstat64(6, {st_mode=S_IFREG|0644, st_size=22, ...}) = 0
close(6)                                = 0
munmap(0xb5f0d000, 32768)               = 0
stat64("/home/tyilk/.aspell.en.prepl", {st_mode=S_IFREG|0644, st_size=24, ...}) = 0
access("/home/tyilk/.aspell.en.prepl", F_OK) = 0
open("/home/tyilk/.aspell.en.prepl", O_RDONLY) = 6
**fcntl64(6, F_SETLKW, {type=F_RDLCK, whence=SEEK_SET, start=0, len=0}**

It hangs on each fcntl64 call for 30 sec.


The /home directory that both of these access is shared over a network using nfs and, since I don't get these hang ups logged in as the machine's root, the problem seems to be there somehow.

Anyone have any further ideas on the cause and a fix?

Thank you!
I had a similar problem with applications taking forever to launch, here is how I fixed it:

[http://www.stchman.com/conf_host.html](http://www.stchman.com/conf_host.html)

It seems as though if the DNS are lousy that Ubuntu can take a long time doing whatever it needs to do.

---

### Post by Jaguar0616 on 2007-07-16
Thanks for the reply, you have:

-- snip --
[FONT="Courier New"]The only line your hosts file should have is the following:

127.0.0.1 localhost bob-laptop
[/FONT]

I've also seen people say that the hosts file needs to have a line like:

[FONT="Courier New"]127.0.1.1 bob-laptop[/FONT]

for some Ubuntu specific reason, though putting my hosts file through its permutations hasn't made any difference on my setup. Any other suggestions?

Thanks!

---

