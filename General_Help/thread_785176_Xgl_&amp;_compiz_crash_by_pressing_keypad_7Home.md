---
title: "Xgl &amp; compiz crash by pressing keypad 7/Home"
date: 2008-05-07
forum: General Help
---

### Post by bijwaard on 2008-05-07
Dear all,

I upgraded to ubuntu hardy a week ago (and am up-to-date with current patches) and now get Xgl and Compiz crashes that take down my X session when I press the 7 (Home) button (or any other) on the numeric keypad of my keyboard. This happens every time, regardless of the NumLock status. I have visual effects set to extra, my card is an Nvidia: 01:00.0 VGA compatible controller: nVidia Corporation NV15 [GeForce2 GTS/Pro] (rev a4), I have a Dell AT101W keyboard. The Xorg log is attached.

There are no indications in the Xorg logfiles, only in the kernel log: 

May  7 10:28:59 workhorse kernel: [328395.638155] Xgl[11488]: segfault at 00000083 eip 0818db66 esp bfd2dfa0 error 4
May  7 10:32:03 workhorse kernel: [328579.834343] Xgl[20404]: segfault at 00000083 eip 0818db66 esp bfbdb520 error 4
May  7 10:45:20 workhorse kernel: [329376.114487] Xgl[21088]: segfault at 00000083 eip 0818db66 esp bf922390 error 4
May  7 10:45:20 workhorse kernel: [329376.148987] compiz.real[21267]: segfault at 04fb043b eip 08055a6d esp bffedb20 error 4
May  7 10:47:31 workhorse kernel: [329507.195963] Xgl[11093]: segfault at 00000083 eip 0818db66 esp bf99c340 error 4
May  7 10:47:35 workhorse kernel: [329510.405570] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
May  7 10:47:35 workhorse kernel: [329510.405613] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
May  7 10:47:35 workhorse kernel: [329510.405637] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
May  7 10:47:35 workhorse kernel: [329510.642866] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
May  7 10:47:35 workhorse kernel: [329510.642909] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
May  7 10:47:35 workhorse kernel: [329510.642933] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
May  7 10:47:56 workhorse kernel: [329532.077111] Xgl[21858]: segfault at 00000083 eip 0818db66 esp bfb2eda0 error 4
May  7 10:47:58 workhorse kernel: [329533.568809] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
May  7 10:47:58 workhorse kernel: [329533.568854] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
May  7 10:47:58 workhorse kernel: [329533.568878] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
May  7 10:47:58 workhorse kernel: [329533.806286] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
May  7 10:47:58 workhorse kernel: [329533.806330] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
May  7 10:47:58 workhorse kernel: [329533.806354] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode

---

### Post by pablo13 on 2008-05-08
Happens to me as well without compiz

---

### Post by Cyclops_ on 2008-05-09
Me too... me too...

I have compiz on, but don't know if it's related....

Though for me, it's keys 7, 6, and 1.  ( i haven't tried any of the others ).  My wife says that 0 deletes words.  

All regardless of the Num Lock status.

---- In addition ----

I set the Caps Lock Key to be an additional Ctrl Key, and (it works) but every time I click it, the Caps Lock light toggles (just annoying).

On the latest Ubuntu upgrade.

---

### Post by stanhelp on 2008-05-23
I have the same problem pressing keypad number 1 7.  Still looking for fix.


Stanhelp

---

### Post by Forlong on 2008-05-23
You do not need Xgl on Hardy, remove it:
```
sudo apt-get remove xserver-xgl
```
Afterwards, restart X and see if it helped.

---

### Post by stanhelp on 2008-05-23
Thank you that worked it doesn't reset the screen anymore.  

Although, I'm still not able to use the keypad to enter numbers. Just found fix for this here:
[https://bugs.launchpad.net/ubuntu/+bug/197771](https://bugs.launchpad.net/ubuntu/+bug/197771)

Using the following steps.
To fix it on Hardy (If you have the problem) :
Go to :
1) System
2) Preferences
3) Keyboard (Tab: Mouse Keys)
4) Uncheck (Allow to control pointer using the keyboard).
This should fix the problem....!
on Hardy.

Stanhelp

---

### Post by bijwaard on 2008-05-23
Many thanks for helping me out here!
The crashes disappeared and I can use my numeric keypad again!
I also spread the word in ubuntu bug #227698 and #31907.

---

### Post by bijwaard on 2008-05-29
One problem with removing xserver-xgl is that compiz is no longer working (I have a legacy nvidia card):-(
I installed it again, and with the mouse-keys disabled on the numeric keyboard I don't have crashes when using the numeric keypad.
So the resolution is just to disable the mouse keys, xserver-xgl can remain.

---

### Post by wheezer on 2008-07-08
I just installed Hardy, and encountered this bug almost immediately.  I have now disabled Preferences > Keyboard > Mouse keys > "Allow to control the pointer using the keyboard" TWICE, and both times, it reset itself after a period of time (less than an hour) and the problem reappeared again.  I THINK it's Firefox3 resetting it, but cannot be sure yet.  This damn bug seems to be years old, according to launchpad, and still not fixed, so  I am not going to bother reporting it.  But this resetting constantly may force me to scream a little. 

Anyone know what is going on here, and how to make this more stable?

I have a fairly new nvidea G8600 card, if that's relevelant.

---

