---
title: "Command-line client for ftp uploads supporting easy restarts"
date: 2008-06-05
forum: General Help
---

### Post by barrkel on 2008-06-05
What is the appropriate command-line (i.e. scriptable) program to use for restartably uploading files over ftp?

The 'ftp' command itself has primitives like 'restart <marker>', but these need to be calculated by hand, and so are not scriptable.

For example, I use 'wget' to download from ftp servers rather than 'ftp' itself, as wget makes restarting easy - '-T' for timeout, '-t' for retries, '-c' to continue downloading from a previous session, etc.

What is the equivalent "rich" front end command line program that supports equivalent functionality in the upload direction for ftp?

---

### Post by bingoUV on 2008-06-05
must you use ftp? rsync is a proven program for this. I think ssh server needs to be running on the other side. 
```

rsync -av source target

```

For details, see man page
```

man rsync

```

Not only will it resume interrupted upload, it will also fix an upload corrupted somewhere in the middle; with minimal network usage.

---

### Post by barrkel on 2008-06-05
Yes, I must use ftp.

For the benefit of others who read this thread in the future, rsync can synchronize files and directories between a client and a remote server that also has rsync, using either pipes (via ssh or another remote shell protocol) or TCP (when using rsync --daemon directly, or another program that understands the rsync protocol).

Rsync isn't bad as a synchronization protocol when a source control system like git or mercurial (hg) can't be used instead, but I need to communicate with an FTP server.

---

### Post by bingoUV on 2008-06-05
have you tried curl's upload? I don't know if it supports resume though.

---

### Post by andrew.46 on 2008-06-06
Hi,

My favourite ftp program ncftp appears to support this by using the -z option, but I have peronally not used this option.

               Andrew

---

