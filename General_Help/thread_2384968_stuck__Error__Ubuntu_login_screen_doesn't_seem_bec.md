---
title: "stuck : Error : Ubuntu login screen doesn't seem because of No Space Left on Device"
date: 2018-02-14
forum: General Help
---

### Post by papatya2 on 2018-02-14
I use dual (Windows 10 on HD + Ubuntu 16.04 on SSD) : It's ok
It was working a while ago.
When I choosed Ubuntu, then login screen was opening, it was ok.
But it is broken for somehow because No Space Left on Device error.
When I choose Ubuntu, then login screen doesn't seem.
Cntrl+Alt+F1 : command line, I can see the error.
/dev/sdb1 clean no space left on device.

$df -h
......
/dev/sdb1 184G %100
...

So I cannot do anything to fix with workarounds because sudo is not working.
For example :

$sudo df -h
sudo: /usr/bin/sudo must be owned by uid 0 and the setuid bit set.

Because I have used chmod 777 for sudo by mistake. I think it should have been 755 to run sudo.
But I cannot change it because just root user can do it. I don't know root user psw also, I didn't set any psw for root, it is default.

I try other things to fix sudo run :

$apt-get update
$apt-get install sudo
E: Write error - write (28: No space left on device)

Stuck... In a loop :

What should I do to make sudo run and gain some free space on SSD ?

---

### Post by Impavidus on 2018-02-14
Can you boot into recovery mode, drop to a root shell and remount the file system read-write?
[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)
You should then be able to fix sudo with```
chmod 4755 /usr/bin/sudo
```(Assuming that was all that was wrong with sudo.)

Then find out why you have no space left. Log files? Too many old kernels? Old caches? Collected to many media files? Just make sure you have a bit of headroom to get a working system.
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
Use **exit** to get out of recovery mode.

Then clean things up properly. It didn't take much time to go from a 95% full drive to a 100% full drive. If you make it again 95% full, it won't take long before the problem returns.

Edit: There is no root password in Ubuntu. And setting permissions on sudo to 4777 allows any ordinary user to open a root shell, which effectively means that every user is an admin.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by papatya2 on 2018-02-15
I found highest size file : error_log 179 GB
/var/log/cups/error_log

But how can I prevent it to be so high ?
How will I remove it ?

sudo rm /etc/cups/subscriptions.conf*

It gives :
rm: cannot remove '/etc/cups/subscriptions.conf' : Read-only file system
(conf.0 gives error also)

---

### Post by papatya2 on 2018-02-15
shutdown and start again.
I could remove error_log.
It seems to be OK.
It is running now. 
Thank you...

---

### Post by spjackson on 2018-02-15
> **papatya2 said:**
> I found highest size file : error_log 179 GB
/var/log/cups/error_log

But how can I prevent it to be so high ?
How will I remove it ?

sudo rm /etc/cups/subscriptions.conf*

It gives :
rm: cannot remove '/etc/cups/subscriptions.conf' : Read-only file system
(conf.0 gives error also)

See the link provided by Impavidus which says:
```

The root partition is mounted read-only. To mount it read/write, enter the command
mount -o remount,rw /

```
You should then be able to remove /var/log/cups/error_log. To find out why that file has got so large, you would need to look at it before you remove it. Perhaps you could mount other partitions (see the above link for details) and do say:
```

tail -1000 /var/log/cups/error_log > /some/file/on/another/partition.log

```
and post a sample here if you need help interpreting it. Alternatively, you could just remove the error log then after booting normally, inspect it once it starts growing again, if it does.

---

### Post by Impavidus on 2018-02-15
When a log file gets larger than a megabyte or so, depending a bit on which log file, something is wrong. Look for repeating messages.

---

### Post by papatya2 on 2018-02-16
I tried tail.
It says No such file or directory.
partition.log

---

### Post by papatya2 on 2018-02-16
File \”/usr/lib/cups/notifier/dbus\” has insecure permissions 0100777/uid...
Notifier for subscription dbus://

---

### Post by papatya2 on 2018-02-16
Solved :

sudo service cups stop
sudo rm /etc/cups/subscriptions.conf*
sudo rm -r /var/cache/cups
sudo service cups start

---

### Post by papatya2 on 2018-02-16
No
It doesn’t help.
Error_log keeps growing again.
Same logs.

---

### Post by Impavidus on 2018-02-16
> **papatya2 said:**
> I tried tail.
It says No such file or directory.
partition.log
I think the idea was you substituted something useful there. But if you already deleted the log, it doesn't matter. If the root cause of the problem wasn't solved, a new log with errors will be created automatically.

> **papatya2 said:**
> File \”/usr/lib/cups/notifier/dbus\” has insecure permissions 0100777/uid...
Notifier for subscription dbus://
Was that (part of) the repeating error message? In that case, you have permissions on more than one file seriously messed up.

> **papatya2 said:**
> Solved :

sudo service cups stop
sudo rm /etc/cups/subscriptions.conf*
sudo rm -r /var/cache/cups
sudo service cups start
Manual says```
       The  subscriptions.conf  file defines the local event notification sub&#8208;
       scriptions that are active. It is normally  located  in  the  /etc/cups
       directory  and  is maintained by the cupsd(8) program. This file is not
       intended to be edited or managed manually.
```
Doesn't sound like a way of solving problems without creating multiple new ones at the same time. I don't see how this could fix the insecure permissions of /usr/lib/cups/notifier/dbus. At best, it could prevent some deamon from checking it, so for a while the error messages may be gone.

We don't have enough information to tell you what the problem on your system is, but I get the impression it's a complete mess.

---

