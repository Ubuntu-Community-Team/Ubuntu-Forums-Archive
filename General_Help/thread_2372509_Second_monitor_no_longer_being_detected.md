---
title: "Second monitor no longer being detected"
date: 2017-09-26
forum: General Help
---

### Post by rlawson977 on 2017-09-26
Hello,

I am running Ubuntu 16.04.3 LTS on a HP Probook 430 G4. I have a HP EliteDisplay E232 monitor plugged in via HDMI and this usually works fine. This morning I came in and found that the monitor simply won't be detected by my laptop. This happened to me a few weeks ago and I re-installed my machine but I don't want to do that again hence seeking help. The only thing I can think  of is some sort of upgrade taking place. I found the following the apt logs:

Start-Date: 2017-09-26  07:45:54
Commandline: /usr/bin/unattended-upgrade
Upgrade: libplist3:amd64 (1.12-3.1, 1.12-3.1ubuntu0.16.04.1)
End-Date: 2017-09-26  07:45:55

I also went through /var/log/syslog but couldn't see anything that seemed interesting. 

Has this happened to anybody else?

---

### Post by rlawson977 on 2017-09-26
I just did and apt upgrade and apt update. Noticed the following output:

W: Possible missing firmware /lib/firmware/i915/kbl_dmc_ver1_01.bin for module i915

---

### Post by dragonfly41 on 2017-09-26
I am forced to use a second monitor since my primary monitor has failed.

If you install xrandr you can run the command xrandr in terminal to see if both monitors are identified.

---

