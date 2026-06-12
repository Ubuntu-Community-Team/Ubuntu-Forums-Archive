---
title: "Xubuntu 16.04.04 won't shut down"
date: 2018-08-22
forum: General Help
---

### Post by SagaciousKJB on 2018-08-22
I usually leave this computer on 24/7 and it runs a few dedicated services (apache,fail2ban,zoneminder,mythtv) and I think one of them is causing the computer to hang when trying to shut down.  It will blank out the screen and leave a blinking cursor, or sometimes go back to a tty1 log in screen, but will just sit there forever.

The only way I can get it to restart is either by physically restarting the machine, or doing Alt + SysRq R-S-E-I-U-B, and usually it will restart after the 'U' and if not I restart with 'B'.  Obviously this isn't ideal, and even though I don't often turn this machine off, I figure I should get it fixed.

Problem is I have no idea where to begin looking.  Can anyone think of some common suspects to search for in the logs files?  I'm also figuring that I'll have to search by looking through the timestamps of the logs to correspond to when I tried to shut the computer down?  The only issue is that with so many services running, I have a lot of different logs to sort through, so it's like looking for a needle in a haystack, except when looking for a needle you actually know what it looks like.

---

### Post by TheFu on 2018-08-22
Does **sudo shutdown now -h** work?  If it does, then this is just a GUI issue, so look there. If it doesn't, you'll need to look through those log files, probably at the tail end to see any issues. Check the timestamps on the log files to see which were touched recently.

You can also manually shutdown your services to see if that helps. I don't use mythtv or zoneminder, but I do use the others and don't have any problems with them cleaning ending as expected.

---

### Post by SagaciousKJB on 2018-08-25
shutdown -h now has the same behavior, but what I noticed is that if I shutdown in recovery/single-user mode then it is much faster, so I do think it must be a service that's slowing it down.  I haven't been able to make much sense of the log files though.

I believe this is the shutdown sequence.  It actually does shutdown eventually I've figured it out, but it takes about 2-3 minutes.  I believe that delay is taking place between the last few rsyslogd entries.



```
Aug 24 14:56:23 AMD systemd[1]: Stopping User Manager for UID 1000...
Aug 24 14:56:23 AMD systemd[1]: Stopping ACPI event daemon...
Aug 24 14:56:23 AMD cpufreqd: event_wait               : Error polling ACPI Event handler (0x0011).
Aug 24 14:56:23 AMD systemd[1]: Stopping ZoneMinder CCTV recording and surveillance system...
Aug 24 14:56:23 AMD zmc_m11[19353]: ERR [Unable to read subheader]
Aug 24 14:56:23 AMD systemd[1]: Stopped target RPC Port Mapper.
Aug 24 14:56:23 AMD zmc_m10[19340]: ERR [Unable to read subheader]
Aug 24 14:56:23 AMD systemd[1700]: Stopped target Default.
Aug 24 14:56:23 AMD zmc_m12[19366]: ERR [Unable to read subheader]
Aug 24 14:56:23 AMD systemd[1700]: Reached target Shutdown.
Aug 24 14:56:23 AMD zmc_m11[19353]: ERR [Unable to get response, disconnecting]
Aug 24 14:56:23 AMD systemd[1700]: Starting Exit the Session...
Aug 24 14:56:23 AMD zmc_m10[19340]: ERR [Unable to get response, disconnecting]
Aug 24 14:56:23 AMD systemd[1700]: Stopped target Basic System.
Aug 24 14:56:23 AMD zmc_m12[19366]: ERR [Unable to get response, disconnecting]
Aug 24 14:56:23 AMD systemd[1700]: Stopped target Sockets.
Aug 24 14:56:23 AMD systemd[1700]: Stopped target Paths.
Aug 24 14:56:23 AMD systemd[1700]: Stopped target Timers.
Aug 24 14:56:23 AMD systemd[1]: Stopping Session c2 of user kenny.
Aug 24 14:56:23 AMD systemd[1]: Stopping Disk Manager...
Aug 24 14:56:23 AMD pulseaudio[16910]: [pulseaudio] main.c: 1 sink(s) available.
Aug 24 14:56:23 AMD systemd[16820]: Reached target Shutdown.
Aug 24 14:56:23 AMD pulseaudio[16910]: [pulseaudio] main.c:   * index: 0
Aug 24 14:56:23 AMD systemd[16820]: Stopped target Default.
Aug 24 14:56:23 AMD pulseaudio[16910]: [pulseaudio] main.c: #011name: <alsa_output.pci-0000_00_14.2.analog-stereo>
Aug 24 14:56:23 AMD systemd[16820]: Stopped target Basic System.
Aug 24 14:56:23 AMD pulseaudio[16910]: [pulseaudio] main.c: #011driver: <module-alsa-card.c>
Aug 24 14:56:23 AMD systemd[16820]: Stopped target Paths.
Aug 24 14:56:23 AMD pulseaudio[16910]: [pulseaudio] main.c: #011flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
Aug 24 14:56:23 AMD systemd[16820]: Stopped target Timers.
Aug 24 14:56:23 AMD pulseaudio[16910]: [pulseaudio] main.c: #011state: SUSPENDED
Aug 24 14:56:23 AMD snapd[990]: 2018/08/24 14:56:23.169758 main.go:78: Exiting on terminated signal.
Aug 24 14:56:23 AMD systemd[16820]: Stopped target Sockets.
Aug 24 14:56:23 AMD pulseaudio[16910]: [pulseaudio] main.c: #011suspend cause: IDLE
Aug 24 14:56:23 AMD systemd[16820]: Starting Exit the Session...
Aug 24 14:56:23 AMD rsyslogd: [origin software="rsyslogd" swVersion="8.16.0" x-pid="948" x-info="http://www.rsyslog.com"] exiting on signal 15.
Aug 24 14:58:06 AMD rsyslogd: [origin software="rsyslogd" swVersion="8.16.0" x-pid="966" x-info="http://www.rsyslog.com"] start
Aug 24 14:58:06 AMD rsyslogd-2222: command 'KLogPermitNonKernelFacility' is currently not permitted - did you already set it via a RainerScript command (v6+ config)? [v8.16.0 try http://www.rsyslog.com/e/2222 ]
Aug 24 14:58:06 AMD rsyslogd-2307: warning: ~ action is deprecated, consider using the 'stop' statement instead [v8.16.0 try http://www.rsyslog.com/e/2307 ]
Aug 24 14:58:06 AMD rsyslogd-2307: message repeated 15 times: [warning: ~ action is deprecated, consider using the 'stop' statement instead [v8.16.0 try http://www.rsyslog.com/e/2307 ]]
Aug 24 14:58:06 AMD rsyslogd: rsyslogd's groupid changed to 108
Aug 24 14:58:06 AMD rsyslogd: rsyslogd's userid changed to 104
```

