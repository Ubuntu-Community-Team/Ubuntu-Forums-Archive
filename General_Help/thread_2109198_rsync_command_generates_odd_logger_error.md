---
title: "rsync command generates odd logger error"
date: 2013-01-26
forum: General Help
---

### Post by mcqueed on 2013-01-26
Ubuntu 12.04.1 64 Server

I am syncing between 2 servers.  Under 10.10 all was good.  I had some hardware replacements and time, so I started from scratch and built 2 new 12.04.1 installs.  Now when I run rsync, I get some odd logger errors.

Here is the command:

```
/usr/bin/rsync -aW --stats -e '/usr/bin/ssh -p 222 -i /home/nasadmin/rsyncssh/nas-mcq-3-rsync-key' nasadmin@192.168.1.11:/media/HomeAudio/shirleyhome/ /media/HomeAudio/shirleyhome/
```and here is the output of that command:

```
logger: invalid option -- 'l'

Usage:
 logger [options] [message]

Options:
 -d, --udp             use UDP (TCP is default)
 -i, --id              log the process ID too
 -f, --file <file>     log the contents of this file
 -h, --help            display this help text and exit
 -n, --server <name>   write to this remote syslog server
 -P, --port <number>   use this UDP port
 -p, --priority <prio> mark given message with this priority
 -s, --stderr          output message to standard error as well
 -t, --tag <tag>       mark every line with this tag
 -u, --socket <socket> write to this Unix socket
 -V, --version         output version information and exit


Number of files: 1338
Number of files transferred: 0
Total file size: 343702889 bytes
Total transferred file size: 0 bytes
Literal data: 0 bytes
Matched data: 0 bytes
File list size: 28337
File list generation time: 0.001 seconds
File list transfer time: 0.000 seconds
Total bytes sent: 206
Total bytes received: 29104

sent 206 bytes  received 29104 bytes  58620.00 bytes/sec
total size is 343702889  speedup is 11726.47

```That logger command error is very odd.

When I run a similar command, I get a different logger error:

Command:

```
/usr/bin/rsync -aW --stats -e '/usr/bin/ssh -p 222 -i /home/nasadmin/rsyncssh/nas-mcq-3-rsync-key' /media/HomeAudio/davidhome/ nasadmin@192.168.1.11:/media/HomeAudio/davidhome/
```Output:

```
logger: unable to resolve '-lWogDtpre.iLsf'

Number of files: 26157
Number of files transferred: 0
Total file size: 54155519539 bytes
Total transferred file size: 0 bytes
Literal data: 0 bytes
Matched data: 0 bytes
File list size: 908245
File list generation time: 0.001 seconds
File list transfer time: 0.000 seconds
Total bytes sent: 910188
Total bytes received: 1942

sent 910188 bytes  received 1942 bytes  608086.67 bytes/sec
total size is 54155519539  speedup is 59372.59

```I don't understand where the logger fits in.

---

### Post by mcqueed on 2013-01-27
I found my own error.  I have a validate script running on the destination machine to check to make sure that the command using the ssh key is only a rsync command.

I added logger commands to that validate script.  I fixed it and all is good.

Here is my validating script if interested:

```
#!/bin/sh 

logger " "
logger "$SSH_ORIGINAL_COMMAND"
logger " "

case "$SSH_ORIGINAL_COMMAND" in 
    *\&*) echo "Rejected";; 
    *\(*) echo "Rejected";; 
    *\{*) echo "Rejected";; 
    *\;*) echo "Rejected";; 
    *\<*) echo "Rejected";; 
    *\`*) echo "Rejected";; 
    *\|*) echo "Rejected";; 
    rsync\ --server*) $SSH_ORIGINAL_COMMAND;; 
    *) echo "Rejected";; 
esac

```

I added the quotes to the line logger "$SSH_ORIGINAL_COMMAND" and it fixed my errors.

---

