---
title: "Dapper server corrupting files upon saving"
date: 2007-01-25
forum: General Help
---

### Post by Zedric on 2007-01-25
I have a seriously annoying problem. I have a Dapper server and a Windows XP client on my local home network. I have Apache and Samba running on the server as I am developing web apps.

The issue is this. Sometimes when I save a file (and all following saves after the error occurs until the machine is rebooted) the file is corrupted. If I save a php file for instance, blocks  of random binary data is inserted into the file at random points, replacing the original html/php code.

When the problem occured right now, I logged in via SSH to save the file and that worked great. If I save via Samba, it's corrupted. Even after reboot, Samba corrupts. I will have it turned off for a while, see if that helps. System and Samba logs give no clue.

The server is running pretty cool, but I replaced a faulty fan on the graphics card the other day. The error first occured two weeks ago. Could it be related?

It sounds kind of hardware related so I've tried running memtest and e2fsck -f, but both came up clean. Any ideas? I don't really know where to start digging.

Sorry about the long post, but rather more details than none, ey? ;)

---

### Post by Zedric on 2007-01-25
Update: This is odd, it seems in a particular I'm testing with, it's always on line 103 the error occurs. 216 characters are replaced by random data. First replaced character is '=', last replaced is also a '=' (but there are five '='s in between them).

If I change the contents ("$query .=" to "$query  .=" (two spaces)) the error stays on the same byte position (i.e., not on the '=' anymore). File system issue? Corrupt block, inode?
The position in the file is number 4097 (i.e. one after 4096, sounds like a block?).

Again, saving over SSH works perfectly. #-o

---

