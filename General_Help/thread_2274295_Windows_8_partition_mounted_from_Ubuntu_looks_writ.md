---
title: "Windows 8 partition mounted from Ubuntu looks writeable, but it's not"
date: 2015-04-19
forum: General Help
---

### Post by larsen.online on 2015-04-19
I'm remotely mounting a Windows 8 partition from Ubuntu 14.04.2 with this line in fstab:
  ```
//192.168.2.110/D /mountpoint  cifs username=myname,password=mypass,iocharset=utf8,gid=1000,uid=1000,file_mode=0777,dir_mode=0777 0 0

```  This mounts the partition just fine and I am able to read the files.  When I look at the file permissions, it looks as if I should be able to  write to the partition, too:
  ```
-rwxrwxrwx  1 myuser mygroup       0 Mär 10 08:43 test.txt*

```  The containing folder has the same permissions. Nevertheless I can´t remove the file, nor can I create one:
  ```
$ rm test.txt
rm: cannot remove ‘test.txt’: Permission denied

$ touch blah
touch: cannot touch ‘blah’: Permission denied

```  I get this result as myuser and as root.  Can anyone tell me what I need to do to get write access on this partition?  Many thanks!

---

### Post by Mark Phelps on 2015-04-19
IF this partition contains the Win8 OS files -- it is doing you a favor by NOT letting you write to it or otherwise make changes to it.  You should only mount an OS partition read-only.

If it's a data only partition, then check in Win8 to ensure that you have disabled FastStartup -- that is NOT the same as Fast Boot.

Also, when you leave Win8, make sure you choose Shut Down, not Restart, because the latter automatically enables hibernation.

---

### Post by larsen.online on 2015-04-19
Thank you, Mark.  That's done it.

---

