---
title: "ubuntu 18.04 hangs up after updating"
date: 2018-07-02
forum: General Help
---

### Post by s9032g@comcast.net on 2018-07-02
Today July 2 I ran updates. After installing I was asked to restart and did so. Now I am hung up. There are many entries. The last ones involve starting authorization mgr; start LSB automatic crash report; started Gnome display mgr . Dispatcher service....before the ppp link was shut down

I cannot copy all this and send it as I can't login to ubuntu.

Tried shutting down. holding shift while starting, holding ctrl, alt, etc. Still stuck.

---

### Post by rattskjelke on 2018-07-02
Youre not the only one with this problem.
I posted this in the Installation & Upgrades section. [https://ubuntuforums.org/showthread.php?t=2395452](https://ubuntuforums.org/showthread.php?t=2395452)
Wait about 10 minutes and see if you get the login screen.

---

### Post by s9032g@comcast.net on 2018-07-02
Various suggestions about running commands, deleting snap,  etc don't help when I can't even boot up. Just wait and hope for now.

---

### Post by rattskjelke on 2018-07-02
Another thread suggested moving the mouse while booting.
I can confirm that on my laptop moving the mouse or touchpad around while booting fixed (or hid) the problem.

---

### Post by s9032g@comcast.net on 2018-07-03
Indeed doing this does get around the problem, but it does not solve the problem as I have to repeat the action every time I login.
Ran Synaptic update and repair errors. Did not help.
I have confidence that a fix will happen. Thanks

---

### Post by s9032g@comcast.net on 2018-07-03
Now that I am able to login I installed "boot repair". Found commands with Google search. Now everything is fine without mouse or trackpad. Normal again.

---

### Post by bodhin2 on 2018-07-03
so can you explain?  everything?  and where you got boot repair?  hate to mess up my new redid system again.  I'd throw the laptop in the garbage at that point.

---

### Post by monkeybrain20122 on 2018-07-04
Same issue here. Now just use kernel 4.15.0.23

---

### Post by monkeybrain20122 on 2018-07-04
> **rattskjelke said:**
> Another thread suggested moving the mouse while booting.
I can confirm that on my laptop moving the mouse or touchpad around while booting fixed (or hid) the problem.

I can confirm that this works on my laptop too.

It seems to be [this bug]("https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=897572") esp see #42 and #47 for the workaround by moving the mouse or touchpad. So this might affect all kernels >= 4.15.0-24. I have tried 4.16.18 from mainline and 4.17.4 (self compiled) exhibit for same problem, so 4.15.0-23 is the only good kernel here.

On the other hand, my 16.04 machine also got updated to 4.15.0-24  but no problem there, only the 18.04 machine is affected.

---

### Post by rattskjelke on 2018-07-04
Also holding the shift key while booting works.

---

### Post by chasb2 on 2018-07-04
> **rattskjelke said:**
> Also holding the shift key while booting works.

Thanks!  Not able to get any cursor activity with mouse or touchpad until hanging for a few minutes, and nothing from keyboarding the usual CTRL+ALT F1, F7 combos.
But the held SHIFT during boot is successful as a workaround.  The splash screen is dismissed within 10 seconds now.

---

### Post by s9032g@comcast.net on 2018-07-04
Heres how to get boot repair: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Holding shift was the first thing I tried. Didn't work for me.

---

### Post by monkeybrain20122 on 2018-07-04
> **s9032g@comcast.net said:**
> Heres how to get boot repair: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Holding shift was the first thing I tried. Didn't work for me.

Nothing to repair, it is a bug.

---

### Post by apeitheo2 on 2018-07-04
```
sudo apt install haveged
sudo systemctl enable haveged
```
This issue only seems to affect kernel 4.15.0-24. getrandom() is called when starting Xorg and for some reason in 4.15.0-24, it hangs for a bit until the entropy is high enough to generate a random number to use as a magic cookie for xauth. Xorg, LightDM, and GDM won't start until xauth is given a random number to use. Any kind of mouse/keyboard input probably raises entropy, which explains why pressing keys or moving the mouse fixes the problem. Haveged generates enough entropy at boot, eliminating the problem.

It's been reported as a bug, so hopefully haveged won't be necessary in future kernels once the bug is fixed.

The previous 4.15.0-23 kernel doesn't have this problem, so booting into that instead would also work.

---

### Post by chasb2 on 2018-07-05
> **apeitheo2 said:**
> 

It's been reported as a bug [...]


That bug is here
[https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1779476](https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1779476)


Thanks for reporting the haveged workaround here.  Saves having to hover over the booting machine hitting keys like a madman.

---

### Post by bodhin2 on 2018-07-05
many thanks to whoever came up with this workaround.  seemed to work on my office laptop!  many, many thanks - for the fix and the additional 33,000 gray hairs.  oh and 200 more wrinkles.  heh Heh!

---

### Post by mc4man on 2018-07-05
Another workaround may be to just remove splash from the grub commandline (i.e the GRUB_CMDLINE_LINUX_DEFAULT=  line, quiet could also be removed if one wanted to see something..) 
Can't test here as I'm not affected by this at all in 18.04, why, no clue. Maybe it's because I have a  ssd, by default the splash only shows for a 1/4 sec or so.

---

### Post by apeitheo2 on 2018-07-05
> **mc4man said:**
> Another workaround may be to just remove splash from the grub commandline (i.e the GRUB_CMDLINE_LINUX_DEFAULT=  line, quiet could also be removed if one wanted to see something..) 
Can't test here as I'm not affected by this at all in 18.04, why, no clue. Maybe it's because I have a  ssd, by default the splash only shows for a 1/4 sec or so.
4.15.0-24 still hangs without GRUB_CMDLINE_LINUX_DEFAULT set to splash and quiet.

---

### Post by bodhin2 on 2018-07-05
mu affected machine has the ssd HD.  go figure.

---

### Post by monkeybrain20122 on 2018-07-05
> **mc4man said:**
> Another workaround may be to just remove splash from the grub commandline (i.e the GRUB_CMDLINE_LINUX_DEFAULT=  line, quiet could also be removed if one wanted to see something..) 
Can't test here as I'm not affected by this at all in 18.04, why, no clue. Maybe it's because I have a  ssd, by default the splash only shows for a 1/4 sec or so.

I have a ssd but am affected. But my other machine with 16.04 is not affected even though HWE updated to same kernel. That one has a Nvidia gpu ..

---

### Post by apeitheo2 on 2018-07-05
According to [https://bugs.launchpad.net/ubuntu/+bug/1779827](https://bugs.launchpad.net/ubuntu/+bug/1779827) a fix has been committed and now we're just waiting for it to be released.

---

### Post by bodhin2 on 2018-07-05
as stated in my thread - the newer faster z series has ssd and sandybridge chip. that was affected.  the other older clower x series and my wife's dell inspiron has ironlake chips and so far no problem.  maybe a connection to chipset there?

---

### Post by monkeybrain20122 on 2018-07-05
> **bodhin2 said:**
> as stated in my thread - the newer faster z series has ssd and sandybridge chip. that was affected.  the other older clower x series and my wife's dell inspiron has ironlake chips and so far no problem.  maybe a connection to chipset there?

Here 
ivybridge + 18.04 + kernel 4.15.0-24 = affected, 
kabylake + 16.04 + kernel 4.15.0-24 + nvidia = not affected.

---

### Post by denny-mello on 2018-07-07
> **apeitheo2 said:**
> ```
sudo apt install haveged
sudo systemctl enable haveged
```
This issue only seems to affect kernel 4.15.0-24. getrandom() is called when starting Xorg and for some reason in 4.15.0-24, it hangs for a bit until the entropy is high enough to generate a random number to use as a magic cookie for xauth. Xorg, LightDM, and GDM won't start until xauth is given a random number to use. Any kind of mouse/keyboard input probably raises entropy, which explains why pressing keys or moving the mouse fixes the problem. Haveged generates enough entropy at boot, eliminating the problem.

It's been reported as a bug, so hopefully haveged won't be necessary in future kernels once the bug is fixed.

The previous 4.15.0-23 kernel doesn't have this problem, so booting into that instead would also work.

This workaround works for my desktop too! thank you kindly.

---

### Post by Cavsfan on 2018-07-07
Also unaffected here with 18.04 installed UEFI on an SSD. Super fast reboot, super fast boot to login screen.
```
cavsfan@cavsfan-Bionic:~$ uname -r
4.15.0-23-generic

```

Oddly I do not have [COLOR=#000000]4.15.0-24 [/COLOR] on my system and it is up to date.

---

### Post by s9032g@comcast.net on 2018-07-08
Mine went bad again after doing boot repair. I ended up using "parted magic" to clean out my ssd, then did a clean install. Not that bad to do with backups.

---

### Post by apeitheo2 on 2018-07-20
If haveged worked for you, I have good news! :D

A fixed kernel (4.15.0-29) was just released and it fixes the entropy problem! I uninstalled haveged and rebooted with the new kernel, and it works! You can leave haveged installed, but once you've upgraded to the latest kernel, it isn't needed any longer.

Reference: [https://bugs.launchpad.net/ubuntu/+bug/1779827/comments/101](https://bugs.launchpad.net/ubuntu/+bug/1779827/comments/101)

---

### Post by bodhin2 on 2018-07-20
Thank you!

---

### Post by pjberry on 2018-10-19
> **s9032g@comcast.net said:**
> Today July 2 I ran updates. After installing I was asked to restart and did so. Now I am hung up. There are many entries. The last ones involve starting authorization mgr; start LSB automatic crash report; started Gnome display mgr . Dispatcher service....before the ppp link was shut down

I cannot copy all this and send it as I can't login to ubuntu.

Tried shutting down. holding shift while starting, holding ctrl, alt, etc. Still stuck.

[Solved without any patch] There is a very simple solution to this hanging problem, which I applied, and it seems valid, initially I tried to make partitions and tried, it hung, Later I deleted all partitions and alongside window, allowed live CD to do it itself and yes it started very well without hanging and beautiful with good speed. Thanks

---

### Post by jeanloup on 2019-09-27
I'm on 4.15.0-65 and whatever is causing this issue has not been solved at all. I've had this problem for months and no kernel update has managed to resolve this once and for all. I have tried to install haveged but turning the machine back on showed this did not help at all. I'm on an AMD Bonaire GPU, I've no idea if that's supposed to make it worse but I don't recall doing anything to my setup to trigger this issue (eg. creating partitions, or messing with the boot sector).

Frankly I'm at a loss what to do about this :/

---

### Post by uRock on 2019-09-27
> **jeanloup said:**
> I'm on 4.15.0-65 and whatever is causing this issue has not been solved at all. I've had this problem for months and no kernel update has managed to resolve this once and for all. I have tried to install haveged but turning the machine back on showed this did not help at all. I'm on an AMD Bonaire GPU, I've no idea if that's supposed to make it worse but I don't recall doing anything to my setup to trigger this issue (eg. creating partitions, or messing with the boot sector).

Frankly I'm at a loss what to do about this :/

Your best bet would be to start a new thread and include as much information as possible, such as the output of the following command, which will show us your current hardware configuration.
```
lspci
```

---

### Post by wildmanne39 on 2019-09-27
Hi jeanloup, please start your own thread so you can get the help you need instead of posting in an old solved thread, most likely your issue is not exactly the same as the OP of this thread.

Thread closed!

---

