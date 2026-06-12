---
title: "Bluefish"
date: 2016-08-14
forum: General Help
---

### Post by pedro_rodriguez2 on 2016-08-14
I was happily using Bluefish to make a little webpage when it stopped working, presumably after an update. I use 14.04. Bluefish will not start.

I get this error in a terminal.

> pedro@pedro-schule:~$ bluefish
error reading list 1 Error opening file: No such file or directory

** (bluefish:5313): WARNING **: no configfile rcfile-2.0, try to convert config files from older versions

config file migration error 1:Error opening file: No such file or directoryerror reading list 1 Error opening file: No such file or directory

(bluefish:5313): GLib-ERROR **: /build/buildd/glib2.0-2.40.2/./glib/gmem.c:103: failed to allocate 18446744073680723746 bytes
Trace/breakpoint trap (core dumped)
pedro@pedro-schule:~$ 

How to fix this? I like Bluefish because it is easy for beginners.

Edit: I have uninstalled and reinstalled Bluefish. I also use Ubu 16.04. Bluefish works there.

---

### Post by agillator on 2016-08-15
First, make sure your two installations (14.04 and 16.04 I think you said) are not sharing anything bluefish uses. Second, when you uninstalled, how did you do it? Manually, apt-get remove or apt-get purge? When you uninstalled did you check before reinstalling to make sure all the configuration files were actually removed (system and user both)?
It sounds almost like the two installation are sharing something that the 16.04 version changed so the 14.04 version can't recognize or use it.

If none of these helped there is always the bigger hammer approach, but be aware it can be very dangerous. Use carefully and judiciously if you use it at all. After you uninstall, do a find for any bluefish related files (*bluefish* as a start). You probably will want to redirect to a file rather than just display. There may (or may not) be a bunch. Look through the list very carefully and make sure the two versions are not sharing it. What I suspect is happening is during uninstallation a corrupted file is not being removed and since it is already there is not being replaced during reinstallation. So anything that looks like a configuration file that is still there, or any other file that looks like it may fill the bill you need to get rid of. DO NOT remove it. Rename to something totally separate that cannot be confused with the original file name. Keep track of what you do so you can reverse it if necessary. Pen and paper are wonderful inventions for this step. Be aware that if you ACCIDENTALLY ERASE OR ALTER A FILE NECESSARY FOR YOUR SYSTEM TO OPERATE, NOT JUST BLUEFISH, YOU CAN SCREW UP YOUR WHOLE SYSTEM!!!! Be cautious and very, very conservative. When you think you have cleaned everything, reboot the computer to be sure you haven't screwed anything up. Assuming it reboots ok, reinstall bluefish and see what happens. This is the blunt instrument, bigger hammer approach. Sometimes it works, sometimes it doesn't. I cannot emphasize enough it is a very dangerous approach, but it has solved similar problems for me many times. It has also, through my stupidity, . . . but I'd rather not talk about that. Just be forewarned. There are two types of people: those who have and those who will.

---

### Post by pedro_rodriguez2 on 2016-08-15
Thanks.

To uninstall I used the Software Centre and clicked remove. I'll go back and do it with apt-get purge. Will that do anything else?

How could anything on 14.04 be shared with 16.04? They are on different partitions. I start 14.04 or 16.04. I still find 16.04 is a bit unstable. When it is better, I will maybe get rid of 14.04 and just use 16.04

---

### Post by agillator on 2016-08-16
A purge SHOULD get the necessary files, but may not. Often it will not delete config files in use or tha have contents for some reason. I think it has to do with the way the installation was written, I don't really know. But if the purge doesn't clear things up, then you may need to consider the hammer. 

It is easy to get the two versions to share data files - whether they will run properly is another question. All you have to do is mount the same partition at the same point in both versions. Personally I do not do that. I tried it once and ran into too many problems. But some people do. The usual candidate is the home directory. They make that a separate partition and then mount it at their /home/<user> directory for both installations. It seems to me they would run into problems with configuration files but I guess they work around it somehow. The normal approach, though, for something like this is not for the same files for two versions, but rather to have nothing in the home directory overwritten by a new installation. They use a separate partition for the home directory, mount it as such during installation so the new version changes the files it has to but doesn't bother anything else. This way they lose none of the important stuff (or any of the garbage) that has collected over time. 

Good luck, I hope the apt-get or dpkg purge solves your problem.

---

### Post by pedro_rodriguez2 on 2016-08-17
No luck, after sudo apt-get purge bluefish, same old:

> pedro@pedro-schule:~$ bluefish
error reading list 1 Error opening file: No such file or directory

** (bluefish:6033): WARNING **: no configfile rcfile-2.0, try to convert config files from older versions

config file migration error 1:Error opening file: No such file or directoryerror reading list 1 Error opening file: No such file or directory

(bluefish:6033): GLib-ERROR **: /build/buildd/glib2.0-2.40.2/./glib/gmem.c:103: failed to allocate 18446744073694722050 bytes
Trace/breakpoint trap (core dumped)
pedro@pedro-schule:~$ 

I'll try and get in touch with whomsoever makes bluefish and tell them.

---

### Post by QIII on 2016-08-17
Hello!

purge removes system config files, but does not remove anything in your /home.

You should have a /.bluefish directory there.  Purge Bluefish and then remove /.bluefish

Reinstall Bluefish and let us know  how it goes.

Cheers!

---

### Post by pedro_rodriguez2 on 2016-08-17
Jo, that did it! Thanks!

I deleted the .bluefish in my home directory. I got this on startup, no idea what it means, but bluefish works again!

> pedro@pedro-schule:~$ bluefish
error reading list 1 Error opening file: No such file or directory

** (bluefish:7389): WARNING **: no configfile rcfile-2.0, try to convert config files from older versions

config file migration error 1:Error opening file: No such file or directoryerror reading list 1 Error opening file: No such file or directory
error reading list 1 Error opening file: No such file or directory
cleanup_scanner, memory scancache 0(0Kb+0Kb) found 0(0Kb) fcontext 0(0Kb) = 0Kb
cleanup_scanner, memory scancache 0(0Kb+0Kb) found 0(0Kb) fcontext 0(0Kb) = 0Kb
Possible error in language file, id - / pattern </script> has ends_context=3, but has only 3 parent contexts
Possible error in language file, id - / pattern </script> has ends_context=3, but has only 3 parent contexts
Possible error in language file: id </script> already exists
Possible error in language file, id - / pattern } has ends_context=2, but has only 2 parent contexts
Possible error in language file, id - / pattern </style> has ends_context=3, but has only 3 parent contexts
Possible error in language file: id </style> already exists
Language statistics for HTML5 from /usr/share/bluefish/bflang//html5.bflang2
reference size          114.81 Kbytes
largest table  4384 (  1096.00 Kbytes)
total tables  57233 ( 14308.25 Kbytes)
contexts        241 (    11.30 Kbytes)
matches       10133 (   474.98 Kbytes)
blocks            9 (     0.28 Kbytes)
cleanup_scanner, memory scancache 0(0Kb+0Kb) found 0(0Kb) fcontext 0(0Kb) = 0Kb
scanning run 1 (11 ms): 0, 0, 0, 11; from 0-1801, loops=2123,chars=1801,blocks 58/54 (0) contexts 84/84 (0) scancache 222
memory scancache 222(5Kb+8Kb) found 58(1Kb) fcontext 84(1Kb) = 17Kb
average 163727 chars/s 1801 chars/run
scancache integrity check done in 0.128000 ms.

Done, fixed! (Until the next time!)

---

