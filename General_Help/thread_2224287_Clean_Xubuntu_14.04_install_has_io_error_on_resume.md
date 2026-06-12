---
title: "Clean Xubuntu 14.04 install has i/o error on resume"
date: 2014-05-15
forum: General Help
---

### Post by 0graham0 on 2014-05-15
Hello,

I just performed a clean install of Xubuntu 14.04 on a Dell Dimension 4700. The machine seems to be running well in general however it fails to resume successfully after suspend. After rebooting I see no syslog entries after the suspend (as far as i can tell). When waking up the monitor displays a black screen with a white cursor with no response to the keyboard for 10 seconds or so. It then sits at a black screen. Switching to tty1 (ctrl+alt+f1) shows a few resume messages and then no prompt. Switching to tty2 and attempting to login results in various "end_request i/o error, dev sda, sector XXXX" messages.

The hard drive has no SMART errors and passes a short self-test. I was previously running Ubuntu 12.04 on the same drive with no issues (to my knowledge). I will attempt an extended self-test if necessary, however I was wondering if there were any other possible culprits before starting the hours long process.

Thanks

---

### Post by 0graham0 on 2014-05-15
I had received the above error 3 times in a row so I figured that was enough times to post about. Curiously enough I just attempted to recreate the problem to snap some photos and received a new set of messages:

[ATTACH=CONFIG]253193[/ATTACH]

---

### Post by 0graham0 on 2014-05-16
For the record I tested the hard drive and RAM overnight and they both passed with no issues.

---

