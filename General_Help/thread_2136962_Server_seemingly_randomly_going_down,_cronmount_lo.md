---
title: "Server seemingly randomly going down, cron/mount loop involved?"
date: 2013-04-19
forum: General Help
---

### Post by Asday on 2013-04-19
My server is going down with little known provocation.  Wouldn't be too much of an issue, except the motherboard likes to play hard to get, and only POSTs one in ten times, but anyway.

It happened today twice in quick succession.  Both were after mounting an NTFS hard disk image to a mount point in a ramdisk (I think that's the right way to say it), and possibly accessing it from windows over Samba.

I have the hard disk image at /media/13s/herp.img, and the ramdisk (10G in size) mounted at /media/ramdisk.  I mount the right partition of the hard disk image with ```
parted /media/13s/herp.img unit B print
``` to find the offset, and then ```
sudo mount -o loop,offset=xxxxxxxx /media/13s/herp.img /media/ramdisk/herp
```.

The first crash happened after I opened the folder in windows, (\\futureserver\ramdisk\herp).  I then closed the window, and shortly afterwards, ubuntu crashed.

The second crash happened after someone else was copying a folder from the disk image, also in windows.  I was, at the time, running ```
sudo apt-get update && sudo apt-get upgrade
```.  It crashed while downloading stuff, and no system changes where made.

The first crash, I was browsing samba with Windows 7.  The second was someone on Windows XP.

The log, at /var/log/messages, however, had this to say:

```
Apr 19 09:38:01 futureserver anacron[1103]: Job `cron.daily' started
Apr 19 09:38:01 futureserver anacron[2454]: Updated timestamp for job `cron.daily' to 2013-04-19
Apr 19 09:38:04 futureserver ddclient[1143]: WARNING:  file /var/cache/ddclient/ddclient.cache, line 4: Invalid Value for keyword 'ip' = ''
Apr 19 09:38:04 futureserver ddclient[1143]: WARNING:  updating xxxxxx.xxxxxxxxxx.com: nochg: No update required; unnecessary attempty so change the current address are considered abusive
Apr 19 09:48:13 futureserver kernel: imklog 5.8.6, log source = /proc/kmsg started.
```

Which lead me to believe something to do with cron was the problem.

Thing is, I've had >31 day uptimes on this before, and this problem only started happening recently, but nothing that I can think of has changed.

I would really really appreciate any help.

---

### Post by Cheesehead on 2013-04-19
> **Asday said:**
> the motherboard likes to play hard to get, and only POSTs one in ten times, but anyway.

Seems like you have hardware failure if you can't even POST. Time to replace the motherboard in that server.

> **Asday said:**
> 
```
Apr 19 09:38:01 futureserver anacron[1103]: Job `cron.daily' started
Apr 19 09:38:01 futureserver anacron[2454]: Updated timestamp for job `cron.daily' to 2013-04-19
Apr 19 09:38:04 futureserver ddclient[1143]: WARNING:  file /var/cache/ddclient/ddclient.cache, line 4: Invalid Value for keyword 'ip' = ''
Apr 19 09:38:04 futureserver ddclient[1143]: WARNING:  updating xxxxxx.xxxxxxxxxx.com: nochg: No update required; unnecessary attempty so change the current address are considered abusive
Apr 19 09:48:13 futureserver kernel: imklog 5.8.6, log source = /proc/kmsg started.
```

Which lead me to believe something to do with cron was the problem.

Seems unlikely - the crash happened over 10 minutes after the daily cron jobs launched.
Your crash didn't leave an entry in that log (hardware failure wouldn't)
Also, cron.daily only runs once each day and anacron runs at each startup. Neither matches your pattern of crashes.

---

### Post by Asday on 2013-04-19
The motherboard has been like this since I built the thing, (and when it set the month long uptimes), so I'm not worried about that.  It's only a problem before I get an opportunity to hit Del or F2.  While it is undeniably a problem, it is one to fix for another time.  Money and time are limiting factors.

That last line in the log (ten minutes later) was the next boot.  I think.  It took me about 10 minutes to restart the thing.  :38 is about the right time to line up with the crash.

How do I check hardware errors?  Or is that not unique to linux; just swap stuff out?

