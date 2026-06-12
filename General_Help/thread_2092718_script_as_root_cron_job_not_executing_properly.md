---
title: "script as root cron job not executing properly"
date: 2012-12-08
forum: General Help
---

### Post by wayover13 on 2012-12-08
I recently found and tweaked a script that is supposed to help my 12.04, heavily modified system, maintain its wifi connection to my home router. The connection's been kinda dodgy, and I decided polling for a new dhcp lease regularly might help that.

The script I found and modified looks like this:```
#!/bin/bash

if ! `ping -c 1 -w 1 -q 192.168.1.1 </dev/null &>/dev/null` ; then
        echo "resetting eth0 $(date)" >>/home/user/renew-eth0.txt
        ifdown eth0
        ifup eth0
else
        echo "eth0 operational $(date)" >>/home/user/renew-eth0.txt
fi
exit 0

```
What the script does, of course, is run a ping test and, based on the result of the ping test, either brings down, then up again, eth0, and sends a message to a log file to that effect, or simply writes to a file with a time/date stamp that eth0 is already up. Pretty simple.

Now, when I bring eth0 down manually, then run that script manually (sudo) from the command line, it works fine: eth0 gets an IP. When I specify the path to that file as a cron job for the root user, however, it doesn't run as expected. It does do the ping test and write the time/date stamped message to the specified file if eth0 is operational. If the ping test is unsuccessful, it also writes the time/date stamped message to the log file: but it does not succeed in bringing up eth0: the computer gets no IP when the script runs this way, despite the fact that it **does** get an IP when I run the script manually from the command line.

So, what could be going on here? Why would the script run successfully when entered at the command line, but only run partially when specified as a cron job? I'm confused by this. Anyone else not?

Thanks,
James

---

### Post by SeijiSensei on 2012-12-08
Try using /sbin/ifup and /sbin/ifdown.  It's always good practice to use complete paths in cron.

---

### Post by wayover13 on 2012-12-08
> **SeijiSensei said:**
> Try using /sbin/ifup and /sbin/ifdown.  It's always good practice to use complete paths in cron.
Thanks for the tip, SeijiSensei. I'd actually considered doing that but was uncertain whether it would help. I've gone ahead and edited the script and will inform here whether it starts to work as expected.

Another modification to the script I've considered is changing ifdown eth0/ifup eth0 to dhclient -r/dhclient eth0. I'm not sure that would really make any significant change, though, since ifdown/ifup already call dhclient, if I understand correctly. Any comments on that possible further modification, anyone?

James

---

### Post by rnerwein on 2012-12-09
> **wayover13 said:**
> I recently found and tweaked a script that is supposed to help my 12.04, heavily modified system, maintain its wifi connection to my home router. The connection's been kinda dodgy, and I decided polling for a new dhcp lease regularly might help that.

The script I found and modified looks like this:```
#!/bin/bash

if ! `ping -c 1 -w 1 -q 192.168.1.1 </dev/null &>/dev/null` ; then
        echo "resetting eth0 $(date)" >>/home/user/renew-eth0.txt
        ifdown eth0
        ifup eth0
else
        echo "eth0 operational $(date)" >>/home/user/renew-eth0.txt
fi
exit 0

```What the script does, of course, is run a ping test and, based on the result of the ping test, either brings down, then up again, eth0, and sends a message to a log file to that effect, or simply writes to a file with a time/date stamp that eth0 is already up. Pretty simple.

Now, when I bring eth0 down manually, then run that script manually (sudo) from the command line, it works fine: eth0 gets an IP. When I specify the path to that file as a cron job for the root user, however, it doesn't run as expected. It does do the ping test and write the time/date stamped message to the specified file if eth0 is operational. If the ping test is unsuccessful, it also writes the time/date stamped message to the log file: but it does not succeed in bringing up eth0: the computer gets no IP when the script runs this way, despite the fact that it **does** get an IP when I run the script manually from the command line.

So, what could be going on here? Why would the script run successfully when entered at the command line, but only run partially when specified as a cron job? I'm confused by this. Anyone else not?

Thanks,
James
do you call your sript from /etc/crontab ? 
after the ifdown command just patch:
 echo "ifdown returns $?" >> /tmp/ifdown_up.txt
and after ifup
echo "ifup returns $?" >> /tmp/ifdown_up.txt

if the returncode ($?) isn't zero you can find the meaning of it in:
/usr/include/asm-generic/errno-base.h
or
/usr/include/asm-generic/errno.h

---

### Post by wayover13 on 2012-12-09
> **rnerwein said:**
> do you call your sript from /etc/crontab ?
No, it doesn't appear so--at least I don't find the cronjob there. I added the job by running sudo crontab -e, btw. Thanks for the further logging tips you've offered, rnerwein. It does seem that adding the full path to the ifup/ifdown binaries, as suggested by SeijiSensei, has got the script working now.

James

---

