---
title: "Ubuntu MATE 16.04 freezes seconds after boot, stuck at login screen"
date: 2018-04-20
forum: General Help
---

### Post by aalok-sathe on 2018-04-20
[SIZE=5]**[SIZE=4]Background[/SIZE]**
[/SIZE]
Two weeks ago,
I was on the kernel `4.13.0-36`, and
a routine update installed `4.13.0-37` 
and `4.13.0-38` automatically. After that, I was unsuccessful in getting my laptop to boot beyond the login screen [(link to bug)][1].
I fixed (temporarily solved) it by removing `-37, -38`, and `apt-mark hold`ing -36. I continued to boot in `-36` without any issues for about two weeks now.

**[SIZE=4]Problem[/SIZE]**

I used my laptop as usual last night and then eventually shut it down. I believe I ran some routine updates through `apt`. Today morning I was unable to boot past the login screen.

Situation: My `grub` pops up by default. Then I choose the top option, which is `-36`. It runs through the boot process, asking me to unlock cryptswap. I do that. It finishes up, shows the login screen. Irrespective of whether or not I interact with it (e.g., moving the cursor around, typing my password really quick, or even booting into `tty2` or any other `tty`), it freezes in the next 6 seconds or so.

My current suspicion is that the problem must be caused by some recent package that was updated, or something to do with the kernels. Whatever it is, is crashing at login while trying to launch GUI. If I understand correctly, it is likely to be some process that occurs at startup.

[B]Things I have tried without much luck
[/B]
- `nomodeset` option: no luck
- `-36` recovery boot, and then trying to dpkg repair packages
- `chroot` followed by `apt upgrade` (according to [this][2] answer)
- reinstalling `-37, -38` because apparently "a fix was committed" at the same link to the bug above. (tried `nomodeset` with all these kernels, too, didn't work)
- switching to another `tty`: doesn't work because machine freezes irrespective of what you do within 5-6 seconds


[B]Logs and info
[/B]
I'm just trying to provide down here anything I think is relevant. If you believe something else might help, please let me know and I'll be happy to upload it.

- DMESG output through `chroot` session ([link][3])
- Auth log for one such failed boot ([link][4])
- `dpkg` log from the last successful graphical session (yesterday) (1. all: [link][5]; 2. only recently installed, filtered using `grep "install"`: [link][6])
- `syslog` from one such failed boot ([link][7])
- Basic information about hardware using `lspci` ([link][8])


  [1]: [https://bugs.launchpad.net/ubuntu/+source/intel-microcode/+bug/1759920](https://bugs.launchpad.net/ubuntu/+source/intel-microcode/+bug/1759920)
  [2]: [https://askubuntu.com/a/837219](https://askubuntu.com/a/837219)
  [3]: [https://pastebin.com/gZtcWfvF](https://pastebin.com/gZtcWfvF)
  [4]: [https://pastebin.com/BfYy9p4J](https://pastebin.com/BfYy9p4J)
  [5]: [https://pastebin.com/LmkP81w6](https://pastebin.com/LmkP81w6)
  [6]: [https://pastebin.com/PUqGPqft](https://pastebin.com/PUqGPqft)
  [7]: [https://pastebin.com/gGmKET1n](https://pastebin.com/gGmKET1n)
  [8]: [https://pastebin.com/jqRWJi2b](https://pastebin.com/jqRWJi2b)

---

### Post by cruzer001 on 2018-04-20
I only see xx-39 as having a fix.

[https://bugs.launchpad.net/ubuntu/+source/intel-microcode/+bug/1759920/comments/100](https://bugs.launchpad.net/ubuntu/+source/intel-microcode/+bug/1759920/comments/100)

[https://bugs.launchpad.net/ubuntu/+source/intel-microcode/+bug/1759920/comments/103](https://bugs.launchpad.net/ubuntu/+source/intel-microcode/+bug/1759920/comments/103)

---

