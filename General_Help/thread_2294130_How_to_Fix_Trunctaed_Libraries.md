---
title: "How to Fix Trunctaed Libraries?"
date: 2015-09-09
forum: General Help
---

### Post by mateojonsonguynn on 2015-09-09
Hello,
I have recently noticed a message that seems to be causing me many problems- including preventing Soundcloud from working, preventing me from using SETI @ home, and breaking my Eclipse installation. The issue is this: Many of my libraries are missing or otherwise truncated. One library in particular that causes a lot of "truncated" errors is LibLLVM(something goes here).so.1.

My question is, why is this happening? Is there any way I can rebuild these libraries? Can I move libraries from a computer running Ubuntu 14.04 to my computer (which is running Ubuntu 14.10, by the way)?

I also get many other annoying errors that I believe to be caused by this, although most of them appear to be harmless. I believe this is definately a software issue, not hardware, because I didn't get any of these problems until I performed a system restore of a fresh install. (I know the restore file wasn't corrupt, either, because the computer had these same issues when I made the backup.) I am running Ubuntu 14.10 Desktop.

---

### Post by dino99 on 2015-09-10
you cant mix libs from a version to a different other one; otherwise you get conflicts and other troubles.

start cleaning your system, reconfigure it; and these issues might be resolved. Each non genuine installed package is the path for problems

---

### Post by mateojonsonguynn on 2015-09-23
Sorry for being a noob, but how do I reconfigure my system?

More recently, this issue has started to affect apt-get (its the same library.)

---

### Post by ian-weisser on 2015-09-23
dino99 is right - the most common reason for the types of errors you describe is the user downloading random libs from the dirty, dirty internet and manually installing them.

Please show us a complete output showing your input and all the errors, so we can determine if this is really your problem. Please [enclose the output in [code] tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168").

---

