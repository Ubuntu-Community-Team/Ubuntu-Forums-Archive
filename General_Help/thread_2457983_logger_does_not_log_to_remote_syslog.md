---
title: "logger does not log to remote syslog"
date: 2021-02-13
forum: General Help
---

### Post by tc2020 on 2021-02-13
Hello All,

I use logger command to send a message to a remote syslog. The message appears to be sent across but does not get logged in /var/log/syslog.  Am I missing something?  

My setup has two devices running Ubuntu 20.04 server LTS and logger version 2.34. The first device IP is 192.168.0.11 and the second, 192.168.0.12. There is no problem in logging message to local syslog on each device and also they can see each other on the network. I use tcpdump utility to check on traffic. Here is what I have:

Second device:
```
$ logger -n 192.168.0.11 "Test"
```

First device:
```
$ sudo tcpdump -n dst port 514 -v
tcpdump: listening on eth0, link-type EN10MB (Ethernet), capture size 262144 bytes
18:18:47.195022 IP (tos 0x0, ttl 64, id 50281, offset 0, flags [DF], proto UDP (17), length 150)
    192.168.0.12.36097 > 192.168.0.11.514: SYSLOG, length: 122
        Facility user (1), Severity notice (5)
        Msg: 1 2021-02-13T18:18:47.193781+00:00 ubuntu ubuntu - - [timeQuality tzKnown="1" isSynced="1" syncAccuracy="284500"] Test
```

On the first device, sudo tail -f /var/log/syslog does not show that message.

Any help would be greatly appreciated. Thanks.

---

