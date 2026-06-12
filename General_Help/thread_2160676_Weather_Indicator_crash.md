---
title: "Weather Indicator crash"
date: 2013-07-07
forum: General Help
---

### Post by laspen on 2013-07-07
Hello
I'm running Ubuntu 12.04 LTS and installed the Weather Indicator, but every time I try to set it up, it crashes. Is there any ways to fix this?

---

### Post by Cheesehead on 2013-07-07
If I recall correctly, the answer is "No, not yet"
See the bug report at [https://bugs.launchpad.net/weather-indicator/+bug/1162485](https://bugs.launchpad.net/weather-indicator/+bug/1162485)

The most common Weather Indicator setup crash is caused by a change in the Yahoo location service.
The original Weather Indicator developers lost interest in the project, and it took until May for a new volunteer to take over.
He has fixed the problem, and the fix is in the latest pre-release version of Ubuntu (13.10)

What you can do:
Request an SRU, to get the fixed version into the 12.04 repositories. See [https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)
If the SRU is declined, then help backport the package. See [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

---

### Post by efflandt on 2013-07-07
The thing is indicator-weather still works in 10.04 (on my old PC) and works on a system that was 11.10 upgraded to 12.04. It is just the version provided in 12.04 (and maybe 12.10?) that has never worked reliably. So I was thinking there must be some other problem than any changes to the Yahoo location service.  Although, I have not run from that drive with 11.10 > 12.04 long enough to tell if it eventually fails like it used to do (it used to work initially in 12.04 and then fail after a time). But on a 12.04.2 system installed from scratch to replace a system on a failing drive, I cannot even add a location to the weather indicator. But maybe that is the issue now with the Yahoo location service, existing locations work, but new locations cannot be added (even if you chose Google instead of Yahoo).

---

### Post by Iowan on 2013-07-07
[This]("http://ubuntuforums.org/showthread.php?t=2152638") one worked for me. Curiously, though, an update made it "go away". I managed to reload it again... currently working.

---

### Post by papibe on 2013-07-07
Hi laspen.

As stated before, the one available on the repositories does not work. I upgraded using a ppa from the development team, and I got it working on 12.04:
```
sudo add-apt-repository ppa:weather-indicator-team/ppa
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install indicator-weather
```
It seems to crash anyway right after the install, but after a reboot it works (old python dependencies running in the background?)

Regards.

---

### Post by laspen on 2013-07-08
Hi
Thanks for the replies.
I went ahead and installed different weather indicator -app, imaginatively named as "My Weather Indicator" by following tutorial found in [http://handytutorial.com/install-my-weather-indicator-in-ubuntu-12-10-12-04/](http://handytutorial.com/install-my-weather-indicator-in-ubuntu-12-10-12-04/) 
It works well.

---

### Post by Mr.Dunham on 2013-09-21
> **papibe said:**
> 
As stated before, the one available on the repositories does not work. I upgraded using a ppa from the development team, and I got it working on 12.04:
```
sudo add-apt-repository ppa:weather-indicator-team/ppa
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install indicator-weather
```
It seems to crash anyway right after the install, but after a reboot it works (old python dependencies running in the background?)


Thank you very much, that helped me. I didn't want a different one, I just wanted this one to work and found this topic and could fix it. I think I got it to work after a log out /log back in.

---

