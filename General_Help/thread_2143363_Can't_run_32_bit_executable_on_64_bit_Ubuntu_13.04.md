---
title: "Can't run 32 bit executable on 64 bit Ubuntu 13.04"
date: 2013-05-08
forum: General Help
---

### Post by paddyjoy on 2013-05-08
Hi everyone,

This problem has really got me stumped, hoping someone can help me out.

I am trying to run a 32 bit executable in ubuntu 64 bit and I'm getting a strange permission deined error.

```

paddy@PJ-UB:~/Downloads$ sudo "./MPLABX-v1_70-linux-installer.run"
sudo: unable to execute ./MPLABX-v1_70-linux-installer.run: Permission denied
```

File is executable
  ```

-rwxrwxr-x  1 paddy paddy  264M May  6 13:03 MPLABX-v1_70-linux-installer.run
```

32 bit libraries are installed

```
paddy@PJ-UB:~/Downloads$ sudo apt-get install libc6:i386 ia32-libs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ia32-libs is already the newest version.
libc6:i386 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded


```

I have checked the checksum of the file and it is ok.

The file is from a legitimate source and nobody else seems to be having the same problem.

Any ideas?

Some other info on the file:
```

paddy@PJ-UB:~/Downloads$ ldd MPLABX-v1_70-linux-installer.run
    not a dynamic executable
``````

 
paddy@PJ-UB:~/Downloads$ sudo strace ./MPLABX-v1_70-linux-installer.run
execve("./MPLABX-v1_70-linux-installer.run", ["./MPLABX-v1_70-linux-installer.r"...], [/* 18 vars */]) = -1 EACCES (Permission denied)
dup(2)                                  = 3
fcntl(3, F_GETFL)                       = 0x8002 (flags O_RDWR|O_LARGEFILE)
fstat(3, {st_mode=S_IFCHR|0620, st_rdev=makedev(136, 1), ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f75e435c000
lseek(3, 0, SEEK_CUR)                   = -1 ESPIPE (Illegal seek)
write(3, "strace: exec: Permission denied\n", 32strace: exec: Permission denied
) = 32
close(3)                                = 0
munmap(0x7f75e435c000, 4096)            = 0
exit_group(1)                           = ?
paddy@PJ-UB:~/Downloads$ file MPLABX-v1_70-linux-installer.run
MPLABX-v1_70-linux-installer.run: ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), statically linked, stripped
paddy@PJ-UB:~/Downloads$ 
```

---

### Post by monkeybrain2012 on 2013-05-08
Shouldn't it be


```
sudo ./"MPLABX-v1_70-linux-installer.run"
```?

---

### Post by paddyjoy on 2013-05-08
Maybe but it gives the same result.

```
paddy@PJ-UB:/data/Downloads$ sudo ./"MPLABX-v1_70-linux-installer.run"
sudo: unable to execute ./MPLABX-v1_70-linux-installer.run: Permission denied
paddy@PJ-UB:/data/Downloads$
```

---

### Post by paddyjoy on 2013-06-29
After two months I finally figures this out so just wanted to post the resolution in case anyone else has the same issue.

The 32 bit application wouldn't run because it was located on an ext4 parition that was mounted with noxec

Pity the ubuntu error message wasn't a little bit more descriptive.


  ```
/dev/sda7 on /data type ext4 (rw,noexec,nosuid,nodev)
```
  
    
    ```
lrwxrwxrwx   1 paddy paddy    16 Nov 22  2012 Downloads -> /data/Downloads/
```

---

