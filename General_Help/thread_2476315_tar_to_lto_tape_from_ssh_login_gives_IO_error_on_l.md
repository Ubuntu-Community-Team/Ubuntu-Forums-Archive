---
title: "tar to lto tape from ssh login gives IO error on large files but works on console"
date: 2022-06-22
forum: General Help
---

### Post by 21Jerry on 2022-06-22
Hi,

For years, I've been using ssh to access my 20.4 ubuntu server.  I've ssh'ed to it and have run tar jobs to tape a hundred times.  I have an lto-5 loader on the server.  The server has 32Gb of real memory.  I had been using HP DL380s but switched to a Dell r610 and have run tar jobs on the r610 to tape.  I have separate SAS HBAs for disk and tape.

Today I ssh'ed to the server and tried to run a command I've run dozens of times:

      **tar -b1024 -cvf /dev/nst0 /owc1**

This backs up a ZFS raidz2 drive.  In every case where it tried to tar a very large file, say over 100Gb, I got an error:

     **tar: lto Wrote only 118784 of 524288 bytes**

And then a message about the error not being recoverable and ending.  I ran mt -f /dev/nst0 status and it didn't report and errors and there were no errors on the console log.

I tried a number of small files and they tar without an issue, for instance /etc, /var, and others.  I've tried other tapes, including those known to be good and brand new lto5.  Same issue at the same spot on the first large file.

I then went down to the server to check the loader, listened to it and it sounded fine.  I ran the command from the console and it worked!  Still running actually as the directory is about 1T and the drive averages about 220Gb per hour, faster depending on small file sizes or not and the drive I am backing-up.

Any ideas?

Thanks

jerry

---

### Post by TheFu on 2022-06-23
Check the system logs.  Might be something useful in there.
My initial thoughts were that a real console was necessary (for some reason), but because it works for smaller tasks, that can't be it.  The log files are all I have to suggest.  

Maybe the SAS connector isn't really solid?  That's unlikely, but we never know. Vibrations can do bad things to connectors.  Normally, only USB connectors have problems with vibrations, though I did have a sata connector inside a cheap, external array, lose connectivity about once a month until I replaced the straight sata connector with a 90° connector.  Since that upgrade, the connection hasn't dropped once and it is over 13 yrs now.

---

