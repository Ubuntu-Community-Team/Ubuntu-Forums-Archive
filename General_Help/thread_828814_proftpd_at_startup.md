---
title: "proftpd at startup"
date: 2008-06-14
forum: General Help
---

### Post by BrainBurner on 2008-06-14
Hello,
I recently installed hardy. Now I wanted to enabled an ftp server, so I installed proftpd and gproftpd [as this guide explain]("http://ubuntuforums.org/showthread.php?t=79588").

I works fine, but it doesn't run at startup. I searched on the forum and I found [this post]("http://ubuntuforums.org/showthread.php?t=26049") about using update-rc.d.

So I did:
```
sudo update-rc.d -f proftpd remove
sudo update-rc.d proftpd defaults
```
But the problem didn't change: proftpd doesn't run at startup, qhat else can I do?

---

### Post by RealPSL on 2008-06-14
Have you tried sysv-rc-conf. You can install it with ```
sudo apt-get install sysv-rc-conf
```. Once installed launch it and configure proftpd at your run level (generally 2).

---

### Post by BrainBurner on 2008-06-15
It doesn't work too.
I looked in the log file and I see that proftpd is killed when I shut down, but it is not restarted!
```
Jun 15 21:26:27 ubuntu proftpd[6121] ubuntu: ProFTPD killed (signal 15)
Jun 15 21:26:27 ubuntu proftpd[6121] ubuntu: ProFTPD 1.3.1 standalone mode SHUTDOWN
```

I also tried to add the line
```
/etc/init.d/proftpd start
```
in /etc/rc.local but it doesn't work.

Any other idea?

---

### Post by reality1011 on 2008-06-15
You should add it to a specific rc level ... I have a DDNS script which runs on startup.  You need to create a link from /etc/rcX.d/S99<link-name> to /etc/init.d/<script>

Note: where the X in rcX is a number....

Make sure you chmod the script to 755 and have root own it...  Also read the README file in the directory to make sure you are doing everything right.

That should work.

---

### Post by RealPSL on 2008-06-15
Would love to see the output of the 2 commands ```
who -r;
ls -l /etc/rc2.d/*proftpd
```

I am assuming that you are booting to runlevel 2 which who -r will confirm. Replace the 2 with your run level.

---

### Post by BrainBurner on 2008-06-16
Here you can see mthe output:
```
         run-level 2  2008-06-16 00:19                   last=
lrwxrwxrwx 1 root root 17 2008-06-15 21:58 /etc/rc2.d/S20proftpd -> ../init.d/proftpd
```

Is there any problem?

---

### Post by reality1011 on 2008-06-16
Try changing the S20 to an S50....

I know the lower numbers are booted first, you might be booting proftp in the wrong order...  Here is my output... 

cappetta@Linux-Box:/etc$ ls -l /etc/rc2.d/*prof*
lrwxrwxrwx 1 root root 17 2007-07-27 17:07 /etc/rc2.d/S50proftpd -> ../init.d/pr                                                                oftpd

---

### Post by RealPSL on 2008-06-17
S20 should be fine unless your machine is using DHCP to obtain an IP address. My machine seems to have the DHCP client at S24 so S20 would mean proftpd is starting before an IP address is assigned which would mean it has no place to bind.

---

