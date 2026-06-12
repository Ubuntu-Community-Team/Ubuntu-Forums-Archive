---
title: "How to enable core dump permanently"
date: 2013-08-22
forum: General Help
---

### Post by jjaison-daniel on 2013-08-22
gusr1@tbox102:~$ echo $USER
gusr1
gusr1@tbox102:~$ grep -e core -e item /etc/security/limits.conf
#<domain>        <type>  <item>  <value>
#<item> can be one of the following:
#        - core - limits the core file size (KB)
#<domain>      <type>  <item>         <value>
gusr1               soft    core            unlimited
*                soft    core            unlimited
gusr1               hard    core            unlimited
*                hard    core            unlimited
#root            hard    core            100000
gusr1@tbox102:~$

Even though I set unlimited in /etc/security/limits.conf still the core dump size is zero.(checked after reboot also)
gusr1@tbox102:~$ ulimit -c
0

Any idea what else I have to check. In terminal if I "set ulimit -c unlimited" is working but after rebooting its gone.
I don't want set the core dump size in the any local profile, I wants to enable permanently in global way.

Also checked the following post, but not helpful to me
[http://ubuntuforums.org/showthread.php?t=1494590](http://ubuntuforums.org/showthread.php?t=1494590)

---

### Post by oldos2er on 2013-08-22
Moved to General Help.

---

### Post by jjaison-daniel on 2013-08-29
Added line "session required pam_limits.so" in the common-session, saw this in some google search. but still ulimit -c is zero. And in /etc/pam.d/login already has this.

gusr1@tbox102:~$ tail --lines=2 /etc/pam.d/common-session /etc/pam.d/common-session-noninteractive 
==> /etc/pam.d/common-session <==
session required pam_limits.so


==> /etc/pam.d/common-session-noninteractive <==
session required pam_limits.so

gusr1@tbox102:~$ grep pam_limits /etc/pam.d/login 
session    required   pam_limits.so

gusr1@tbox102:~$ ulimit -c
0

---

