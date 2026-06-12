---
title: "adept_manager crashing"
date: 2008-04-05
forum: General Help
---

### Post by DaveTheAve on 2008-04-05
> 
david@devlon:~$ sudo adept_manager
QObject::connect: Use the SIGNAL macro to bind ::
kapture::PkgSystem::PkgSystem()
KCrash: Application 'adept_manager' crashing...
david@devlon:~$ konversation
Segmentation fault (core dumped)


Please any help would be great!!! I'm really stuck; I'm hoping doing the following for 8.04 will fix my system but I don't know:

> 
sudo apt-get update
sudo apt-get upgrade
sudo apt-get --dist-upgrade


P.S. MySQL won't start ether.... I'm a developer so thats important as well!

---

### Post by DaveTheAve on 2008-04-05
Here is a snippet from my mysqld error:

> 
david@devlon:~$ sudo mysqld
080405 13:33:34 - mysqld got signal 4;
This could be because you hit a bug. It is also possible that this binary
or one of the libraries it was linked against is corrupt, improperly built,
or misconfigured. This error can also be caused by malfunctioning hardware.
We will try our best to scrape up some info that will hopefully help diagnose
the problem, but since we have already crashed, something is definitely wrong
and this may fail.

key_buffer_size=0
read_buffer_size=131072
max_used_connections=0
max_connections=100
threads_connected=0
It is possible that mysqld could use up to
key_buffer_size + (read_buffer_size + sort_buffer_size)*max_connections = 217599 K
bytes of memory
Hope that's ok; if not, decrease some variables in the equation.

thd=(nil)
Attempting backtrace. You can use the following information to find out
where mysqld died. If you see no messages after this, something went
terribly wrong...
frame pointer is NULL, did you compile with
-fomit-frame-pointer? Aborting backtrace!
The manual page at [http://www.mysql.com/doc/en/Crashing.html](http://www.mysql.com/doc/en/Crashing.html) contains
information that should help you find out what is causing the crash.



---

### Post by pointone on 2008-04-05
Did this just start happening out of nowhere, or were you messing around with system settings/installing new software recently?

How much free space do you have left on your drives?

---

### Post by DaveTheAve on 2008-04-05
This indeed just started happening. I'm assuming via aptcron update rain daily.

as for hard drive space I have 400mb left on my root partition.

---

### Post by pointone on 2008-04-05
This may be your problem. When you start to run out of disk space, all sorts of weird and freaky things start happening. Try freeing up at least a GB and see if this helps at all.

---

### Post by DaveTheAve on 2008-04-05
Sure thing, except:

For this issue:

[http://ubuntuforums.org/showthread.php?t=738616](http://ubuntuforums.org/showthread.php?t=738616)

---

### Post by DaveTheAve on 2008-04-11
Any thoughts?

---

### Post by DaveTheAve on 2008-04-13
Here is the backtrace from the KDE crash Handler (just found out about it :P ):
```

(no debugging symbols found)
Using host libthread_db library "/lib/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 47586913688800 (LWP 16866)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[KCrash handler]
#5  0x00000000004ea63f in ?? ()
#6  0x00000000004e8b6b in (anonymous namespace)::initactors ()
#7  0x00000000004d94a0 in ?? ()
#8  0x000000000043b66e in ?? ()
#9  0x0000000000435673 in ?? ()
#10 0x0000000000435e57 in ?? ()
#11 0x000000362a83bd76 in QObject::activate_signal ()
   from /usr/lib/libqt-mt.so.3
#12 0x000000362aba9e51 in QSignal::signal () from /usr/lib/libqt-mt.so.3
#13 0x000000362a85aeeb in QSignal::activate () from /usr/lib/libqt-mt.so.3
#14 0x000000362a861f1e in QSingleShotTimer::event ()
   from /usr/lib/libqt-mt.so.3
#15 0x000000362a7d72a2 in QApplication::internalNotify ()
   from /usr/lib/libqt-mt.so.3
#16 0x000000362a7d9031 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#17 0x00000034151db308 in KApplication::notify ()
   from /usr/lib/libkdecore.so.4
#18 0x000000362a769d12 in QApplication::sendEvent ()
   from /usr/lib/libqt-mt.so.3
#19 0x000000362a7ca55c in QEventLoop::activateTimers ()
   from /usr/lib/libqt-mt.so.3
#20 0x000000362a77e443 in QEventLoop::processEvents ()
   from /usr/lib/libqt-mt.so.3
#21 0x000000362a7f07e7 in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#22 0x000000362a7f05ef in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#23 0x000000362a7d8d68 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#24 0x0000000000431a46 in ?? ()
#25 0x0000003617a1db44 in __libc_start_main () from /lib/libc.so.6
#26 0x0000000000431739 in ?? ()
#27 0x00007ffff9973368 in ?? ()
#28 0x0000000000000000 in ?? ()

```

---

