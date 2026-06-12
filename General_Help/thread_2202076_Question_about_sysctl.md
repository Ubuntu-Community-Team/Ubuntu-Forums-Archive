---
title: "Question about sysctl"
date: 2014-01-27
forum: General Help
---

### Post by michael95 on 2014-01-27
Hi again to everyone :)
so i was watching a video at youtube on fullscreen
when suddenly the screen becames white and the 
computer freeze but keyboard and mouse works

so i didnt what to do and i hard reset
today i was searching about and i fall
in the Magic SysRQ

and i have a question

when i run "gksudo gedit /etc/sysctl.conf" the line kernel.sysrq=1 doesnt exists

but then when i run "sudo sysctl -A | grep -i sysrq" the result is 

```

error: "Invalid argument" reading key "fs.binfmt_misc.register"
kernel.sysrq = 1
error: permission denied on key 'net.ipv4.route.flush'
error: permission denied on key 'net.ipv6.route.flush'
error: permission denied on key 'vm.compact_memory'

```


after i found another command "sudo cat /proc/sys/kernel/sysrq" with the respond 1

and my question as a new in Ubuntu is  

does the Command 1 and Command 2 intercept the same configuration file sysctl.conf
in the same directory /etc/sysctl.conf?

if yes how it is possible the second command to give the answer about kernel.sysrq value
and the first not?

and my second question

why the kernel.sysrq command in a two different paths 
and which path has the highest priority ?

Thanks and really sorry about this newbie question
Michael

---

### Post by mcduck on 2014-01-27
/etc/sysctl.conf is the config file, while anything in /proc doesn't actually exist on the disk, /proc is a special filesystem that displays all running processes as files (so what you see there is not the setting file, it's the actual value used by the kernel at the moment when you read from the file). IN this case the sysrq has already been enabled in Ubuntu's kernel at compilation time and therefore there is no need to specify it again in any configuration file.

---

### Post by michael95 on 2014-01-27
> **mcduck said:**
> /etc/sysctl.conf is the config file, while anything in /proc doesn't actually exist on the disk, /proc is a special filesystem that displays all running processes as files (so what you see there is not the setting file, it's the actual value used by the kernel at the moment when you read from the file). IN this case the sysrq has already been enabled in Ubuntu's kernel at compilation time and therefore there is no need to specify it again in any configuration file.

thanks you with your details 
and very well explained answer

i mark the thread as Solved

---