### Post by DuckHook on 2021-02-13
You do not tell us if you set up the rsyslog client/server daemons properly. Have you followed instructions such as those below?
[https://www.linux.com/topic/networking/remote-logging-syslog-part-1-basics/](https://www.linux.com/topic/networking/remote-logging-syslog-part-1-basics/)
[https://linuxhint.com/send_linux_logs_remote_server/](https://linuxhint.com/send_linux_logs_remote_server/)

---

### Post by tc2020 on 2021-02-13
DuckHook,

Thanks for your response, very helpful.

Going through your second link , I realized I did not have the ports open in /etc/rsyslog.conf. I made the following changes to the file on both devices:

```
module(load="imudp")
input(type="imudp" port="514")
module(load="imtcp")
input(type="imtcp" port="514")
```

First device:
```
$  logger -n 192.168.0.12 "Test"
```

That logs the message to syslog on the second device. It works!.

Second device:
```
$  logger -n 192.168.0.11 "Test"
```

That does not log the message on the first device syslog. This may be due to syslog-ng that I have set up in the first device as log server to collect logs. Can this coexist with rsyslog?. 

Messages received on the first device:

```
$ sudo systemctl status rsyslog.service
&#9679; rsyslog.service - LSB: enhanced syslogd
     Loaded: loaded (/etc/init.d/rsyslog; generated)
     Active: active (exited) since Sat 2021-02-13 22:22:44 UTC; 4min 28s ago
TriggeredBy: &#9679; syslog.socket
       Docs: man:systemd-sysv-generator(8)
    Process: 1159 ExecStart=/etc/init.d/rsyslog start (code=exited, status=0/SUCCESS)

Feb 13 22:22:11 ubuntu systemd[1]: Starting LSB: enhanced syslogd...
Feb 13 22:22:44 ubuntu systemd[1]: Started LSB: enhanced syslogd.
```

The above was captured right after bootup. It looks like rsyslog got kicked out or something by syslog-ng?..

---

### Post by DuckHook on 2021-02-13
> **tc2020 said:**
> …does not log the message on the first device syslog. This may be due to syslog-ng that I have set up in the first device as log server to collect logs. Can this coexist with rsyslog?…
…It looks like rsyslog got kicked out or something by syslog-ng?
We have no idea of how much you've customized your install, how far off default configuration it is, and how many other apps/utilities/modules/services you have loaded on it. I've never tried rsyslog with syslog-ng, so have no idea how to answer your question. But since you've obviously added it, it's clear that you are not starting out from a pristine base and have instead a convoluted system that's not at a good baseline. As a rule, two apps of trying to do the same thing will usually conflict if only because they must claim the same resources, so it's a bad idea to just hork one on top of another.

It is far more difficult to straighten out a tangle than to start from a clean default environment. Instead of trying to pick your way through knots, you should purge as many apps as you can remember adding, get back to as close a default install as possible and then follow the steps in either of the above links.

---

### Post by tc2020 on 2021-02-14
DuckHook,

I fully understand what you were saying. As mentioned previously, the second device works and we can consider it as a clean setup as it uses the default rsyslog.conf. To solve my problem, I just uncommented the lines to open the ports in this file for rsyslog to receive my messages. Your second link pointed me to this solution. In some way, this thread can be marked as solved.

So you know, I have been experimenting ways to post messages to remote hosts. This is why these two devices have different software modules installed, such as syslog-ng on the first device. This syslog-ng was installed and with configuration entries I found on the net:
```

$ sudo apt install syslog-ng                            
$ sudo nano /etc/syslog/syslog-ng.conf

  

  @version: 3.5

  @include "scl.conf"

  @include "`scl-root`/system/tty10.conf"
      options {

          time-reap(30);

          mark-freq(10);

          keep-hostname(yes);

          };

      source s_local { system(); internal(); };
      source s_network {

          syslog(transport(tcp) port(514));

          };
      destination d_local {
      file("/var/log/syslog-ng/messages_${HOST}"); };
      destination d_logs {

          file(

              "/var/log/syslog-ng/logs.txt"
              owner("root")
              group("root")

              perm(0777)

              ); };

      log { source(s_local); source(s_network); destination(d_logs); };
  
$ sudo mkdir /var/log/syslog-ng
$ sudo touch /var/log/syslog-ng/logs.txt
$ sudo systemctl start syslog-ng
$ sudo systemctl enable syslog-ng
```

As in previous post, with this syslog-ng running in device #1, I could not post to its syslog from device #2.

To troubleshoot, I first commented out the tcp port 514 in rsyslog.conf since this port is used in syslog-ng as above. So the default rsyslog.conf looks like this now:
```

# /etc/rsyslog.conf configuration file for rsyslog
#
# For more information install rsyslog-doc and see
# /usr/share/doc/rsyslog-doc/html/configuration/index.html
#
# Default logging rules can be found in /etc/rsyslog.d/50-default.conf


#################
#### MODULES ####
#################

module(load="imuxsock") # provides support for local system logging
#module(load="immark")  # provides --MARK-- message capability

# provides UDP syslog reception
module(load="imudp")
input(type="imudp" port="514")

# provides TCP syslog reception
#module(load="imtcp")
#input(type="imtcp" port="514")

# provides kernel logging support and enable non-kernel klog messages
module(load="imklog" permitnonkernelfacility="on")

###########################
#### GLOBAL DIRECTIVES ####
###########################

#
# Use traditional timestamp format.
# To enable high precision timestamps, comment out the following line.
#
$ActionFileDefaultTemplate RSYSLOG_TraditionalFileFormat

# Filter duplicated messages
$RepeatedMsgReduction on

#
# Set the default permissions for all log files.
#
$FileOwner syslog
$FileGroup adm
$FileCreateMode 0640
$DirCreateMode 0755
$Umask 0022
$PrivDropToUser syslog
$PrivDropToGroup syslog

#
# Where to place spool and state files
#
$WorkDirectory /var/spool/rsyslog

#
# Include all config files in /etc/rsyslog.d/
#
$IncludeConfig /etc/rsyslog.d/*.conf
```


After the change, rebooted device #1. 
On device #2, posted message to device#1:
```
$ logger -n 192.168.0.11 Test

```

No message posted in syslog of device#1. This is consistent with the status of rsyslog.service as it says active( exited) as below:

```
$ sudo systemctl status rsyslog
&#9679; rsyslog.service - LSB: enhanced syslogd
     Loaded: loaded (/etc/init.d/rsyslog; generated)
     Active: active (exited) since Sun 2021-02-14 19:57:14 UTC; 1h 43min ago
TriggeredBy: &#9679; syslog.socket
       Docs: man:systemd-sysv-generator(8)
    Process: 1174 ExecStart=/etc/init.d/rsyslog start (code=exited, status=0/SUCCESS)

Feb 14 19:57:14 ubuntu systemd[1]: Starting LSB: enhanced syslogd...
Feb 14 19:57:14 ubuntu systemd[1]: Started LSB: enhanced syslogd.
```

Turning off the tcp port 514 in rsyslog.conf and stopping syslog-ng service did not change the rsyslog status, still active (exited).

One of my goals is to be able to use logger command line (or any Linux/Ubuntu command line) to post messages to central syslog collector server. Syslog-ng is used in this case. 

I will continue troubleshooting this issue, maybe start with a fresh Ubuntu install on device #1 and build up from there. I have Apache2, PHP, snmpd, snmptrapd, vsftpd, and couple other things. Having said that, I just use their default .conf with some minor edits, nothing really wild.

---

### Post by DuckHook on 2021-02-14
Please use standard system fonts and styles when posting, especially within *code* tags, as non&#8209;standard fonts render oddly on some browsers and mobile devices and can be hard to read or else fail to preserve output formatting.
> **tc2020 said:**
> …maybe start with a fresh Ubuntu install on device #1 and build up from there. I have Apache2, PHP, snmpd, snmptrapd, vsftpd, and couple other things. Having said that, I just use their default .conf with some minor edits, nothing really wild.
I'm not sure you need to go that far. Perhaps just back out syslog-ng, go back to standard syslog, then try again. It is unusual to want rsyslog to work in both directions, but I can't think of a reason why it can't be done.

I've only ever set up the daemon to report to a central log server—i.e. just one way—so have no experience with reporting bidirectionally. I wonder if that in itself can cause a loop, but again, I don't really see why it would be a problem. Hopefully, someone who has experimented with rsyslog more than I have drops in on this thread. I'm afraid that further advice on tweaking would be getting out of my league.

---

### Post by tc2020 on 2021-02-14
It's interesting on the font rendering on your end. I simply copied it from PuTTY and pasted it in, nothing fancy.

My device #1 with syslog-ng is intended to be set up for one direction (syslog collector) only, so it should be Ok. I just use logger command from it to post to the device #2. 

I do not have deep knowledge on the backend working relationship between syslog-ng and rsyslog. I assume they are independent in some way as long as I do not use the same tcp/udp ports for both. 

I also tried disabling syslog-ng ($systemctl disable syslog-ng), but still the same active(exited) from rsyslog status even after stop/start. I will continue with this and see how far I can get.

---

### Post by DuckHook on 2021-02-14
> **tc2020 said:**
> It's interesting on the font rendering on your end. I simply copied it from PuTTY and pasted it in, nothing fancy.
It might just be that, then. Nothing further to worry about.

---

