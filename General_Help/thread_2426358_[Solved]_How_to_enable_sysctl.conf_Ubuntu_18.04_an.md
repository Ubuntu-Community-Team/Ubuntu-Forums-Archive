---
title: "[Solved] How to enable sysctl.conf Ubuntu 18.04 and above?"
date: 2019-09-07
forum: General Help
---

### Post by mpugliesi2 on 2019-09-07
**&#8203;**&#8203;Hello folks.  

How to enable the sysctl.conf file again? What I need to do to enable it? I've seen that now we have many .conf files in folder /etc/sysctl.d .

But nothing works. I have created my own file, didn't worked. I have tried to edit de 99*.conf file, fail. 
Tried to fallow the instructions from README file inside the /etc/sysctl.d folder, return error!


What magic is necessary to be done?

---

### Post by #&amp;thj^% on 2019-09-07
Type the following command to reload settings from config files without rebooting the box:
```
# sysctl --system
```

The settings are read from all of the following system configuration files:

  ```
  /run/sysctl.d/*.conf
    /etc/sysctl.d/*.conf
    /usr/local/lib/sysctl.d/*.conf
    /usr/lib/sysctl.d/*.conf
    /lib/sysctl.d/*.conf
    /etc/sysctl.conf
```

---

### Post by mpugliesi2 on 2019-09-07
I did that and...