So I was guessing the delay is in this...

```
Aug 24 14:58:06 AMD rsyslogd-2307: warning: ~ action is deprecated, consider using the 'stop' statement instead [v8.16.0 try http://www.rsyslog.com/e/2307 ]
Aug 24 14:58:06 AMD rsyslogd-2307: message repeated 15 times: [warning: ~ action is deprecated, consider using the 'stop' statement instead [v8.16.0 try http://www.rsyslog.com/e/2307 ]]
```

Since it says the message was repeated 15 times.

I followed the link to the rsyslog page, and basically there is use of a '~' where 'stop' now needs to be.

But the delay still persisted after that.

So I've narrowed it down to this part at least...

```
Aug 25 12:27:41 AMD systemd[1]: Stopping LSB: Speech Dispatcher...
Aug 25 12:27:41 AMD rsyslogd: [origin software="rsyslogd" swVersion="8.16.0" x-pid="966" x-info="http://www.rsyslog.com"] exiting on signal 15.
Aug 25 12:31:28 AMD rsyslogd: [origin software="rsyslogd" swVersion="8.16.0" x-pid="953" x-info="http://www.rsyslog.com"] start
Aug 25 12:31:28 AMD rsyslogd-2222: command 'KLogPermitNonKernelFacility' is currently not permitted - did you already set it via a RainerScript command (v6+ config)? [v8.16.0 try http://www.rsyslog.com/e/2222 ]
Aug 25 12:31:28 AMD rsyslogd: rsyslogd's groupid changed to 108
Aug 25 12:31:28 AMD rsyslogd: rsyslogd's userid changed to 104

```

So I found this option in /etc/rsyslog.conf/

```
$KLogPermitNonKernelFacility on
```

But I really don't know if it should be turned on or off.

Google netted me this problem that seems similar, though not quite, since it is causing his system to halt.  Though the suggested workaround was to simply comment out the option, so perhaps it's not needed?

[https://askubuntu.com/questions/937217/ubuntu-16-04-desktop-restart](https://askubuntu.com/questions/937217/ubuntu-16-04-desktop-restart)

According to the referenced server fault page

```
 From what I can tell this informs rsyslog to allow non-kernal events into syslog...

```

Which I do believe I need since it seems like I have plenty of non-kernel services logging to syslog.

It seems that these two bugs are somehow related, but I'm getting in over my head at this point.

[https://bugs.launchpad.net/ubuntu/+source/rsyslog/+bug/1531622](https://bugs.launchpad.net/ubuntu/+source/rsyslog/+bug/1531622)
[https://bugs.launchpad.net/ubuntu/+source/rsyslog/+bug/830046](https://bugs.launchpad.net/ubuntu/+source/rsyslog/+bug/830046)

I changed /dev/xconsole to /dev/console and so there's no longer any errors about that, but despite commenting out KLogPermitNonKernelFacility I still see errors about that in syslog, and it still takes 2-3 minutes to shutdown or restart.  There also seems to be plenty of non kernel log entries, so I don't think commenting it out even had any effect.

---

### Post by TheFu on 2018-08-26
Seems like you are following a logical path.

With my bias, when I looked at the logs, I saw  pulse audio and snap.  Snaps use a loopback mount. If that gets stuck ... shutdown would be stuck. I don't use snaps.

Killing pulse has never been an issue for me.  Had to do that about 20 times a day for a few years before it got better.

---

