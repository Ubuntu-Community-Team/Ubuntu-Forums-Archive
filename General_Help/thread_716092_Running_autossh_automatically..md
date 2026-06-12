---
title: "Running autossh automatically."
date: 2008-03-05
forum: General Help
---

### Post by TerranFury on 2008-03-05
Hi,

I have installed autossh and would like it to run automatically at boot.

Autossh itself works fine.  I run,

```

autossh -pXX -N -M 20000 -f -R XXXX:localhost:XX XXXX@XXXX.dyndns.org

```

This works perfectly.  My problem is running it at boot.  Here's what I attempted:

I created a script, /etc/init.d/autossh.sh which simply runs the above command:
```

#!/bin/sh
autossh -pXX -N -M 20000 -f -R XXXX:localhost:XX XXXX@XXXX.dyndns.org

```
Here are its attributes:
```

-rwxr-xr-x 1 root root 595 2008-03-05 15:00 autossh.sh

```

Then, I created a symlink in /etc/rc2.d:
```

lrwxrwxrwx 1 root root 20 2008-03-05 13:49 S99autossh -> ../init.d/autossh.sh

```

Now, I would expect autossh to run automatically at boot.  However, when I check (after a reboot),
```

ps -e | grep -i autossh

```
...I get nothing.

In an effort to debug, I made some changes to /etc/init.d/autossh.sh:
```

#!/bin/sh

su - username -c 'echo "Running autossh.sh on $(date). [FLAG5]" >> /home/username/autossh.sh.log'
su - username -c 'echo "--ifconfig----" >> /home/username/autossh.sh.log'
su - username -c '/sbin/ifconfig >> /home/username/autossh.sh.log'
su - username -c 'echo "--------------" >> /home/username/autossh.sh.log'

su - username -c 'autossh -pXX -N -M 20000 -f -R XXXX:localhost:XX XXXX@XXXXXX.dyndns.org 1&2>> /home/username/autossh.sh.log' &
su - username -c 'echo "ps output: $(ps -e | grep autossh)" >> /home/username/autossh.sh.log'
su - username -c 'echo "=========================" >> /home/username/autossh.sh.log'

```
The interesting thing is this:  After I log in, I find that ~/autossh.sh.log has been created!  The network interface seems to have been brought up by the time it is run (that is, ifconfig returned sensible things)!  Clearly, the script gets run!  Here is the output:

~/autossh.sh.log
```

Running autossh.sh on Wed Mar  5 14:51:06 EST 2008. [FLAG5]
--ifconfig----
eth0      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX
          inet addr:192.168.XX.XX  Bcast:192.168.XX.XXX  Mask:255.255.255.0
          inet6 addr: XXXX::XXX:XXXX:XXXX:XXXX/XX Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3371 errors:0 dropped:0 overruns:0 frame:0
          TX packets:615 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:574222 (560.7 KB)  TX bytes:90746 (88.6 KB)
          Base address:0xdf40 Memory:feae0000-feb00000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

--------------
ps output:  5628 pts/1    00:00:00 autossh.sh
 5643 ?        00:00:00 autossh
 5646 ?        00:00:00 autossh
=========================

```
(Like I said before, this all looks sane.)

So, sometime after this runs, autossh (and my script?) must be somehow getting killed.  Why would this happen?  My only thought is that my runlevel must be wrong, but I check it...
```

username@XXXXX:~$ runlevel
N 2

```
...and it is indeed 2, so since I put the symlink to autossh.sh in /etc/rc**2**.d, I'd expect it to still be running!  Yet it isn't.

I get the feeling that my understanding of the SysV boot process must be wrong or something.  What's going on?  Any ideas for how I might be able to get autossh to run at boot?

Thanks.

---

