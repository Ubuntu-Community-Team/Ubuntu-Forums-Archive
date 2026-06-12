---
title: "Ubuntu ipv6 connetion"
date: 2019-10-17
forum: General Help
---

### Post by azadiyame on 2019-10-17
Hello
My customers can't connect to my system with ipv6. There was no problem with ipv4. But with ipv6, customers cannot access the system.

---

### Post by #&amp;thj^% on 2019-10-17
Does your provider have IPV6 working yet?
```
sysctl -a|grep disable_ipv6
```
Mine is disabled by myself:
```
sysctl: permission denied on key 'fs.protected_fifos'
sysctl: permission denied on key 'fs.protected_hardlinks'
sysctl: permission denied on key 'fs.protected_regular'
sysctl: permission denied on key 'fs.protected_symlinks'
sysctl: permission denied on key 'kernel.cad_pid'
sysctl: permission denied on key 'kernel.unprivileged_userns_apparmor_policy'
sysctl: permission denied on key 'kernel.usermodehelper.bset'
sysctl: permission denied on key 'kernel.usermodehelper.inheritable'
sysctl: permission denied on key 'net.core.bpf_jit_harden'
sysctl: permission denied on key 'net.core.bpf_jit_kallsyms'
sysctl: permission denied on key 'net.core.bpf_jit_limit'
sysctl: permission denied on key 'net.ipv4.tcp_fastopen_key'
sysctl: permission denied on key 'vm.mmap_rnd_bits'
sysctl: permission denied on key 'vm.mmap_rnd_compat_bits'
sysctl: permission denied on key 'vm.stat_refresh'

```

---

### Post by azadiyame on 2019-10-17
Hello there


He's working. But my customers can't connect to my system with ipv6.

---

### Post by #&amp;thj^% on 2019-10-17
Please show:
```
sysctl -a|grep disable_ipv6
```

---

### Post by Skaperen on 2019-10-17
can *you* connect to your system, from somewhere else?  if you post or PM an ipv6 address, i can try to ping it.

---

### Post by azadiyame on 2019-10-17
Hello

Don't I need to enable customers to connect?   [COLOR=#000000][FONT=&quot]disable_ipv6 [/FONT][/COLOR]Instead enabled? 

sysctl -a|grep disable_ipv6

---

### Post by #&amp;thj^% on 2019-10-17
> **azadiyame said:**
> Hello

Don't I need to enable customers to connect?   [COLOR=#000000][FONT=&quot]disable_ipv6 [/FONT][/COLOR]Instead enabled? 

sysctl -a|grep disable_ipv6

That does not disable ipv6 it just shows me if you have it disabled. 
Was there any output from that command?
EDIT: If this one make you feel better use:
```
test -f /proc/net/if_inet6 && echo "IPv6 supported" || echo "IPv6 not supported"
IPv6 not supported

```
As you can see mine is "IPv6 not supported"

---

### Post by Skaperen on 2019-10-17
the command "_sysctl -a|grep disable_ipv6_" is 2 programs running together in what is called a pipeline.  the "|" separates them.  the output of the 1st program is fed into the input of the 2nd program.  the 2nd program filters that data it gets to just lines that have the argument on the command line.  so, it's looking for any "_disable_ipv6_" in the output of the 1st program.

---

