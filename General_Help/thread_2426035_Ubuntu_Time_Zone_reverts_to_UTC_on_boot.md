---
title: "Ubuntu Time Zone reverts to UTC on boot"
date: 2019-09-03
forum: General Help
---

### Post by kbocek2 on 2019-09-03
I've newly installed Ubuntu 18.04.3 on two hosts, desktop on one, server  on another. The timezone on the server resets to UTC on each boot.

```
# cat /etc/timezone
America/Los_Angeles

# ls -la /etc/localtime
lrwxrwxrwx 1 root root 39 Sep  2 22:47 /etc/localtime -> /usr/share/zoneinfo/America/Los_Angeles
```

I've run [FONT=courier new]dpkg-reconfigure tzdata[/FONT] several times. I've tried[FONT=courier new] timedatectl set-timezone "America/Los_Angeles"[/FONT] too.

timedatectl shows:

```
Local time: Mon 2019-09-02 23:00:54 America
                  Universal time: Mon 2019-09-02 23:00:54 UTC
                        RTC time: Mon 2019-09-02 16:00:44
                       Time zone: America/Los_Angeles (America, +0000)
       System clock synchronized: no
systemd-timesyncd.service active: yes
                 RTC in local TZ: yes
```

I can't get the Local Time to show PDT like the desktop? I do have NTP installed and configured. Date shows UTC instead of PDT:

```
$ date
Tue Sep  3 20:18:13 UTC 2019

```

---

### Post by #&amp;thj^% on 2019-09-03
I just use the terminal for this stuff:
```
timedatectl set-local-rtc 1 --adjust-system-clock
```

To check out if your system uses Local time, just run:
```

timedatectl
```
To Revert back UTC use:
```

timedatectl set-local-rtc 0
```
Opps i may have missed the important feature you requested IE:
```
sudo timedatectl set-timezone PDT
```

---

### Post by TheFu on 2019-09-03
I just set the TZ environment variable in my .bashrc file.
```

#export TZ='Europe/London'; 
#export TZ='Asia/Bangkok'; 
# export TZ='Asia/Seoul'; 
# export TZ='Asia/Kathmandu'; 
# export TZ='Europe/Amsterdam'; 
# export TZ='Africa/Johannesburg';
export TZ='America/New_York';
```

Simple. Effective. Every user login can have their own.  I left a number of commented versions that I've used on travel.

---

### Post by kbocek2 on 2019-09-03
Nope set-local-rtc 1 still has the system in UTC. set-timezone says PDT is not a valid timezone.

As far as .bashrc settings, no I need to get the root environment to America/Los_Angeles or PDT. This is going to be a DVR and having local time is crucial for correct recordings.

I also tried:

[FONT=courier new]#TZ=America/Los_Angeles
#export TZ
[/FONT]
As well as PDT and "America/Los_Angeles". Nothing changed.

---

### Post by TheFu on 2019-09-03
All internal time is in UTC.  It is only the display of the time that changes.

Sorry - in bash - and most scripting languages, the '#' is a comment.  
```
export TZ='America/Los_Angeles'
```
would be correct, uncommented, assuming that was a valid location. I don't know if the single-quote is required or not, just that I've always used it.

The DVR wouldn't have any issue with UTC time. All computer TV schedule data uses UTC.  Which ever userid is running the DVR program, just set the environment as above for that userid or in whatever script starts is.
For the system, just set the timezone file with the value you want.
```

$ more /etc/timezone 
America/Los_Angeles
```
Do what with **echo "America/Los_Angeles" | sudo tee /etc/timezone **
is what [https://help.ubuntu.com/community/UbuntuTime](https://help.ubuntu.com/community/UbuntuTime) says.

On older releases, we'd use **dpkg-reconfigure tzdata**

---

### Post by kbocek2 on 2019-09-04
The hash mark was the root prompt. I suppose I could have left it off. So let me repeat my issue.

```
# timedatectl
                      Local time: Wed 2019-09-04 15:20:26 America
                  Universal time: Wed 2019-09-04 15:20:26 UTC
                        RTC time: Wed 2019-09-04 15:20:27
                       Time zone: America/Los_Angeles (America, +0000)
       System clock synchronized: no
systemd-timesyncd.service active: yes
                 RTC in local TZ: no

```
It says America for Local Time and under time zone 'America, +0000'. Date shows UTC:

```
# date
Wed Sep  4 15:22:35 UTC 2019
```

Doing your export command:

```
# export TZ='America/Los_Angeles'
# date
Wed Sep  4 15:23:51 America 2019

```
Just like timedatectl, local time is "America" and not "America/Los_Angeles"

Looks like I fixed it with:

```
# apt install --reinstall tzdata
```

```
# timedatectl
                      Local time: Wed 2019-09-04 08:38:17 PDT
                  Universal time: Wed 2019-09-04 15:38:17 UTC
                        RTC time: Wed 2019-09-04 15:38:18
                       Time zone: America/Los_Angeles (PDT, -0700)
       System clock synchronized: no
systemd-timesyncd.service active: yes
                 RTC in local TZ: no
```

---

### Post by TheFu on 2019-09-04
I'm in the middle of doing a fresh 18.04 server install.  It is patching now after I had to fight with a non-working DNS config immediately post-install.  Sad, so sad that DNS doesn't work out of the box. I did a manual network setup for IPv4.

```
tf@test-1804:~$ export TZ='America/New_York'
tf@test-1804:~$ date
Wed Sep  4 13:19:27 **EDT** 2019
tf@test-1804:~$ unset TZ
tf@test-1804:~$ date
Wed Sep  4 17:20:10 **UTC** 2019
```
Worked perfectly for a userid, tf.

For the entire server .... 
```
tf@test-1804:~$ more /etc/timezone 
Etc/UTC
tf@test-1804:~$ echo "America/New_York" | sudo tee /etc/timezone 
tf@test-1804:~$ more /etc/timezone 
America/New_York
# Now I rebooted ...
tf@test-1804:~$ date
Wed Sep  4 13:24:24 **EDT** 2019
tf@test-1804:~$ !more
more /etc/timezone 
America/New_York

```

Don't know what was happening elsewhere. Seems to work 100% as expected.

---

