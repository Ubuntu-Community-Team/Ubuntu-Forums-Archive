---
title: "Closing the lid suspends the computer even if it's shuting down!"
date: 2014-01-08
forum: General Help
---

### Post by ehsanoo on 2014-01-08
I normally press the power button on my laptop, choose the shutdown option and immediately close the laptop's lid and go away. Next time that I come to my laptop, I see it wakes up and continue the shutdown process and turns off.

The problem is that it goes to sleep when I close the lid because it's still not turned off.

I know it's wrong, I should wait for the computer to fully shutdown, but there is a question, why ubuntu suspends the computer even when I'm shuting it down? Ubuntu already knows that my computer is going to be turned off in 5 seconds(It's killing open applications, etc.) so I think Ubuntu should ignore such events(lid switch and similar, I mean) then, right?

As I'm a serious fan of Ubuntu, and I already know that it's not an issue, I'm not saying it's Ubuntu's fault or a problem at all. But I'm really interestead in knowing if it's possible to tell Ubuntu not to go to sleep when the user wants to shut down.

Of course I suspend my laptop with closing the lid a lot of times in a day, so I do not want to turn this great feature off.

---

### Post by ian-weisser on 2014-01-08
This has been reported, and may be due to several bugs (at least one of which was fixed).
You can help diagnose the specific issue you are suffering from and add yourself to that bug report.

[https://bugs.launchpad.net/ubuntu/+source/systemd-shim/+bug/1211514](https://bugs.launchpad.net/ubuntu/+source/systemd-shim/+bug/1211514)
[https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/1245956](https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/1245956)
Likely to be other relevant bug reports if you poke around a bit.

---

### Post by mc4man on 2014-01-08
If you're on 13.10 (saucy) make sure you have systemd-shim (6-0ubuntu0.13.10
```
apt-cache policy systemd-shim
```

---

### Post by ehsanoo on 2014-01-10
Thank you both for your replay. I didn't know that it's a known bug. I had systemd-shim version 3+real-0ubuntu1 installed which I now have upgraded to 6-0ubuntu0.13.10 after reinstalling both systemd-shim and pm-utils.

Since this problem was not happening all the time, I need a little time to see if it's solved or not. I will be back and mark the thread as solved later if the problem is gone.

And for those who have the same problem, systemd-shim package .deb files can be found on [launchpad]("https://launchpad.net/ubuntu/+source/systemd-shim") and you can install them using the following command:

```
dpkg -i FILE.deb
```

---

