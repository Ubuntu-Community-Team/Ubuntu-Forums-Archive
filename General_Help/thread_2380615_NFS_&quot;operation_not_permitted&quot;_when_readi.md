---
title: "NFS &quot;operation not permitted&quot; when reading or creating files"
date: 2017-12-19
forum: General Help
---

### Post by sparkee2 on 2017-12-19
We've got a situation where our Ubuntu NFS functionality seems to degrade over time. Generally these situations are fixable with unmounting/remounting. In this instance of the problem, an NFS client/server relationship will function well and then at some point the permissions seem to break with "Operation not permitted" messages.

After the point in time at which the NFS permissions go goofy this way, a user can't read or create files on the mount. These fail with "Operation not permitted":
[FONT=&quot]  echo hi > /ws/jenkins/hi.txt[/FONT]
[FONT=&quot]  wc -c /ws/jenkins/otherfile.txt[/FONT]
[FONT=&quot]  cat /ws/jenkins/otherfile.txt[/FONT]


These work fine on this same mount:
[FONT=&quot]  chmod[/FONT]
[FONT=&quot]  chgrp[/FONT]
[FONT=&quot]  mv[/FONT]
[FONT=&quot]  rm[/FONT]
[FONT=&quot]  mkdir[/FONT]
[FONT=&quot]  rmdir[/FONT]



NFS client: 16.04.3 LTS (Xenial Xerus)
hostname: buildnode-23
Here are the mounts that are not managed by autofs:
[FONT=courier new]  # egrep -v '^#|^$' /etc/fstab[/FONT]
[FONT=courier new]  /dev/sda1                               /                      ext4    defaults             0 1[/FONT]
[FONT=courier new]  /dev/sda5                               none                   swap    sw                   0 0[/FONT]
[FONT=courier new]  LABEL=DATA                              /disk/data             ext4    defaults             0 0[/FONT]
[FONT=courier new]  /disk/data                              /ws                    none    defaults,bind,nofail 0 0[/FONT]
[FONT=courier new]  filesvr:/disk/data1/jenkins             /ws/jenkins            nfs defaults                 0 0[/FONT]
[FONT=courier new]  filesvr:/disk/data4/jenkins_build_logs  /ws/jenkins_build_logs nfs defaults                 0 0[/FONT]
[FONT=courier new]  #[/FONT]


NFS server: 14.04.5 LTS, Trusty Tahr
Hostname: filesvr
Server exports include this entry:
[FONT=courier new]/disk/data1/jenkins \[/FONT]
[FONT=courier new]    @netgrp1(rw,no_auth_nlm,insecure,async,no_subtree_check) \[/FONT]
[FONT=courier new]    @netgrp2(rw,no_auth_nlm,insecure,async,no_subtree_check) \[/FONT]
[FONT=courier new]    @netgrp3(ro,no_auth_nlm,insecure,async,no_subtree_check)[/FONT]
And we can see the client in the two rw netgroups:
[FONT=courier new]  # getent netgroup netgrp1 | tr ' ' '\012' |  grep -i buildnode-23[/FONT]
[FONT=courier new]  (buildnode-23.rose.rdlabs.hpecorp.net,-,)[/FONT]
[FONT=courier new]  # getent netgroup netgrp2 | tr ' ' '\012' |  grep -i buildnode-23[/FONT]
[FONT=courier new]  (buildnode-23.rose.rdlabs.hpecorp.net,-,)[/FONT]
[FONT=courier new]  # getent netgroup netgrp3 | tr ' ' '\012' |  grep -i buildnode-23[/FONT]
[FONT=courier new]  #[/FONT]


This is an NIS environment. The output of these commands is identical on both client and server:
[FONT=courier new]  # grep swbuildn /etc/passwd[/FONT]
[FONT=courier new]  # ypmatch swbuildn passwd | cut -d: -f1,3-[/FONT]
[FONT=courier new]  swbuildn:30124:2000:Jenkins Build Master:/users/swbuildn:/bin/bash[/FONT]


