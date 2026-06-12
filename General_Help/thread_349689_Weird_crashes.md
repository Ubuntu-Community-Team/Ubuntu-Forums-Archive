---
title: "Weird crashes"
date: 2007-01-30
forum: General Help
---

### Post by koolguynet on 2007-01-30
Ok, I have no idea where to begin.  I guess I will describe what is happening and then if people can suggest what logs or commands to post, that would be great.  I have a Kubuntu Edgy box (IBM NetVista) that I am running for a home server.  As a windows box it ran great and as a Kubuntu box it runs great, for a little bit.  For the first 24-36 hours after turning it on it runs really fast and smooth.  Webpages are served through apache, SSH works, everything is great!  Then at some point between 24-36 hours it takes a dump.  I can't ssh to it, web pages time out and from the system itself I can still see the screen and sometimes can run commands but it literally takes 15 minutes just to show the terminal window.  Does anyone have any ideas?  Is there a log that may show what is going on?

---

### Post by crispy_420 on 2007-01-30
Just an idea, but is it overheating? Sometimes thermal sensors don't quite work write in ubuntu.

---

### Post by koolguynet on 2007-01-30
I doubt that is it because it would power down if that was the case.  Also everything seems to be cool.  The room it is in stays at around 60 this time of year and the machine is well ventilated.

---

### Post by po0f on 2007-01-30
koolguynet,

You mentioned Web pages timing out and not being able to SSH in; any other services running on this box?

---

### Post by koolguynet on 2007-01-30
Here is what is running:

ps -A
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 migration/0
    3 ?        00:00:00 ksoftirqd/0
    4 ?        00:00:00 watchdog/0
    5 ?        00:00:00 events/0
    6 ?        00:00:00 khelper
    7 ?        00:00:00 kthread
    9 ?        00:00:00 kblockd/0
   10 ?        00:00:00 kacpid
   11 ?        00:00:00 kacpi_notify
   91 ?        00:00:00 kseriod
  124 ?        00:00:00 pdflush
  125 ?        00:00:00 pdflush
  126 ?        00:00:00 kswapd0
  127 ?        00:00:00 aio/0
 1722 ?        00:00:00 khubd
 1821 ?        00:00:00 kjournald
 1898 ?        00:00:00 logd
 2011 ?        00:00:00 udevd
 2755 ?        00:00:00 shpchpd
 2826 ?        00:00:00 kpsmoused
 3210 ?        00:00:00 kjournald
 3440 tty1     00:00:00 getty
 3441 tty2     00:00:00 getty
 3442 tty3     00:00:00 getty
 3443 tty4     00:00:00 getty
 3444 tty5     00:00:00 getty
 3445 tty6     00:00:00 getty
 3655 ?        00:00:00 acpid
 3752 ?        00:00:00 syslogd
 3778 ?        00:00:00 dd
 3780 ?        00:00:00 klogd
 3793 ?        00:00:00 kdm
 3814 tty7     00:00:00 Xorg
 3823 ?        00:00:00 kdm
 3824 ?        00:00:00 cupsd
 3857 ?        00:00:00 hpiod
 3860 ?        00:00:00 python
 3914 ?        00:00:00 apt-index-watch
 3930 ?        00:00:00 dbus-daemon
 3945 ?        00:00:01 hald
 3946 ?        00:00:00 hald-runner
 3954 ?        00:00:00 hald-addon-acpi
 3962 ?        00:00:00 hald-addon-keyb
 3964 ?        00:00:02 kdm_greet
 3966 ?        00:00:00 hald-addon-keyb
 3975 ?        00:00:00 hald-addon-stor
 4313 ?        00:00:00 thinkpad-keys
 4324 ?        00:00:00 hald-addon-keyb
 4353 ?        00:00:00 nmbd
 4355 ?        00:00:00 smbd
 4360 ?        00:00:00 smbd
 4374 ?        00:00:00 sshd
 4420 ?        00:00:00 hcid
 4427 ?        00:00:00 sdpd
 4437 ?        00:00:00 krfcommd
 4456 ?        00:00:00 anacron
 4470 ?        00:00:00 atd
 4483 ?        00:00:00 cron
 4510 ?        00:00:00 apache2
 4511 ?        00:00:00 apache2
 4512 ?        00:00:00 apache2
 4514 ?        00:00:00 apache2
 4634 ?        00:00:00 sshd
 4636 ?        00:00:00 sshd
 4637 pts/0    00:00:00 bash
 4653 pts/0    00:00:00 ps