---

### Post by Cheesehead on 2013-04-20
Rebooting causes a huge of log activity. Did you edit all that out of the 10-minute gap?

Check /var/log/dmesg after a failure, too. Be warned, it's pretty big, and lots of boot activity. If you have a hardware fault, sometimes you can see it flicking on/off in that log. Or you can see the cascade of failures leading to a kernel panic.

Describe the crash: Lockup but mouse moves? Total lockup including mouse but clear image? Scrambled image? Kernel Panic screen? Revert to login screen? Poweroff? Black screen? Any beeping or flashing lights? Something different? Any warning before the crash?

---

### Post by Asday on 2013-04-20
> **Cheesehead said:**
> Rebooting causes a huge of log activity. Did you edit all that out of the 10-minute gap?

Check /var/log/dmesg after a failure, too. Be warned, it's pretty big, and lots of boot activity. If you have a hardware fault, sometimes you can see it flicking on/off in that log. Or you can see the cascade of failures leading to a kernel panic.

Describe the crash: Lockup but mouse moves? Total lockup including mouse but clear image? Scrambled image? Kernel Panic screen? Revert to login screen? Poweroff? Black screen? Any beeping or flashing lights? Something different? Any warning before the crash?

There was nothing in the ten minute gap; that's the first line of rebooting activity.  I neglected to put the rest of the huge log of activity in, 'cause it was implied.

I don't actually know about the crash.  The behaviour seems to be similar to a windows bluescreen, in that it instantly reboots, but for the motherboard issues, I can't tell if it's that, or it just hangs on the desktop, as of course I run the machine headless.

I'll check dmesg next time it goes down; is it simple enough to understand?

---

### Post by Cheesehead on 2013-04-20
Also check /var/log/syslog . Lots of good information there.

---

### Post by Asday on 2013-04-24
> **Cheesehead said:**
> Also check /var/log/syslog . Lots of good information there.

Ok, so the last few lines in syslog before it went down this time are:

```
Apr 24 10:32:22 futureserver named[1113]: error (network unreachable) resolving
'myip.dnsdynamic.org/A/IN': 2001:500:48::1#53
Apr 24 10:32:22 futureserver named[1113]: error (network unreachable) resolving
'myip.dnsdynamic.org/A/IN': 2001:500:c::1#53
Apr 24 10:32:22 futureserver named[1113]: error (network unreachable) resolving
'dns1.registrar-servers.com/A/IN': 2001:500:1::803f:235#53
Apr 24 10:32:22 futureserver named[1113]: error (network unreachable) resolving
'dns1.registrar-servers.com/AAAA/IN': 2001:500:1::803f:235#53
Apr 24 10:32:23 futureserver named[1113]: error (network unreachable) resolving
'org/DS/IN': 2001:500:2f::f#53
Apr 24 10:32:23 futureserver named[1113]: error (network unreachable) resolving
'org/DNSKEY/IN': 2001:500:b::1#53
Apr 24 10:32:23 futureserver named[1113]: error (network unreachable) resolving
'org/DNSKEY/IN': 2001:500:e::1#53
Apr 24 10:32:23 futureserver named[1113]: error (network unreachable) resolving
'org/DNSKEY/IN': 2001:500:40::1#53
Apr 24 10:32:23 futureserver named[1113]: error (network unreachable) resolving
'org/DNSKEY/IN': 2001:500:f::1#53
```

Please let me know if there's sensitive information in there I should be censoring.

This happened about 15 minutes after cron.hourly did something, but that looks unrelated.

Unfortunately, I can't understand dmesg, and there's a lot of it, so I'm not sure where a failure happened.

---

### Post by Cheesehead on 2013-05-02
Looks like your ddns config file is malformed.
The system keeps trying to resolve addresses from that config file that are not valid: 'org/DNSKEY/IN' and other silliness.

However, that should not cause a system crash.

/var/log/dmesg entries use a timestamp in seconds of uptime (seconds since boot).
So after a reboot, look for all the high numbers, then the jump back to zero.
[8020.15] stuff that happened right before a crash
[8021.20] more stuff that happened right before a crash
[0.00] system restart after the crash

---