Permissions are good to experiment here and in subdirs:
[FONT=courier new]  # pwd[/FONT]
[FONT=courier new]  /ws/jenkins[/FONT]
[FONT=courier new]  # ls -la[/FONT]
[FONT=courier new]  total 344[/FONT]
[FONT=courier new]  drwxr-xr-x  13 swbuildn devs   4096 Dec 19 13:37 .[/FONT]
[FONT=courier new]  drwxr-xr-x   6 root     root   4096 Jan 18  2017 ..[/FONT]
[FONT=courier new]  drwxrwxr-x 480 swbuildn devs  36864 Dec 19 13:36 build_platform[/FONT]
[FONT=courier new]  drwxr-xr-x 230 swbuildn devs  65536 Dec 19 13:34 build_platform_coverity[/FONT]
[FONT=courier new]  drwxr-xr-x 542 swbuildn devs 122880 Dec 19 13:30 func_test[/FONT]
[FONT=courier new]  drwxr-xr-x 375 swbuildn devs  16384 Dec 19 12:38 lib[/FONT]
[FONT=courier new]  drwxrwxr-x   2 swbuildn devs   4096 Dec 18 12:02 test[/FONT]
[FONT=courier new]  drwxrwxrwx   6 swbuildn devs   4096 Aug 14 16:07 tools[/FONT]
as this user:
[FONT=courier new]  # id[/FONT]
[FONT=courier new]  uid=30124(swbuildn) gid=2000(devs) groups=2000(devs),1003(locallogin)[/FONT]


In case it illuminates anything, here's an strace of a simple "cat" command:


[FONT=courier new]  # strace cat *envfile[/FONT]
[FONT=courier new]  execve("/bin/cat", ["cat", "tf.envfile"], [/* 33 vars */]) = 0[/FONT]
[FONT=courier new]  brk(NULL)                               = 0x24c4000[/FONT]
[FONT=courier new]  access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)[/FONT]
[FONT=courier new]  mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f66baf15000[/FONT]
[FONT=courier new]  access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)[/FONT]
[FONT=courier new]  open("/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 3[/FONT]
[FONT=courier new]  fstat(3, {st_mode=S_IFREG|0644, st_size=46393, ...}) = 0[/FONT]
[FONT=courier new]  mmap(NULL, 46393, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f66baf09000[/FONT]
[FONT=courier new]  close(3)                                = 0[/FONT]
[FONT=courier new]  access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)[/FONT]
[FONT=courier new]  open("/lib/x86_64-linux-gnu/libc.so.6", O_RDONLY|O_CLOEXEC) = 3[/FONT]
[FONT=courier new]  read(3, "\177ELF\2\1\1\3\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0P\t\2\0\0\0\0\0"..., 832) = 832[/FONT]
[FONT=courier new]  fstat(3, {st_mode=S_IFREG|0755, st_size=1868984, ...}) = 0[/FONT]
[FONT=courier new]  mmap(NULL, 3971488, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f66ba928000[/FONT]
[FONT=courier new]  mprotect(0x7f66baae8000, 2097152, PROT_NONE) = 0[/FONT]
[FONT=courier new]  mmap(0x7f66bace8000, 24576, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1c0000) = 0x7f66bace8000[/FONT]
[FONT=courier new]  mmap(0x7f66bacee000, 14752, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f66bacee000[/FONT]
[FONT=courier new]  close(3)                                = 0[/FONT]
[FONT=courier new]  mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f66baf08000[/FONT]
[FONT=courier new]  mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f66baf07000[/FONT]
[FONT=courier new]  mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f66baf06000[/FONT]
[FONT=courier new]  arch_prctl(ARCH_SET_FS, 0x7f66baf07700) = 0[/FONT]
[FONT=courier new]  mprotect(0x7f66bace8000, 16384, PROT_READ) = 0[/FONT]
[FONT=courier new]  mprotect(0x60b000, 4096, PROT_READ)     = 0[/FONT]
[FONT=courier new]  mprotect(0x7f66baf17000, 4096, PROT_READ) = 0[/FONT]
[FONT=courier new]  munmap(0x7f66baf09000, 46393)           = 0[/FONT]
[FONT=courier new]  brk(NULL)                               = 0x24c4000[/FONT]
[FONT=courier new]  brk(0x24e5000)                          = 0x24e5000[/FONT]
[FONT=courier new]  open("/usr/lib/locale/locale-archive", O_RDONLY|O_CLOEXEC) = 3[/FONT]
[FONT=courier new]  fstat(3, {st_mode=S_IFREG|0644, st_size=2981280, ...}) = 0[/FONT]
[FONT=courier new]  mmap(NULL, 2981280, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f66ba650000[/FONT]
[FONT=courier new]  close(3)                                = 0[/FONT]
[FONT=courier new]  fstat(1, {st_mode=S_IFCHR|0600, st_rdev=makedev(136, 0), ...}) = 0[/FONT]
[FONT=courier new]  open("tf.envfile", O_RDONLY)      = -1 EPERM (Operation not permitted)[/FONT]
[FONT=courier new]  write(2, "cat: ", 5cat: )                    = 5[/FONT]
[FONT=courier new]  write(2, "tf.envfile", 16tf.envfile)        = 16[/FONT]
[FONT=courier new]  open("/usr/share/locale/locale.alias", O_RDONLY|O_CLOEXEC) = 3[/FONT]
[FONT=courier new]  fstat(3, {st_mode=S_IFREG|0644, st_size=2995, ...}) = 0[/FONT]
[FONT=courier new]  read(3, "# Locale name alias data base.\n#"..., 4096) = 2995[/FONT]
[FONT=courier new]  read(3, "", 4096)                       = 0[/FONT]
[FONT=courier new]  close(3)                                = 0[/FONT]
[FONT=courier new]  open("/usr/share/locale/en_US.UTF-8/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)[/FONT]
[FONT=courier new]  open("/usr/share/locale/en_US.utf8/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)[/FONT]
[FONT=courier new]  open("/usr/share/locale/en_US/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)[/FONT]
[FONT=courier new]  open("/usr/share/locale/en.UTF-8/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)[/FONT]
[FONT=courier new]  open("/usr/share/locale/en.utf8/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)[/FONT]
[FONT=courier new]  open("/usr/share/locale/en/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)[/FONT]
[FONT=courier new]  open("/usr/share/locale-langpack/en_US.UTF-8/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)[/FONT]
[FONT=courier new]  open("/usr/share/locale-langpack/en_US.utf8/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)[/FONT]
[FONT=courier new]  open("/usr/share/locale-langpack/en_US/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)[/FONT]
[FONT=courier new]  open("/usr/share/locale-langpack/en.UTF-8/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)[/FONT]
[FONT=courier new]  open("/usr/share/locale-langpack/en.utf8/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)[/FONT]
[FONT=courier new]  open("/usr/share/locale-langpack/en/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)[/FONT]
[FONT=courier new]  write(2, ": Operation not permitted", 25: Operation not permitted) = 25[/FONT]
[FONT=courier new]  write(2, "\n", 1[/FONT]
[FONT=courier new]  )                       = 1[/FONT]
[FONT=courier new]  close(1)                                = 0[/FONT]
[FONT=courier new]  close(2)                                = 0[/FONT]
[FONT=courier new]  exit_group(1)                           = ?[/FONT]
[FONT=courier new]  +++ exited with 1 +++[/FONT]
  
Any ideas? I'll experiment with mounting on the hard drive instead of onto the bind mount.

---

### Post by sparkee2 on 2018-02-05
Hoping for any helpful thoughts, please. Responding just to keep this thread alive. Thanks in advance!

---

