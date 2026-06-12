---
title: "Hostname resets after rebooting"
date: 2014-01-29
forum: General Help
---

### Post by michael102 on 2014-01-29
Hello Gurus,

I have an unmanaged VPS running Ubuntu 12.04.3 LTS (precise), the default host name it came with was very long "vps-1148921-19454.manage.myhosting.com" so I wanted to change it to something shorter like "**ubuntu-1**". I read that I could simply edit /etc/hostname & /etc/hosts, however my changes always get reset after every reboot.

My Changes:
[PHP]
$echo "ubuntu-1" > /etc/hostname
$hostname -F /etc/hostname
$hostname
    ubuntu-1

$cat /etc/hosts
    127.0.0.1       localhost
    #my edit is below this line
    127.0.1.1       ubuntu-1
    ::1             localhost ip6-localhost ip6-loopback
    fe00::0         ip6-localnet
    ff00::0         ip6-mcastprefix
    ff02::1         ip6-allnodes
    ff02::2         ip6-allrouters
    # Auto-generated hostname. Please do not remove this comment.
    192.30.165.158 vps-1148921-19454.manage.myhosting.com vps-1148921-19454
[/PHP]

The changes seems to take effect, however after Rebooting (sudo reboot) my changes are lost, it resets to the following:

[PHP]
$hostname
    vps-1148921-19454.manage.myhosting.com

$cat /etc/hostname
    vps-1148921-19454.manage.myhosting.com
[/PHP]

/etc/hosts keeps the same contents

Any help would be appreciated.

---

### Post by Habitual on 2014-01-29
"Maybe", just maybe change:
```
192.30.165.158 vps-1148921-19454.manage.myhosting.com vps-1148921-19454
``` to 
```
192.30.165.158 ubuntu-1 
```

have you contacted myhosting.com support about this issue?

---

### Post by jeanjd63 on 2014-01-29
Hello

Have-you try the commands :
[B]sudo  -i
hostname [COLOR=#000000][FONT=Ubuntu Mono]ubuntu-1
exit[/FONT][/COLOR][/B]

---

### Post by michael102 on 2014-01-29
Thanks guy, the issue is resolved. I had to change it through my VPS console page, apparently those settings would overwrite anything I did on command line. 

My hosts entry now looks like:
192.30.165.158 ubuntu-1.com ubuntu-1

---

### Post by Habitual on 2014-01-30
VPSs, you have to love 'em. ;)
Glad it worked out.

---

