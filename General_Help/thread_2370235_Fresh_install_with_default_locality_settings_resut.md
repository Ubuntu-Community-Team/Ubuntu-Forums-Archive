---
title: "Fresh install with default locality settings resuts in non-English keyboard settings."
date: 2017-09-01
forum: General Help
---

### Post by gbambo on 2017-09-01
I have a US market laptop. I installed 17.04 with locality defaults. My Y and Z key are reversed and a few others are too. Every time I install this I download new install image and get a differently crippled system. What is going on. How can separately download install images originating on different mirrors always produce non-functional installs? Especially given that Debian installs seem to work repeatedly.

The hardware was represented as Ubuntu 16 & 17 capable.

...

---

### Post by vasa1 on 2017-09-01
Please read [Suggestions on how to get your support questions answered as quickly as possible]("https://ubuntuforums.org/showthread.php?t=1422475")

You can install *inxi* and then post the output of ```
inxi -Fxzc0
```

Also useful would be the outputs of the following:
```
uname -a
```
```
env | grep XDG_CURRENT_DESKTOP
```
```
echo $DESKTOP_SESSION
```
```
lsb_release -a
```
```
cat /etc/*-release
```
```
cat /var/log/installer/media-info
```
```
cat /etc/debian_version
```
```
grep -Ev '(^#|^ *$|deb-src)' /etc/apt/sources.list /etc/apt/sources.list.d/*
```

---

