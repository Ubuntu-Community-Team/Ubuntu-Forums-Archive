---
title: "NTP does not adjust offset"
date: 2015-04-08
forum: General Help
---

### Post by alex_p2 on 2015-04-08
Hi,

my Ubuntu HTPC won't set and correct the NTP offset.

E.g.:
```

root@kodi:~# date; service ntp stop; ntpd -q -g; service ntp start; date;hwclock -r
Wed Apr  8 17:20:50 CEST 2015
 * Stopping NTP server ntpd                                                                                    [ OK ]
ntpd: time set -168.557714s
 * Starting NTP server ntpd                                                                                    [ OK ]
Wed Apr  8 17:20:57 CEST 2015
Wed 08 Apr 2015 05:20:59 PM CEST  -0.989133 seconds

```

Hwclock runs fine.
No idea whats wrong here:

sudo ntpd -qgddd| pastebinit --> [http://paste.ubuntu.com/10773889/](http://paste.ubuntu.com/10773889/)

Does anyone have an idea how to fix this issue?
ntpdate does not work just as ntpd

---

### Post by tgalati4 on 2015-04-09
Check your button battery on the motherboard.  It's possible that your motherboard rtc is not keeping time correctly or there is too much jitter.  Your debug file has large time offsets, which usually means the rtc is not working correctly.  ntpd won't change a clock with large offsets.

How old is the system?

---

### Post by alex_p2 on 2015-04-09
The Hardware is from January this year. Furthermore the Hwclock shows the correct time, so rtc should work correctly?
Is there a way to hard adjust the offset?

---

### Post by SeijiSensei on 2015-04-09
I'm not sure this is what you are asking, but using:
```
sudo hwclock --systohc
```
or
```
sudo hwclock --hctosys
```
will set the hardware clock to the current system time or vice versa.

---

### Post by tgalati4 on 2015-04-09
Since you have a new motherboard, it's possible you have a problem with the version of the kernel that you are running.

```
uname -a
```

---

### Post by alex_p2 on 2015-04-09
Setting with HWClock doesn't work too:

```

root@kodi:~# hwclock --set --date "04/09/2015 16:43:10"
root@kodi:~# hwlock
-bash: hwlock: command not found
root@kodi:~# hwclock
Thu 09 Apr 2015 04:43:16 PM CEST  -0.937260 seconds
root@kodi:~# date
Thu Apr  9 16:45:45 CEST 2015
root@kodi:~# sudo hwclock --hctosys
root@kodi:~# date

```

Also tried an other kernel:

```
root@kodi:~# uname -a
Linux kodi 3.19.3-031903-lowlatency #201503261036 SMP PREEMPT Thu Mar 26 14:46:22 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

```

Before I had the following one:

```

ii  linux-image-3.13.0-48-generic                               3.13.0-48.80                          amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP

```

---

