---
title: "dmesg - smsc95xx 1-1.1:1.0: eth0: kevent 2 may have been dropped"
date: 2013-10-29
forum: General Help
---

### Post by Marchello_Lippi on 2013-10-29
Hi all, 

dmesg returns a lot of lines, here is small part: 

[80814.613795] smsc95xx 1-1.1:1.0: eth0: kevent 2 may have been dropped
[80814.613819] smsc95xx 1-1.1:1.0: eth0: kevent 2 may have been dropped
[80814.613844] smsc95xx 1-1.1:1.0: eth0: kevent 2 may have been dropped
[80814.613870] smsc95xx 1-1.1:1.0: eth0: kevent 2 may have been dropped
[80814.613894] smsc95xx 1-1.1:1.0: eth0: kevent 2 may have been dropped
[80814.613918] smsc95xx 1-1.1:1.0: eth0: kevent 2 may have been dropped
[80832.135765] net_ratelimit: 1165 callbacks suppressed
[80832.135808] smsc95xx 1-1.1:1.0: eth0: kevent 2 may have been dropped
[80832.135853] smsc95xx 1-1.1:1.0: eth0: kevent 2 may have been dropped
[80832.135970] smsc95xx 1-1.1:1.0: eth0: kevent 2 may have been dropped
[80832.136076] smsc95xx 1-1.1:1.0: eth0: kevent 2 may have been dropped
[80832.136126] smsc95xx 1-1.1:1.0: eth0: kevent 2 may have been dropped
[80832.136212] smsc95xx 1-1.1:1.0: eth0: kevent 2 may have been dropped
[80832.136248] smsc95xx 1-1.1:1.0: eth0: kevent 2 may have been dropped
[80832.136276] smsc95xx 1-1.1:1.0: eth0: kevent 2 may have been dropped
[80832.136301] smsc95xx 1-1.1:1.0: eth0: kevent 2 may have been dropped
[80832.136326] smsc95xx 1-1.1:1.0: eth0: kevent 2 may have been dropped

What does it mean?

---

### Post by tomearp on 2013-10-29
Not an error message I've come across before but there is a topic on the Raspberry Pi forums where people were reporting the same error message, but not much is given in terms of the cause.

[http://www.raspberrypi.org/phpBB3/viewtopic.php?p=134136]("http://www.raspberrypi.org/phpBB3/viewtopic.php?p=134136")

One suggested fix is to add 

smsc95xx.turbo_mode=N 

to /boot/cmdline.txt which would fix the issue at the expense of some network performance. 


Another proposed fix is detailed here [http://forum.stmlabs.com/showthread.php?tid=452&highlight=smsc95]("http://forum.stmlabs.com/showthread.php?tid=452&highlight=smsc95")

---

### Post by pqwoerituytrueiwoq on 2014-04-20
the [FONT=Courier New]vm.min_free_kbytes = 8192[/FONT] option is set stock in the copy i have installed
the other possible solution seems to be linked to high network usage, which at that time will have been nothing unless my router was chating with the pi or vice versa
only thing running at the time was mpd, which was still running and functioning (i have a toggle switch to toggle playback)
my voltage does drop during mp3 playback vs idle from 4.91v to 4.90v (read with multimeter)
my amperage reading using the TP1 and TP2 checkpoints is useless, i guess it does not work with getting power to the pi via usb A ports, there is no way 0.4mA is possible

---

