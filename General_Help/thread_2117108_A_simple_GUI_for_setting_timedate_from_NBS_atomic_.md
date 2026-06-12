---
title: "A simple GUI for setting time/date from NBS atomic clock"
date: 2013-02-17
forum: General Help
---

### Post by RedRat on 2013-02-17
Back several versions of Ubuntu ago, I think 7 and 8, there were GUI programs for setting the system time and date from interrogating sources such as the National Bureau of Standards based on its atomic clock. I don't seem to find such programs now available in 12.04. Is there one. I know Windows had these pretty commonly but have not found one here. 

The closest thing I have found is "ntp" which is run from the CL.

---

### Post by The Cog on 2013-02-17
For just occasional use, I would use ntpdate rather than ntp. ntpdate is installed by default. However it is a command line utility. In the past, I have scheduled it under cron to run daily. 

I really can't see the need for a GUI for such a thing. But there is a package called system-config-date which might do for you.

---

### Post by mcduck on 2013-02-17
Unless you for some reason want to manually specify the time server, you really shouldn't need any extra tools. Just enable the "Set the time: Automatically from the Internet" option in Date&Time settings (although it should already be enabled by default). This option will use NTP servers to sync your clock.

---

### Post by RedRat on 2013-02-17
> **mcduck said:**
> Unless you for some reason want to manually specify the time server, you really shouldn't need any extra tools. Just enable the "Set the time: Automatically from the Internet" option in Date&Time settings (although it should already be enabled by default). This option will use NTP servers to sync your clock.
Just checked and I don't have that option. It only says "Network Time" which I think is the same as you mentioned. However, I think it only does that when the computer is turned on. I have noted that when I rouse the computer from its sleep, sometimes the time and date are off by a day or so. I have a suspicion that the internal battery might be going in the computer, at least that was one symptom I saw in my older computers. 

I was just hoping that there would be a simple GUI that I could click on that would automatically synchronize with the Bureau of Standards clock. I used ntpdate and that works but I have to open a terminal, and run it as root. Just a lot of fiddling around for something so simple.

---

### Post by tgalati4 on 2013-02-17
ntpd (from package ntp) uses very little resources.  

```
sudo apt-get install ntp
```

You won't need to worry about the correct time--ever.

---

### Post by JKyleOKC on 2013-02-17
+1

Using ntpd is the best way to keep your clock within a microsecond or so of the atomic clocks, at all times.

---

### Post by tgalati4 on 2013-02-18
Well, technically, you can be within a millisecond of national time standards with ntp.  To get microsecond accuracy, you have to tweak ntp with a "drift" file and 2nd order corrections.  By doing this, I was able to get ~250 microseconds (1/4 of a millisecond) consistently throughout the day.  The corrections account for thermal drift of your real-time clock and some correction for network latency.  If you are a horologist, you would get excited.

This is for a Drapper Drake (6.06) ntp server--really old:

tgalati4@tubuntu2:/etc$ cat ntp.conf
# Updated 20 Oct 08 to add new servers
logfile /home/tgalati4/ntp_stuff/ntp_trace.log
driftfile /var/lib/ntp/ntp.drift
# The next 4 lines adds statistics to /var/log/ntpstats--hopefully
statistics loopstats peerstats # clockstats
statsdir /var/log/ntpstats/
filegen peerstats file peers type day link enable
filegen loopstats file loops type day link enable
# filegen clockstats file clockstats type day link enable
server tick.cs.unlv.edu
server tick.mtnlion.com
#server tick.jpunix.net
server ntp1.stsn.net
server north-america.pool.ntp.org
server time.apple.com
# Beef up security policy--see hpubuntu's /etc/ntp.conf
restrict default kod notrap nomodify nopeer noquery
restrict 127.0.0.1 nomodify
broadcast 192.168.1.255

---

