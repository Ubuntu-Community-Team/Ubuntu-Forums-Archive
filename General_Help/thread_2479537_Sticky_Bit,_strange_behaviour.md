---
title: "Sticky Bit, strange behaviour"
date: 2022-09-28
forum: General Help
---

### Post by inktvis75 on 2022-09-28
Hi, can someone explain this to me? For so far as I know, this is the opposite of how the sticky bit should work.

```

ubuntu@lpi100:~$ hostnamectl
 Static hostname: lpi100
       Icon name: computer-vm
         Chassis: vm
      Machine ID: 7c702c7e4b5f4a8dab9c7eec8e10e15b
         Boot ID: af0f80a311594331a2324403b6f2338a
  Virtualization: kvm
Operating System: Ubuntu 22.04.1 LTS
          Kernel: Linux 5.15.0-48-generic
    Architecture: x86-64
 Hardware Vendor: RDO
  Hardware Model: OpenStack Compute

ubuntu@lpi100:~$ stat /tmp
  File: /tmp
  Size: 4096      	Blocks: 8          IO Block: 4096   directory
Device: 801h/2049d	Inode: 1552        Links: 14
Access: (1777/drwxrwxrwt)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2022-09-28 13:37:29.647025467 +0000
Modify: 2022-09-28 14:16:25.640716177 +0000
Change: 2022-09-28 14:16:25.640716177 +0000
 Birth: 2022-09-21 11:29:23.061330463 +0000

ubuntu@lpi100:~$ touch /tmp/file1

ubuntu@lpi100:~$ sudo chmod 777 /tmp/file1

ubuntu@lpi100:~$ stat /tmp/file1
  File: /tmp/file1
  Size: 0               Blocks: 0          IO Block: 4096   regular empty file
Device: 801h/2049d      Inode: 7443        Links: 1
Access: (0777/-rwxrwxrwx)  Uid: ( 1000/  ubuntu)   Gid: ( 1000/  ubuntu)
Access: 2022-09-28 13:42:48.263466289 +0000
Modify: 2022-09-28 13:42:48.263466289 +0000
Change: 2022-09-28 13:43:15.947503162 +0000
 Birth: 2022-09-28 13:42:48.263466289 +0000

ubuntu@lpi100:~$ su student
Password:

student@lpi100:/home/ubuntu$ echo hallo2 >> /tmp/file1
bash: /tmp/file1: Permission denied

student@lpi100:/home/ubuntu$ sudo rm /tmp/file1

student@lpi100:/home/ubuntu$ stat /tmp/file1
stat: cannot statx '/tmp/file1': No such file or directory

```

---

### Post by TheFu on 2022-09-28
Don't know what you think those commands are showing.  I  don't see it. Please explain what you expected to happen and how it didn't happen.

The sticky bit is often confused with the setuid and setgid bits.

The sticky bit just prevents other users (except root) from deleting a file or directory who's parent directory has the +t bit set, even if the permissions are 777.  As always, permissions don't matter for root.  It will also force a file to be cached always, making for faster reads when it is accessed on non-directory file system objects.

From the manpage:
```
RESTRICTED DELETION FLAG OR STICKY BIT
       The restricted deletion flag or sticky bit is a single bit, whose interpreta&#8208;
       tion  depends  on  the  file type.  For directories, it prevents unprivileged
       users from removing or renaming a file in the directory unless they  own  the
       file  or  the  directory; this is called the restricted deletion flag for the
       directory, and is commonly found on  world-writable  directories  like  /tmp.
       For regular files on some older systems, the bit saves the program's text im&#8208;
       age on the swap device so it will load more quickly when run; this is  called
       the sticky bit.
```

---

### Post by inktvis75 on 2022-09-29
As you can see in my code, the sticky bit in this version of Ubuntu allows to delete the file, if you have the correct permissions ( for instance 777), but you are not allowed to write into it

---

### Post by The Cog on 2022-09-29
Student used sudo to delete the file - so root deleted it, not the student. No problems there.

This puzzles me - I would expect appending to an existing file to be allowed:
```
student@lpi100:/home/ubuntu$ echo hallo2 >> /tmp/file1
bash: /tmp/file1: Permission denied
```

---

### Post by inktvis75 on 2022-09-29
you're right, the "sudo rm" is my mistake ... but sticky bit is still not working as expected

---

### Post by TheFu on 2022-09-29
> **inktvis75 said:**
> you're right, the "sudo rm" is my mistake ... but sticky bit is still not working as expected

I tested on 18.04 and 20.04, because that's what I had handy.
18:04 the append worked after I made the file permissions 777 ... which I'd never do in the real world.  That's just lazy.
20.04 the append did not work with 666 or 777 permissions. Got a permission denied error.

So, something changed between those releases.  I know that some security changes happened related to access of logs and dmesg output. 

Ah ... the web answers: [https://stackoverflow.com/questions/70479857/should-posix-sticky-bit-deny-appending-by-root](https://stackoverflow.com/questions/70479857/should-posix-sticky-bit-deny-appending-by-root)
Solution:
   sudo sysctl fs.protected_regular=0

Some security vulnerabilities were closed by changing kernel defaults [https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/commit/?id=30aba6656f61ed44cba445a3c0d38b296fa9e8f5](https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/commit/?id=30aba6656f61ed44cba445a3c0d38b296fa9e8f5)   multiple CVEs were closed.

On 18.04:
```
$ sudo sysctl fs.protected_regular
fs.protected_regular = 0
```

On 20.04:
```
$ sudo sysctl fs.protected_regular
fs.protected_regular = 2
```

Seems like that change may be relevant.  I didn't change the default back to 0. Feel free, but know that 8 closed CVEs depend on this change.

---

### Post by The Cog on 2022-09-29
Thanks for that insight. I had been thinking maybe it was because append (in bash like that) was doing a create new file, delete old file, rename new file switcheroo. That would surprise me though, when o_append would be so much easier. 
If it's closing a security hole then I'm happy to go with that, although perhaps the docs on the sticky bit could use another paragraph.

---

### Post by TheFu on 2022-09-29
> **The Cog said:**
> Thanks for that insight. I had been thinking maybe it was because append (in bash like that) was doing a create new file, delete old file, rename new file switcheroo. That would surprise me though, when o_append would be so much easier. 
If it's closing a security hole then I'm happy to go with that, although perhaps the docs on the sticky bit could use another paragraph.

But the change was made outside the chmod command, in the kernel and not all kernels make that setting the default. An update to the chmod which points to the kernel dependency might be useful on Linux, but I suspect the GNU team behind chmod wouldn't make that modification.  It would be a distro or Linux-specific thing, perhaps?

---

### Post by inktvis75 on 2022-09-30
Wow, thank you very much !!!

---

### Post by TheFu on 2022-09-30
> **inktvis75 said:**
> Wow, thank you very much !!!

Good to know we aren't going crazy when things that vaguely seemed to work previously don't any more.  It was dumb luck that I found that weblink AND that it was relevant.  

If my testing didn't actually show what you were saying, I'd have stopped looking.

---

