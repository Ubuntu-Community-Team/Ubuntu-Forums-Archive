---
title: "Unusual Software Center Crash"
date: 2013-05-29
forum: General Help
---

### Post by Yarb on 2013-05-29
Hello! (this is my first post here, apologies if anything is out of line)

I have recently installed Ubuntu 13.04 (32-bit, I believe), and everything has been going great-- except for the Software Center.

Every time I run it (the Software Center) it works perfectly for perhaps... 10 seconds. Everything loads, and the page looks as expected. But after those 10 seconds my entire screen simply goes black. It eventually comes back, but I have been brought back to the log-in screen. This happens every time I run the Software Center-- although it sometimes lasts longer than 10 seconds (but never more than a minute. Just enough time to start a download, but never finish it). I can still download apps with the *sudo apt-get install *command, but I would very much like having access to the Software Center.

I have tried re-installing the Software Center (with *sudo apt-get install --reinstall software-center*) to no avail, and have no idea what else to try. (There isn't much information to be found about this particular problem)

Has anyone else experienced this? If so, have you been able to fix it? I'm willing to try anything. 

Thanks!

---

### Post by fantab on 2013-05-29
I am on Ubuntu Development Release, 13.10 and I experienced the same issue with Software Center. The crash has been reported. Keep updating your System regualrly and the fix will arrive soon.
I would like to suggest that you install and use **'Synaptic' Package Manager**  as an alternative. It far superior in my view.

```
sudo apt-get install synaptic
```

---

