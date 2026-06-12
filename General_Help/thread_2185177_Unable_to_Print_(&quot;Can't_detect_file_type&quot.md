---
title: "Unable to Print (&quot;Can't detect file type&quot;)"
date: 2013-11-01
forum: General Help
---

### Post by bak&#305;r on 2013-11-01
Dear all,

My day became a nightmare, after I realised that I would not be able to print a page that I had to send. I am using a laserjet HP, which functioned flawlessly till now. I tried installing hplip again, but to no avail.
Two consecutive messages appear: one indicating the start of the process, and another telling me that the job is complicated. In the queue, the jobs are listed with "stopped" or "unknown file type".

Any help will be appreciated.

OS: 2 different computers with Ubuntu 13.10 and Mint 15, 64 bit

---

### Post by tgalati4 on 2013-11-01
Reboot the printer and reseat the connections from the printer to the computer or LAN.

If that doesn't work, then look for more descriptive errors in /var/log/cups.

---

### Post by bak&#305;r on 2013-11-01
I have tried this once more, but it did not work. It used to say "hpcups" is missing, but after I have fixed this by installing the package, it stated complaining "unknown file type"

```

D [01/Nov/2013:18:14:36 +0200] [Job 8] printer-state-message="Can't detect file type"

```

---

### Post by Toz on 2013-11-01
*Thread title changed to be more descriptive of the problem.*

---

### Post by tgalati4 on 2013-11-01
Sometimes the printer queue gets messed up.  Try deleting the printer from CUPS ([http://localhost:631](http://localhost:631)) and reinstall.  Do you have the latest *hpijs* installed?

tgalati4@Mint14-Extensa ~ $ apt-cache policy hpijs
hpijs:
  Installed: 3.12.6-3ubuntu4.2
  Candidate: 3.12.6-3ubuntu4.2
  Version table:
 *** 3.12.6-3ubuntu4.2 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal-updates/main amd64 Packages
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) quantal-security/main amd64 Packages
        100 /var/lib/dpkg/status
     3.12.6-3ubuntu4 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main amd64 Packages

---

### Post by bak&#305;r on 2013-11-01
I updated, I guess this is quite new:
```

Installed: 3.13.3-1ubuntu0.1
Candidate: 3.13.3-1ubuntu0.1

```

No change after trying both, unfortunately.

---

### Post by tgalati4 on 2013-11-01
What is the exact model and age of the Laserjet printer?  I have a feeling that your printer's processor has taken a dump.  Can you print a status sheet from the printer's front panel?  Also, try reseating the RAM in the printer.  How is this printer connected to the network?

The fact that it does not work with two different computers tells me that it is not a CUPS problem, but a data transmission or interpretation problem at the printer.

Do you have any other printers on the same network?  Do they work with CUPS?

---

### Post by bak&#305;r on 2013-11-02
There is no network, printer is directly connected via USB. I unfortunately do not have any other printers to test, whether it is computer or printer related.

Where is RAM?

The recent error report is this : Exception: var/spool/cups/d00015-001 unexpected brace token.

---

### Post by bak&#305;r on 2013-11-09
Thanks for everybody that tried to help me, although without success. Strangely enough, the problem has been spontaneously cleared after an update.

---

### Post by AgentZ86 on 2014-01-02
I didn't see what printer model it is ?

This could make a difference if your using the postscript driver (recommended) and there it is not a postscript printer or if it's an older HP 4 / 5 with NO postscript memory installed.

But I had the same problem and switched drivers from the (postscript) recommended to the CUPS printer and it worked perfectly after that.

Anyhow FYI could be driver issue still that fixed upon update.
Anyhow glad it's fixed I hate printer issues

---

