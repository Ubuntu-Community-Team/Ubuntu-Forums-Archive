---
title: "SheepShaver error - Ubuntu 8.04"
date: 2008-05-21
forum: General Help
---

### Post by darkal on 2008-05-21
I was trying to compile from source SheepShaver [http://gwenole.beauchesne.info/en/projects/sheepshaver](http://gwenole.beauchesne.info/en/projects/sheepshaver)
I did everything as explained here [http://ubuntuforums.org/showthread.php?t=670336&highlight=sheepshaver](http://ubuntuforums.org/showthread.php?t=670336&highlight=sheepshaver)
Compilation went fine. After running SheepShaver I see GUI, can set the options etc., but after pressing "START" I get > SheepShaver error: 
Cannot map Low Memory Globals: Permission denied.

In the console there is a message before Sheepshaver quits:

> SheepShaver V2.3-Pre (May 21 2008) by Christian Bauer and Mar"c" Hellwig
The program 'SheepShaver' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 9 error_code 2 request_code 105 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
I was using SheepShaver earlier on different machine but this is the first time I see that error.
Has anyone had that problem? Any possible solutions?
Can anyone confirm that SheepShaver works on Ubuntu 8.04?

I run Ubuntu 8.04 i386 version.

Thx.

---

### Post by darkal on 2008-05-25
I have found the solution and hope it helps others.

The problem is closely related to Wine bug described there:
[https://bugs.launchpad.net/ubuntu/+source/wine/+bug/114025](https://bugs.launchpad.net/ubuntu/+source/wine/+bug/114025)

In the file /etc/syscl.conf there is:

> # protect bottom 64k of memory from mmap to prevent NULL-dereference
# attacks against potential future kernel security vulnerabilities.
# (Added in kernel 2.6.23.)
vm.mmap_min_addr = 65536
 
Changing the line to [COLOR="Red"]vm.mmap_min_addr = 0[/COLOR] makes SheepShaver start without problems.

Solution can be checked fast by writing in console:

```
sudo sysctl -w vm.mmap_min_addr=0
```

If Sheepshaver starts, then sysctl.conf file can be edited.

---

