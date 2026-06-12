---
title: "[SOLVED] qemu assertion problem"
date: 2007-09-06
forum: General Help
---

### Post by Bothered on 2007-09-06
I am running qemu 0.8.2 with kqemu installed according to the guide [here]("https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo"). I have an NTFS partition mounted to /shared using ntfs-3g that is used to share files between Windows and ubuntu, and want to be able use that partition on virtualised operating systems. I have tried to use the fat:rw: option, but get the following assertion failure:

```
qemu -hda fat:rw:/shared -cdrom KNOPPIX5.1.1DVD.iso -boot d -m 384 -k en-gb -soundhw es1370 -localtime

```

```
qemu: /build/buildd/qemu-0.8.2+dfsg/block-vvfat.c:97: array_get: Assertion `index < array->next' failed.
Aborted (core dumped)

```

I know that I can use the partition directly using -hda /dev/[drive], but that requires running qemu with root privileges, which I don't want to do. I also don't really want to create a new shared fat partition. Any ideas how I can get around this problem?

EDIT: One more thing, I have tried using qemu 0.9 using the package in the repository mentioned in [this]("http://tech.tolero.org/blog/en/linux/qemu-9-and-kqemu-for-ubuntu-dapper-edgy-feisty") blog entry, and suffered from the same problem.

---

### Post by Bothered on 2007-09-06
I've found the problem, but still don't know how to get around it:

[qemu 0.8.2 : abort: assertion failed]("http://qemu-forum.ipi.fi/viewtopic.php?t=2596")

---

### Post by Bothered on 2007-09-07
The solution to the problem is to use a built-in smb server.

---

### Post by Bothered on 2007-09-09
Just a quick note for anyone else who tries this: I was unable to get the -smb for qemu to work, but managed to share the directory using my main samba server and then accessing the server at 10.0.2.2.

---

