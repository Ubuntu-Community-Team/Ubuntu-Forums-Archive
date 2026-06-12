---
title: "setuid not working for rdiff-backup"
date: 2007-10-07
forum: General Help
---

### Post by hollerith on 2007-10-07
I'm using rdiff-backup.  I want xscreensaver to run a local incremental backup of / for me - no SSH.  sudo asks for a password which is no good since I'm not around to type it in.  I want many incremental backups.  I've setuid on `which rdiff-backup` (I'm not crazy about the idea please don't bleat on about security).  I've tried chmod/chown &c on the target (a huge external Maxtor).  I even tried setuid on script which calls rdiff-backup but I get the same results:

```
Exception '[Errno 1] Operation not permitted: '/media/disk-1/backup'' raised of class '<type 'exceptions.OSError'>':
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 295, in error_check_Main
    try: Main(arglist)
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 315, in Main
    take_action(rps)
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 271, in take_action
    elif action == "backup": Backup(rps[0], rps[1])
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 324, in Backup
    backup_set_rbdir(rpin, rpout)
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 381, in backup_set_rbdir
    rpout.chmod(0700) # just make sure permissions aren't too lax
  File "/var/lib/python-support/python2.5/rdiff_backup/rpath.py", line 826, in chmod
    self.conn.os.chmod(self.path, permissions & Globals.permission_mask)
Traceback (most recent call last):
  File "/usr/bin/rdiff-backup", line 23, in <module>
    rdiff_backup.Main.error_check_Main(sys.argv[1:])
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 295, in error_check_Main
    try: Main(arglist)
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 315, in Main
    take_action(rps)
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 271, in take_action
    elif action == "backup": Backup(rps[0], rps[1])
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 324, in Backup
    backup_set_rbdir(rpin, rpout)
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 381, in backup_set_rbdir
    rpout.chmod(0700) # just make sure permissions aren't too lax
  File "/var/lib/python-support/python2.5/rdiff_backup/rpath.py", line 826, in chmod
    self.conn.os.chmod(self.path, permissions & Globals.permission_mask)
OSError: [Errno 1] Operation not permitted: '/media/disk-1/backup'

```

If its running as root why is it getting permissions problems?

---

### Post by MeanderingCode on 2007-11-17
I, too, am having similar issues...

small script that, among other things, moves a file in /etc.

Its permissions (script) are 4754, ownership root:me, but mv returns a permission denied.

I've tried other variations (most notably setting root:root ownership, executable by all, and setuid and setgid alone and together) to no avail.

Someone?

===============================
EDIT:

So, i just after posting read that the kernel doesn't like executing scripts as setuid because of the ['race condition']("http://en.wikipedia.org/wiki/Race_condition").

My new question is:  Any pointers on how to get this done, anyway? (writing and compiling a C program would require pulling out that old textbook and dredging through stuff i never learned, so i would rather do it by hand if that's my only option)

---

### Post by roelpeeters on 2007-11-17
How did you mount your drive? What kind of file system is it running? If the Maxtor has a FAT32 filesystem (which does not recognize or use permissions) these commands will fail. The default linux file system is ext3 which provides for permissions.

---

### Post by MeanderingCode on 2007-11-18
> **roelpeeters said:**
> How did you mount your drive? What kind of file system is it running? If the Maxtor has a FAT32 filesystem (which does not recognize or use permissions) these commands will fail. The default linux file system is ext3 which provides for permissions.

Are you asking me?  I'm sorry if i wasn't clear, but the permissions took...it is on ext3, btw.
the link in my other post describes what's known as the ["race condition"]("http://en.wikipedia.org/wiki/Race_condition") (Wikipedia.org) that is the reason the linux kernel won't let scripts which are parsed upon execution (as opposed to something already compiled into a binary) execute with setuid or setgid.

My question is: can i "package" or compile bash scripts or ruby/perl/python scripts so i *can* setuid them; i don't currently have the time to add learning another language to my plate (only looked at C++ for three months...6 years ago...been longer since i wrote in BASIC (that doesn't compile, does it?)

---

### Post by roelpeeters on 2007-11-20
I am sorry, I must have misread your question. You could try the following.

1. Create a simple C program that launches your script:

```

#include <stdlib.h>

int main()
{
        system("./myscript.sh");
        return 0;
}

```

2. Compile with:
```

g++ mypgm.cpp -o mypgm

```

3. Change permissions and owner with:
```

sudo chown root mypgm
sudo chmod +xs mypgm

```

Then run the program mypgm. The system statement in your program will launch your script.

On a side note, most BASIC dialects are not compiled but interpreted. C++ is compiled.

Hope this solves your problem.

---

