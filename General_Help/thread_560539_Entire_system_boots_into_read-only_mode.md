---
title: "Entire system boots into read-only mode"
date: 2007-09-26
forum: General Help
---

### Post by toyotafosgate on 2007-09-26
I am new to the Unix/Linux world so forgive me but I'm learning quickly.. 

Now I have installed Ubuntu Server Edition 6.10 and was attempting to copy over the
config files from a backup of an existing mail server. I wasn't quite sure of the right way to do this so I installed Ubuntu, then POSTFIX, SMTP-AUTH and TTLS. 

After installing I attempted to copy over the existing /etc and /home backupfiles into the new server and overwrite the existing files. Once that was finished I rebooted. The prompt came up the same as the existing mail server which is good, and the same user name an password. 

But after I logged in it came up with error messages:
     add_to_rules: invalid KERNEL operation
     add_to_rules: invalid SYSFS operation
     add_to_rules: invalid rule '/etc/udev/rules.d/65-persistent-disk.rules:11'
             syslogd /var/auth.log: Read-only file system
             syslogd: /var/log/syslog: Read-only file system

and then there is more of the syslogd lines...

     Also when I type my user name in it says:
Configuration error - unknown item 'FAIL_DELAY' (notify administrator)

Now from the research I have done I have found that Ubuntu goes into read-only
mode when it is protecting itself from further harm. Any error can send it into read-only,
usually a harddrive problem I guess. I am pretty sure that it is no coincidence that I added the
files and then rebooted and that when the problems began occuring. I also found that simply deleting the FAIL_DELAY from an entry of one of the config files will solve that but I can't fix any errors in read-only mode so what am I supposed to do.... 

any help would be greatly appreciated,

       Brandon

---