Did not work! :(

---

### Post by mpugliesi2 on 2019-09-07
What I want is simple.It worked pretty much straight forward:  echo "256" > /sys/block/sda/queue/nr_requests

So, I need that inside the sysctl.conf to override the standard number during boot time.  It worked before like a charm, old versions without  systemd . Not anymore.

---

### Post by #&amp;thj^% on 2019-09-07
> **mpugliesi2 said:**
> I did that and...

Did not work! :(

What? did it show like this:
```
sysctl --system
* Applying /etc/sysctl.d/00-local-userns.conf ...
sysctl: permission denied on key 'kernel.unprivileged_userns_clone'
* Applying /usr/lib/sysctl.d/10-arch.conf ...
sysctl: permission denied on key 'fs.inotify.max_user_instances'
sysctl: permission denied on key 'fs.inotify.max_user_watches'
* Applying /usr/lib/sysctl.d/50-coredump.conf ...
sysctl: permission denied on key 'kernel.core_pattern'
* Applying /usr/lib/sysctl.d/50-default.conf ...
sysctl: permission denied on key 'kernel.sysrq'
sysctl: permission denied on key 'kernel.core_uses_pid'
sysctl: permission denied on key 'net.ipv4.conf.all.rp_filter'
sysctl: permission denied on key 'net.ipv4.conf.all.accept_source_route'
sysctl: permission denied on key 'net.ipv4.conf.all.promote_secondaries'
sysctl: permission denied on key 'net.core.default_qdisc'
sysctl: permission denied on key 'fs.protected_hardlinks'
sysctl: permission denied on key 'fs.protected_symlinks'
sysctl: permission denied on key 'fs.protected_regular'
sysctl: permission denied on key 'fs.protected_fifos'

```

---

### Post by mpugliesi2 on 2019-09-07
Look:

```
root@bigbeta1-note:/etc/sysctl.d# [COLOR=#0000cd]cat /sys/block/sda/queue/nr_requests                               
64[/COLOR]
root@bigbeta1-note:/etc/sysctl.d# sysctl --system     
* Aplicando /etc/sysctl.d/10-console-messages.conf ...
kernel.printk = 4 4 1 7
* Aplicando /etc/sysctl.d/10-ipv6-privacy.conf ...
net.ipv6.conf.all.use_tempaddr = 2
net.ipv6.conf.default.use_tempaddr = 2
* Aplicando /etc/sysctl.d/10-kernel-hardening.conf ...
kernel.kptr_restrict = 1
* Aplicando /etc/sysctl.d/10-link-restrictions.conf ...
fs.protected_hardlinks = 1
fs.protected_symlinks = 1
* Aplicando /etc/sysctl.d/10-magic-sysrq.conf ...
kernel.sysrq = 176
* Aplicando /etc/sysctl.d/10-network-security.conf ...
net.ipv4.conf.default.rp_filter = 2
net.ipv4.conf.all.rp_filter = 2
* Aplicando /etc/sysctl.d/10-ptrace.conf ...
kernel.yama.ptrace_scope = 1
* Aplicando /etc/sysctl.d/10-zeropage.conf ...
vm.mmap_min_addr = 65536
* Aplicando /usr/lib/sysctl.d/50-default.conf ...
net.ipv4.conf.all.promote_secondaries = 1
net.core.default_qdisc = fq_codel
[COLOR=#ff0000]* Aplicando /etc/sysctl.d/60-nr-request.conf ...[/COLOR]
* Aplicando /etc/sysctl.d/90-override.conf ...
net.core.default_qdisc = cake
* Aplicando /etc/sysctl.d/99-sysctl.conf ...
* Aplicando /etc/sysctl.d/protect-links.conf ...
fs.protected_hardlinks = 1
fs.protected_symlinks = 1
* Aplicando /etc/sysctl.conf ...
root@bigbeta1-note:/etc/sysctl.d# [COLOR=#0000cd]cat /sys/block/sda/queue/nr_requests  
64[/COLOR]
root@bigbeta1-note:/etc/sysctl.d# 


```

Content inside de file: 60-nr-request.conf:

**echo "256" > /sys/block/sda/queue/nr_requests**

---

### Post by wildmanne39 on 2019-09-07
Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by #&amp;thj^% on 2019-09-07
Do you have a back-up of your now edited file? (The Original.)

---

### Post by mpugliesi2 on 2019-09-07
No back-up. I just created this file. Why?

---

### Post by SeijiSensei on 2019-09-08
Entries in sysctl.conf do not have format you're using. Here's the directive to enable IP packet forwarding for example:
```

net.ipv4.ip_forward = 1

```

However, that line references /proc/sys/net/ipv4/ip_forward.  There is no /proc/sys/block on my machine, but it does appear as /sys/block.  I don't know how one references that in sysctl.conf.  Putting the "echo" command you referenced in /etc/sysctl.conf will likely fail.

How about trying this:
```
echo 'echo "256" > /sys/block/sda/queue/nr_requests' >> /etc/rc.local
```
then rebooting.  Does that work?

---

### Post by #&amp;thj^% on 2019-09-08
Along with SeijiSensei's Advice,
If this is all your after then, If it were me I'd make the change in "/etc/udev/rules.d"
Something like this:
```
# nano /etc/udev/rules.d/71-nr-requests.rules

```
With this added:
```
SUBSYSTEM!="block", GOTO="end_rule"
ENV{DEVTYPE}=="partition", GOTO="end_rule"
ACTION!="add|change", GOTO="end_rule"
KERNEL=="sd*", ATTR{queue/nr_requests}="256" 
LABEL="end_rule"
```
Now to check:
```
# grep "" /sys/block/sd*/queue/nr_requests
/sys/block/sda/queue/nr_requests:256
/sys/block/sdb/queue/nr_requests:256
/sys/block/sdc/queue/nr_requests:256
/sys/block/sdd/queue/nr_requests:256
/sys/block/sde/queue/nr_requests:256

```
EDIT: Forgot to mention The rules above **will set nr_requests to 256 for all sd* devices, **if you need to blacklist some (e.g. sda, and sdb), use the rules like:

```
SUBSYSTEM!="block", GOTO="end_rule"
ENV{DEVTYPE}=="partition", GOTO="end_rule"
ACTION!="add|change", GOTO="end_rule"
KERNEL=="sda|sdb", GOTO="end_rule"
KERNEL=="sd*", ATTR{queue/nr_requests}="256"
LABEL="end_rule"
```


Also I use scheduler [bfq]:
```
# cat /sys/block/sda/queue/scheduler
mq-deadline kyber [bfq] none

```
This is Arch kernel:"Kernel: 5.2.11.a-1-hardened x86_64"

---

### Post by mpugliesi2 on 2019-09-08
Thank you  [[COLOR=#000000]SeijiSensei[/COLOR]]("https://ubuntuforums.org/member.php?u=698195")[COLOR=#000000] ![/COLOR]

[COLOR=#000000]It is working now. You were wright about de command, should be inside** rc.local** and not in **sysctl.conf**.   But it was necessary to create two files and activate de rc.local because of systemd.  

I followed this instructions to activate rc.local in Ubuntu 19.04: [/COLOR][https://www.linuxbabe.com/linux-server/how-to-enable-etcrc-local-with-systemd](https://www.linuxbabe.com/linux-server/how-to-enable-etcrc-local-with-systemd)

Thanks a lot!

---

### Post by mpugliesi2 on 2019-09-08
Thanks for the help [[COLOR=#000000]1fallen[/COLOR]]("https://ubuntuforums.org/member.php?u=2040855")[COLOR=#000000] ! 

The tip from [/COLOR][COLOR=#000000] [/COLOR][[COLOR=#000000]SeijiSensei[/COLOR]]("https://ubuntuforums.org/member.php?u=698195")[COLOR=#000000][COLOR=#000000]  plus a tutorial did the job!


[/COLOR][/COLOR]

---

