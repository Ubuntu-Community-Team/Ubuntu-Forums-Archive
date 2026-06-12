---
title: "[SOLVED] losetup always makes a read only loop device"
date: 2008-06-14
forum: General Help
---

### Post by kalesh7 on 2008-06-14
I am trying to create a loopback device and then add some files to that device.
the code used is
```

sudo losetup /dev/loop0 file.iso
sudo mount /dev/loop0 /mnt
sudo cp file_to_copy /mnt/file_to_copy

```
cp returns with an error that copy failed and it's a read only filesystem
from what I know it should setup a readonly if the -r option is given, but for some reason it always gives me a readonly filesystem.:(

any help appreciated.

---

### Post by cariboo on 2008-06-14
Give isomaster a try. There is an article about this program on Linux.com - link here:

[http://www.linux.com/feature/124565](http://www.linux.com/feature/124565)

Isomaster is in  the repositories, you can install it using Synaptic.

Jim

---

### Post by kalesh7 on 2008-06-14
thanks for your reply, however my requirements were a bit more than mounting iso files or such,
I found that mount has a loopback mount(still learning all the tons of commands lol) and works pretty well
for anyone else needing anything similar the command is 
```

mount file_to_mount mount_point -o loop=/dev/loop3

```
more options (such as type and blocksize and so on) are available but that does it for me

---

