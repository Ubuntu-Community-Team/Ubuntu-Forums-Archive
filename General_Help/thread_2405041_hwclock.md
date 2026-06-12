---
title: "hwclock"
date: 2018-10-31
forum: General Help
---

### Post by barium2 on 2018-10-31
18.04 delivers a nastygram to me when running 'hwclock'. The reply is:[INDENT]
hwclock:Cannot access Hardware Clock via any known method
hwclock:Use the --debug option to see details of your search for an access method
[/INDENT]

Running 'hwclock --debug'  yields:[INDENT]
Trying to open /dev/rtc0
No usable clock interface found.
hwclock: Cannot access the Hardware Clock via any known method
[/INDENT]


I verified the device 'rtc' exists in the /dev directory. It points to 'rtc0'

Several searches indicate that I need to enable it in 'menuconfig'. I do not
know what menuconfig is and where to find it. Tried to run it at a command
prompt but received a message 'command not found'. Other articles reference 
building a new kernel. Are these accurate answers and if so which is preferable? 
How does one run 'menuconfig' in 18.04?

Thanks

Barry

---

### Post by #&amp;thj^% on 2018-11-01
Did you try with "sudo"?
Mine shows:
```
sudo hwclock
[sudo] password for me: 
2018-11-01 09:15:16.061707-06:00

```
Without "sudo":
```
hwclock
hwclock: Cannot access the Hardware Clock via any known method.
hwclock: Use the --verbose option to see the details of our search for an access method.
```

---

### Post by barium2 on 2018-11-02
ROTFL. Thanks for the sanity check. You hit the 
nail on the head as when I prefaced hwclock with 
sudo, all was fine. Mea Culpa.

Barry

---

