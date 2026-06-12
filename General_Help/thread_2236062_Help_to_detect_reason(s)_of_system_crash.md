---
title: "Help to detect reason(s) of system crash"
date: 2014-07-24
forum: General Help
---

### Post by chinmay3 on 2014-07-24
Hello Ubuntu community,
I am using trusty tahr on acer aspire 5920. I usually browse with firefox while listening music on clementine music player. But for last some time system gets hanged suddenly leaving me clueless. I want to find reasons behind this system crash. Thanks in Advance.:p

I have updated system but even though problem persists. Tried uninstalling and reinstalling clementine . I can't predict anything wrong from system log.

---

### Post by Bucky Ball on 2014-07-24
When it crashes, immediately open a terminal and issue:

```
dmesg
```

Hit enter. Near the bottom of the output should be a description of the crash that just happened and hopefully a clue to why. Post the relevant section here (between [code] tags [ /code], please ;)).

---

### Post by chinmay3 on 2014-07-24
It doesn't go into terminal mode. I tried pressing alt+ctr+f4/f5 with no luck. Only hard reboot is possible. Will "dmesg" be helpful after reboot?

---

### Post by Bucky Ball on 2014-07-24
Just open a terminal. Try and replicate the crash (browse and use Clementine) and when it crashes, open a terminal right there on the desktop from Accessories and type 'dmesg', without the apostrophes. It doesn't need to drop to a CLI (which you would get hitting F1-F6). Just a terminal in a running desktop is fine. ;)

PS: Dropping to a CLI, you could still get the dmesg by logging in and typing 'dmesg', but terminal fine.

---

### Post by grahammechanical on 2014-07-24
There is a utility called top that will show you which services are using the CPU and memory and how much of system resources they are using.

```
top
```

Run the command and watch what happens and see if the system is freezing due to the CPU being used to the maximum or the memory is being used to the maximum.

Does this happen if you a playing music through Rhythmbox? If it does not happen then the problem is with Clementine.

Regards.

---

