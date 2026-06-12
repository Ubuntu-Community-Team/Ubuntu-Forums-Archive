---
title: "havp pid file disappearing"
date: 2007-12-17
forum: General Help
---

### Post by A-star on 2007-12-17
I'm using Ubuntu 7.10 as my server and when I install havp from the repositories, it works fine until I restart.

Then the pid file in /var/run/havp/havp.pid suddenly disappears.

Here is the log file.
First it starts up fine.
Then after reboot I get the error.

Any ideas?
```

17/12/2007 12:34:42 === Starting HAVP Version: 0.86
17/12/2007 12:34:42 Change to user havp
17/12/2007 12:34:42 Change to group havp
17/12/2007 12:34:42 --- Initializing ClamAV Library Scanner
17/12/2007 12:34:42 ClamAV: Using database directory: /var/lib/clamav/
17/12/2007 12:34:44 ClamAV: Loaded 178290 signatures (engine 0.91.2)
17/12/2007 12:34:44 ClamAV Library Scanner passed EICAR virus test (Eicar-Test-Signature)
17/12/2007 12:34:44 --- All scanners initialized
17/12/2007 12:34:44 Process ID: 7613
17/12/2007 12:37:03 === Starting HAVP Version: 0.86
17/12/2007 12:37:03 Change to user havp
17/12/2007 12:37:03 Change to group havp
17/12/2007 12:37:03 --- Initializing ClamAV Library Scanner
17/12/2007 12:37:03 ClamAV: Using database directory: /var/lib/clamav/
17/12/2007 12:37:05 ClamAV: Loaded 178290 signatures (engine 0.91.2)
17/12/2007 12:37:06 ClamAV Library Scanner passed EICAR virus test (Eicar-Test-Signature)
17/12/2007 12:37:06 --- All scanners initialized
17/12/2007 12:37:06 Can not write to PIDFILE!
17/12/2007 12:37:06 Process ID: 4432 

```

---

