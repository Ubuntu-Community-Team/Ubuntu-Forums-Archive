---
title: "computer turns off during different actions"
date: 2014-08-10
forum: General Help
---

### Post by soxterix on 2014-08-10
Since I've installed Ubuntu 14.04 in April my computer turned off about three times during that time. I can't recall what I was doing back then but it surprised me because it wasn't something unusual I was doing during that time. And as far as I remember it has never happend when I had 12.10, 13.04, 13.10. I was something that surprised me and I thought about posting here before but you know - it was like three times in four months. You can live with that. But just today it happend three times. First time I was installing netbeans and in the middle of installation computer turned off. And next two times after I clicked "print" in Document Viewer trying to print pdf file. The last time was not a turn off but a restart of the computer.
I can't say anything more because there is no alert before computer turns off, no error on the screen. It just turns off. I get black screen and in a second computer is turned off.
I have Ubuntu 14.04 64bit installed on the same hard drive with Kali Linux and Windows 7. It's Intel Core i3, 5GB RAM, 320GB hard drive with over 150GB for Ubuntu. And as I said before I had Ubuntu 12.10, 13.04, 13.10 before (always alongside Windows 7) on the same computer and I don't think it has happend before.
Any ideas what can couse this problem? Anyone had similar problem?

---

### Post by nerdtron on 2014-08-10
Once it happens again, post the output of "dmesg" and "cat /var/log/syslog" so that we can see some logs on what is happening on the system.

In the meantime, did you install any new applications before this started? Is your computer unusually hot during the time it rebooted?

---

### Post by soxterix on 2014-08-10
I'd say my computer is pretty hot all the time. In sensors software it shows Core 0: +83.0°C (high = +80.0°C, crit = +90.0°C), Core 2: +82.0°C (high = +80.0°C, crit = +90.0°C) right now. I don't think I've installed any new applications before this started. And it happend 20 minutes ago again (after I visited youtube page) so I attach files with "dmesg" and "cat /var/log/syslog" output.
Files are too big to attach here so I uploaded somewhere else. Dmesg: [http://www.speedyshare.com/KHYeh/dmesg.txt](http://www.speedyshare.com/KHYeh/dmesg.txt) and syslog: [http://www.speedyshare.com/VUaXW/syslog.txt](http://www.speedyshare.com/VUaXW/syslog.txt)
At the end of writing this message temperature decreased to 65 and 58.

---

### Post by nerdtron on 2014-08-10
I guess this says it all. From the the syslog file:

```
Aug 10 22:25:17 soxterix wpa_supplicant[806]: wlan0: CTRL-EVENT-SCAN-STARTED 
**Aug 10 22:28:09 soxterix kernel: [ 2195.266046] thermal thermal_zone0: critical temperature reached(90 C),shutting down**
Aug 10 22:28:09 soxterix rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="734" x-info="http://www.rsyslog.com"] exiting on signal 15.
Aug 10 22:29:13 soxterix rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="796" x-info="http://www.rsyslog.com"] start
```

If this is a laptop, you might want to open it up and clean the fan and grill from accumulated dusts. If you don't want to open, take it to a service center and have it cleanup.
You computer is way too hot. The automatic shutdown you experience is a safety mechanism of computers to shutdown before any further damage is done.

---

### Post by soxterix on 2014-08-14
Thanks a lot. But i would like to ask you to look at my log files again. I saved them right after last turn off and there is no similar message to message which you pointed out. This time it was during python installation. dmesg: [http://speedy.sh/TXAnG/dmesg.txt](http://speedy.sh/TXAnG/dmesg.txt) and syslog: [http://speedy.sh/scKNR/syslog.txt](http://speedy.sh/scKNR/syslog.txt)

---

