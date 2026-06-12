---
title: "Terminal will not accept input and Software Center gives error"
date: 2013-02-04
forum: General Help
---

### Post by poeticoddity on 2013-02-04
I'm using Lubuntu 12.10.  I've never come across a problem like this in the last four years of using Ubuntu and variants.

When I try to open Tilda (either from the GUI or using ALT+F2), it never opens.  When I open LXTerminal, it just sits there and does not accept keyboard input.

When I've tried to install another terminal client, the Lunbutu Software Center gives me the following error:

```
installArchives() failed: Setting up install-info (4.13a.dfsg.1-8ubuntu2) ...
/var/lib/dpkg/info/install-info.postinst: 32: /var/lib/dpkg/info/install-info.postinst: update-info-dir: not found
dpkg: error processing install-info (--configure):
 subprocess installed post-installation script returned error exit status 127
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 install-info
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)
Setting up install-info (4.13a.dfsg.1-8ubuntu2) ...
/var/lib/dpkg/info/install-info.postinst: 32: /var/lib/dpkg/info/install-info.postinst: update-info-dir: not found
dpkg: error processing install-info (--configure):
 subprocess installed post-installation script returned error exit status 127

```

I've never had the terminal fail to respond before.  I've rebooted several times, I made a secondary account with root priviledges, and nothing's changed.  If anyone has any suggestions, I would be most appreciative. This actually has me a bit worried that I'll have to reformat my office desktop. :(

---

### Post by poeticoddity on 2013-02-04
The virtual terminal will accept a login, but briefly flashes something on the screen (I couldn't catch it with scroll lock the half dozen times I tried) before prompting me for login again.

---

### Post by TheFu on 2013-02-04
After the machine is running, power it off - do not shutdown.

Boot from other media - flash drive or CDROM, whatever.

Run** fsck** against the HDD partitions where the OS is.
Mount the HDD with your OS and /var/log.
Look/**grep** through the log files to see any errors or warnings. Are there any clear issues?  Anything about failing hardware?

If the HDD is filling up, weird things start to happen. There is 2 types of storage limits, check both with 
$ **df -k**
$ **df -i**
Anything over 97% utilization is bad - really Linux/Unix like less than 90% utilization before problems start on most average sized (20G or less) partitions.  With really large partitions, the utilization can be higher before issues begin.  Last week, one of my boxed ran out of inodes - it was bad - really bad.

**Being out of storage or inodes is bad.**

If your local APT repo has become corrupted, I'd recommend restoring the entire OS from a backup prior to when the issues first started.

---

### Post by thenox on 2013-02-06
This is a strange problem. I'd be interested to know if the above fix worked.

---