Primarily it is running Xorg, ssh, and apache.  SMB is unconfigured as of yet.

---

### Post by po0f on 2007-01-30
koolguynet,

I forgot to ask: is there a gradual increase in load, or does it spike?  Someone might be DOS'ing you; check you Apache/SSH logs for unusual activity.

---

### Post by koolguynet on 2007-01-30
l'll monitor it more closely this time around.  I could just close the firewall ports and see if it is more stable.

---

### Post by koolguynet on 2007-01-31
It has been up for 24 hours...here is the uptime results:

uptime
 22:00:21 up 1 day, 44 min,  1 user,  load average: 0.00, 0.00, 0.00


doesn't look like load is an issue right now

---

### Post by koolguynet on 2007-02-02
OK, I just had it "crash".  Here is what happened.  I used SCP and sent over a folder (which went fine).  Closed SCP and about five minutes later went to ssh to the box.  The first attempt timed out, the second attempt allowed me to login but it won't give me a command prompt immediately.  I had to wait about five minutes for the prompt.  Here is the uptime command output:


casita:~$ uptime
 00:29:49 up 2 days,  3:14,  1 user,  load average: 2.32, 0.78, 0.28


and here is PS -A
 ps -A
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 migration/0
    3 ?        00:00:00 ksoftirqd/0
    4 ?        00:00:00 watchdog/0
    5 ?        00:00:00 events/0
    6 ?        00:00:00 khelper
    7 ?        00:00:00 kthread
    9 ?        00:00:00 kblockd/0
   10 ?        00:00:00 kacpid
   11 ?        00:00:00 kacpi_notify
   91 ?        00:00:00 kseriod
  126 ?        00:00:00 kswapd0
  127 ?        00:00:00 aio/0
 1722 ?        00:00:00 khubd
 1821 ?        00:00:00 kjournald
 1898 ?        00:00:00 logd
 2011 ?        00:00:01 udevd
 2755 ?        00:00:00 shpchpd
 2826 ?        00:00:00 kpsmoused
 3210 ?        00:00:00 kjournald
 3440 tty1     00:00:00 getty
 3441 tty2     00:00:00 getty
 3442 tty3     00:00:00 getty
 3443 tty4     00:00:00 getty
 3444 tty5     00:00:00 getty
 3445 tty6     00:00:00 getty
 3655 ?        00:00:00 acpid
 3778 ?        00:00:00 dd
 3780 ?        00:00:00 klogd
 3793 ?        00:00:00 kdm
 3857 ?        00:00:00 hpiod
 3860 ?        00:00:00 python
 3914 ?        00:00:00 apt-index-watch
 3930 ?        00:00:00 dbus-daemon
 3945 ?        00:00:01 hald
 3946 ?        00:00:00 hald-runner
 3954 ?        00:00:00 hald-addon-acpi
 3962 ?        00:00:00 hald-addon-keyb
 3966 ?        00:00:00 hald-addon-keyb
 3975 ?        00:00:00 hald-addon-stor
 4313 ?        00:00:00 thinkpad-keys
 4324 ?        00:00:00 hald-addon-keyb
 4353 ?        00:00:00 nmbd
 4355 ?        00:00:00 smbd
 4360 ?        00:00:00 smbd
 4374 ?        00:00:00 sshd
 4420 ?        00:00:00 hcid
 4427 ?        00:00:00 sdpd
 4437 ?        00:00:00 krfcommd
 4470 ?        00:00:00 atd
 4483 ?        00:00:00 cron
 4858 ?        00:00:00 apache2
 4859 ?        00:00:00 apache2
 4860 ?        00:00:00 apache2
 4862 ?        00:00:00 apache2
 4917 ?        00:00:00 cupsd
 6715 ?        00:00:07 Xrealvnc
 6747 ?        00:00:00 dbus-launch
 6748 ?        00:00:00 dbus-daemon
 7577 tty7     00:00:01 Xorg
 7578 ?        00:00:00 kdm
 7583 ?        00:00:02 kdm_greet
 8196 ?        00:00:00 syslogd
 8663 ?        00:00:00 pdflush
 8665 ?        00:00:00 pdflush
 8689 ?        00:00:00 sshd
 8691 ?        00:00:00 sshd
 8692 pts/0    00:00:00 bash
 8710 pts/0    00:00:00 ps

