---
title: "[SOLVED] backuppc"
date: 2007-07-20
forum: General Help
---

### Post by upthelum on 2007-07-20
I cant open rar files and have been through the boards looking at threads for a solution. 
This was the last thing i tried:

sudo aptitude update
sudo aptitude install unrar
unrar x filename.rar

When i did "sudo aptitude install unrar" i got this message:

"root@ubuntu-desktop:/# sudo aptitude install unrar
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Reading task descriptions... Done
Building tag database... Done
No candidate version found for unrar
The following packages have been kept back:
  firefox iptables libnspr4 libnss3
  linux-image-2.6.15-28-server
0 packages upgraded, 0 newly installed, 0 to remove and 5 not upgr aded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up backuppc (2.1.2-2ubuntu5) ...
 * Starting backuppc... 2007-07-20 13:22:01 $Conf{SendmailPath} = '/usr/sbin/sendmail' is not a valid executable program
invoke-rc.d: initscript backuppc, action "start" failed.
dpkg: error processing backuppc (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 backuppc
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up backuppc (2.1.2-2ubuntu5) ...
 * Starting backuppc... 2007-07-20 13:22:04 $Conf{SendmailPath} = '/usr/sbin/sendmail' is not a valid executable program
invoke-rc.d: initscript backuppc, action "start" failed.
dpkg: error processing backuppc (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 backuppc"

I get this a lot. Backuppc seems to be the problem though i am unsure how to resolve it. 
Can anyone help, thanks in advance...

---

### Post by Happy_Man on 2007-07-20
For unrar, are all your repos enabled?

---

### Post by upthelum on 2007-07-20
As far as i know, i added another this morning which i found on the forums.

---

### Post by upthelum on 2007-07-20
Ok so now i tried this:
sudo apt-get install rar
Reading package lists... Done
Building dependency tree... Done
Package rar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package rar has no installation candidate

What does this mean?

---

### Post by Happy_Man on 2007-07-23
> **upthelum said:**
> Ok so now i tried this:
sudo apt-get install rar
Reading package lists... Done
Building dependency tree... Done
Package rar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package rar has no installation candidate

What does this mean?
The package "unrar" used to be "rar", but then they changed it.

---

### Post by upthelum on 2007-07-23
Cheers, still no joy though...

---

