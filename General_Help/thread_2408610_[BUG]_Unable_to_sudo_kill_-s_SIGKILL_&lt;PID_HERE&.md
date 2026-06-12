---
title: "[BUG] Unable to sudo kill -s SIGKILL &lt;PID HERE&gt; in 18.04"
date: 2018-12-20
forum: General Help
---

### Post by eanbowman on 2018-12-20
Some rogue apache2 processes:
```
23786 ?        00:00:00 apache2
23836 ?        00:00:00 apache2
23839 ?        00:00:00 apache2
23840 ?        00:00:00 apache2
23875 ?        00:00:00 apache2
25555 ?        00:00:00 apache2
```

I'd like to kill them. Okay... Let's just do it as root! I know how to do this!
```

# kill -s SIGKILL 23786
bash: kill: (23786) - Permission denied
```

Okay, instead of running it as root (#) I'll just sudo:
```

$ sudo kill -s SIGKILL 23786
bash: kill: (23786) - Permission denied
```

```
cat /proc/version
Linux version 4.15.0-42-generic (buildd@lgw01-amd64-023) (gcc version 7.3.0 (Ubuntu 7.3.0-16ubuntu3)) #45-Ubuntu SMP Thu Nov 15 19:32:57 UTC 2018
```

```
sudo dmesg | tail
[ 7227.471689] audit: type=1400 audit(1545323976.363:355): apparmor="DENIED" operation="signal" profile="docker-default" pid=4648 comm="runc" requested_mask="receive" denied_mask="receive" signal=term peer="unconfined"
[ 7227.476017] audit: type=1400 audit(1545323976.367:356): apparmor="DENIED" operation="signal" profile="docker-default" pid=4649 comm="runc" requested_mask="receive" denied_mask="receive" signal=term peer="unconfined"
[ 7227.476020] audit: type=1400 audit(1545323976.367:357): apparmor="DENIED" operation="signal" profile="docker-default" pid=4646 comm="runc" requested_mask="receive" denied_mask="receive" signal=term peer="unconfined"
[ 7227.492379] audit: type=1400 audit(1545323976.383:358): apparmor="DENIED" operation="signal" profile="docker-default" pid=4645 comm="runc" requested_mask="receive" denied_mask="receive" signal=term peer="unconfined"
[ 7229.490185] audit: type=1400 audit(1545323978.379:359): apparmor="DENIED" operation="signal" profile="docker-default" pid=4672 comm="runc" requested_mask="receive" denied_mask="receive" signal=kill peer="unconfined"
[ 7229.498535] audit: type=1400 audit(1545323978.391:360): apparmor="DENIED" operation="signal" profile="docker-default" pid=4677 comm="runc" requested_mask="receive" denied_mask="receive" signal=kill peer="unconfined"
[ 7229.498539] audit: type=1400 audit(1545323978.391:361): apparmor="DENIED" operation="signal" profile="docker-default" pid=4699 comm="runc" requested_mask="receive" denied_mask="receive" signal=kill peer="unconfined"
[ 7229.506821] audit: type=1400 audit(1545323978.399:362): apparmor="DENIED" operation="signal" profile="docker-default" pid=4716 comm="runc" requested_mask="receive" denied_mask="receive" signal=kill peer="unconfined"
[ 7229.507924] audit: type=1400 audit(1545323978.399:363): apparmor="DENIED" operation="signal" profile="docker-default" pid=4671 comm="runc" requested_mask="receive" denied_mask="receive" signal=kill peer="unconfined"
[ 7386.576873] audit: type=1400 audit(1545324135.467:364): apparmor="DENIED" operation="signal" profile="docker-default" pid=4356 comm="bash" requested_mask="receive" denied_mask="receive" signal=kill peer="unconfined"
```



... I'm uploading files. I'd prefer not to have to reboot right now. But I can't kill processes as ROOT?!?!?!?!?

What the hell is happening to Ubuntu these days?!

I'm pretty pissed. I have several 4GB files uploading, and I want to get work done. I want to start up some docker images but I can't do that when something's using the ports required. This is a REAL PROBLEM here...

---

### Post by eanbowman on 2018-12-20
I wanted to delete this reply but this forum doesn't support that.

---

### Post by Holger_Gehrke on 2018-12-20
I don't know why you get "permission denied", but since Apache2 is usually run as a service through systemd it would only get restarted as soon as you kill it. The right way to stop Apache would be 'systemctl stop apache2'.

Holger

---