Any ideas what is causing this load spike?

---

### Post by koolguynet on 2007-02-02
Here is a snapshot of 'top':  (btw...commands are taking about 60 seconds to display the output)



top - 00:30:03 up 2 days,  3:14,  1 user,  load average: 2.47, 0.89, 0.32
Tasks:  69 total,   3 running,  66 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.1%us,  0.0%sy,  0.0%ni, 99.3%id,  0.6%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    645024k total,   637620k used,     7404k free,   187088k buffers
Swap:  1951856k total,      208k used,  1951648k free,   347744k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 8665 root      15   0     0    0    0 S  0.3  0.0   0:00.04 pdflush
    1 root      16   0  1632  532  448 S  0.0  0.1   0:01.15 init
    2 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0
    3 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    4 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 events/0
    6 root      11  -5     0    0    0 S  0.0  0.0   0:00.02 khelper
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    9 root      10  -5     0    0    0 S  0.0  0.0   0:00.03 kblockd/0
   10 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
   11 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify
   91 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 kseriod
  126 root      15   0     0    0    0 S  0.0  0.0   0:00.14 kswapd0
  127 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
 1722 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khubd
 1821 root      10  -5     0    0    0 S  0.0  0.0   0:00.48 kjournald
 1898 root      15   0  1600  544  468 S  0.0  0.1   0:00.00 logd

Here is ifconfig for my public interface (doen't look like any DoS attacks, does it?)
eth0      Link encap:Ethernet  HWaddr 00:09:6B:F3:19:7E
          inet addr:216.31.XXX.XX  Bcast:216.31.XXX.XXX  Mask:255.255.248.0
          inet6 addr: fe80::209:6bff:fef3:197e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31212 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15466 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:13199841 (12.5 MiB)  TX bytes:1931624 (1.8 MiB)

---

### Post by koolguynet on 2007-02-14
Ok after my last post, the machine seemed to stabilize to a certain extent.  I unplugged its WAN interface to rule out DoS.  I am not sure when it happened (I have been out of town) it started up again.  I went to log into KDE and it took about 2.5 hours to get to the screen.  This is really a deal breaker for me.  I have to get this working, anyone have any ideas?

---

### Post by koolguynet on 2007-02-22
This is my last shot to see if anyone can offer me some help.  This is really causing me serious problems, if I can't figure out what this is then I will have to back down to 6.06 and if that doesn't work then Windows goes back on the box (which is not what I wish to do).  Anyone have any ideas?

---

### Post by tallman9 on 2007-02-22
[http://kmandla.wordpress.com/2006/11/11/howto-set-up-edgy-for-speed/](http://kmandla.wordpress.com/2006/11/11/howto-set-up-edgy-for-speed/)
just try to optimize your system...perhaps you have some cron or anacron service running regularly at that time.
also try installing sysv-rc-conf  ...
[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

---

### Post by koolguynet on 2007-02-22
I'll do that.  Thanks!

---

