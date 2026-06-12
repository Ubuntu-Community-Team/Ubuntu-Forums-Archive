---
title: "Numeric keypad stopped working"
date: 2008-05-27
forum: General Help
---

### Post by cybrsaylr on 2008-05-27
Been using linux about a yr. Started out with Fedora then went to Ubuntu. Just joined the Forum.

A couple hours ago the numeric numbers keypad on the right side of my keyboard stopped working with Ubnutu Hardy Heron. I have to use the numbers across the top of the keyboard which is a real pain. I have a dual boot desktop system with XP and Hardy and when I go back to XP the numbers pad works fine. Then I go back to HH and it won't work. I tried checking the keyboard options in HH and all looks like it's setup right but after fooling around with settings I still can't get it to work like before. The 'Num Lock' indicator light seems to be working normal. Checked the Num Lock state and all appears normal.
Anyone have any ideas on how to get it working normal again with HH?

---

### Post by hanexar on 2008-05-28
I have the exact same problem here, exept it just showed up this weekend for no obvious reason...

---

### Post by hanexar on 2008-05-28
Oh, got this:

[http://ubuntuforums.org/showthread.php?t=807526&highlight=numeric+keypad+-working](http://ubuntuforums.org/showthread.php?t=807526&highlight=numeric+keypad+-working)

worked great!

---

### Post by chrisccoulson on 2008-05-28
I responded to a bug report on Launchpad a couple of weeks ago from someone with a similar issue, but the original reporter never responded.

The bug report is here: [https://bugs.launchpad.net/ubuntu/+bug/231173]("https://bugs.launchpad.net/ubuntu/+bug/231173")

My response:
> 

Are you referring to the number keys along the top row of the keyboard, or the number key pad? If it is the pad, can you turn Num Lock on and off? Do the keys only not work in X? (Could you try switching to a terminal by doing CTRL+ALT+F1 and logging in, then test the keys to see if they work).

If they only stop working in X, could you run 'xev' in a terminal, move your mouse cursor to the window that appears and press the keys which aren't working (with both num lock on and off) to see if any events are registered. Could you attach the output as a text file?

Thanks


Could you please follow my instructions and report your results

---

### Post by cybrsaylr on 2008-05-28
Thanks hanexar,
I went to the thread you showed on post #3 above and followed the advice there and got my numeric keypad working again! You really get hooked on that keypad. Having to use the numbers across the top on the keyboard is a real pain.

---

### Post by wilberfan on 2008-10-27
Ctrl-Shift-NumLock fixed this for me (based on #3 above).

:)

---

### Post by provoko on 2011-09-23
> **wilberfan said:**
> ctrl-shift-numlock fixed this for me (based on #3 above).

:)

thank you!!!!!

---

