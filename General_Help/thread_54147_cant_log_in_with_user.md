---
title: "cant log in with user"
date: 2005-08-03
forum: General Help
---

### Post by boazg on 2005-08-03
i have an odd problem of which i have so far spotted 3 symptoms:
1) is i log in as a non-root user i get "unable to cd /home/user" and am loged out. i can log in with root (i gave him a password with a livecd)
2) if as root i 'su user' or 'su - user' i get the error "no shell"
3) if i try to 'sudo' i get " sudo: can't open /etc/sudoers: Permission denied"

the home directories exists and their permissions are ok, /etc/passwd is in tact and permissions are ok. permissions of /etc/sudoers are ok.

i first noticed this when i was messing with CPAN, trying to remove Tk. i dont think it has anything to do with the problem

note: i use a kernel with the nitro patchset. i dont think this is the reason, because i have the same problem when i boot into the ubuntu kernel, and from a chroot from a liveCD.

i must say this is one of the oddest thing i've seen

hope to get help. thx
        boazg

---

### Post by boazg on 2005-08-03
forgot to mention, there were some similar problems in google, but all in languages i dont understand

---

### Post by boazg on 2005-08-03
UPDATE:
if i 'strace su boazg'
then

setuid32(1000)                          = 0
close(3)                                = 0
**execve("/bin/sh", ["sh"], [/* 23 vars */]) = -1 EACCES (Permission denied)**
open("/usr/share/locale/locale.alias", O_RDONLY) = -1 EACCES (Permission denied)
open("/usr/share/locale/en_GB/LC_MESSAGES/shadow.mo", O_RDONLY) = -1 EACCES (Permiss
ion denied)
open("/usr/share/locale/en/LC_MESSAGES/shadow.mo", O_RDONLY) = -1 EACCES (Permission
 denied)
open("/usr/share/locale-langpack/en_GB/LC_MESSAGES/shadow.mo", O_RDONLY) = -1 EACCES
 (Permission denied)
open("/usr/share/locale-langpack/en/LC_MESSAGES/shadow.mo", O_RDONLY) = -1 EACCES (P
ermission denied)
open("/usr/share/locale/en_US/LC_MESSAGES/shadow.mo", O_RDONLY) = -1 EACCES (Permiss
ion denied)
open("/usr/share/locale-langpack/en_US/LC_MESSAGES/shadow.mo", O_RDONLY) = -1 EACCES
 (Permission denied)
write(2, "No shell\n", 9No shell
)               = 9

similar result if i 'strace su - boazg'
permissions for /bin/sh are
lrwxrwxrwx  1 root root 4 2005-07-01 02:00 /bin/sh -> bash
-rwxr-xr-x  1 root root 643852 2005-01-13 23:44 /bin/bash

i made a suid bash, and it failed on:./bash: 
error while loading shared libraries: libncurses.so.5: cannot open shared object file: Permission denied

the disk passed fsck...

something is wrong, permissons aren't being executed correctly, but this happens for every kernel and livecd (chroot) i seem to run. why?

---

### Post by mitchmao on 2005-08-09
Having the same problem here.
Was messing with gnorrmalize-0.7.6 from source and installing with:
"checkinstall --nodoc -S ./install"
then removed the package with:
"dpkg -r gnormalize"
to install in my local repo but suddenly all the problems begun.
having all the problems of BOAZG
I think I'll need help.

Thanks

---

