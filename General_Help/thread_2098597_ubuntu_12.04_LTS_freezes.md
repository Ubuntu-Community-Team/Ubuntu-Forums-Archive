---
title: "ubuntu 12.04 LTS freezes"
date: 2012-12-27
forum: General Help
---

### Post by klemenl on 2012-12-27
Hello,
I have installed 12.04 LTS ubuntu version on a new hp probook 4740s machine (i5, 6GB ram, radeon) and it randomly and often freezes. I installed updates but it did not help. By factory installation it was SuSE 11 Enterprise Desktop and it worked without freezing.

What happens? The system stops responding. The picture is there, but mouse does not move, the keyboard has no effect (not even ctrl+alt+del), the only thing that does make an effect is the power button. When I turn the box on again it works as nothing happened (until next random freeze.) I worked with unix systems like Solaris and HP-UX time ago and switching off system like this was not a good thing to do. I'm surprised my system comes back as nothing happened.

I ask for your help to fix the issue.

Thank you in advance! K.

---

### Post by jopeto on 2012-12-27
I had a similar problem as you:

[http://ubuntuforums.org/showthread.php?t=2057665](http://ubuntuforums.org/showthread.php?t=2057665)

I was guessing that the problem was with the desktop environment, since I was not having that problem when using a simple window manager such as FVWM. Unfortunately no one replied to my question and a forum administrator suggested the following to me in a private message after sometime:

> Why don't you try - getting all the information you can together into one post and start a new thread, report the old one and ask for it to be closed.

 You can get the system log - 
```
cat /var/log/syslog
```
When you get a crash try this in a terminal
```
dmesg | tail
```
I'd check dmesg for errors as well - possibly the xorg log - you'll find them all in /var/log

However, this was a machine that I don't use often, so I didn't have time or incentive to persevere. In the end I upgraded to Ubuntu 12.10 and since then I haven't had a problem.

---

### Post by david stevenson on 2012-12-27
Well it is a problem for me.
I have just upgraded from 10.04 LTS to 12.04 LTS as this is my main desktop and I like it stable. And it is not!
If 12.10 has fixed the problem why is the LTS still buggy.

For the record I get short pause type freezes every day, or several times some days. Just wait 20secs plus and it recovers. And every few days I get a total screen freeze, I can still ssh in but can see nothing in log or dmesg. Killing compiz clears the screen.

I have seen posts recommending later kernels, but also posts saying it does not help.
Hardware
Processor IntelÂ® Coreâ„¢2 Duo CPU P7550 @ 2.26GHz Ã— 2
Graphics unknown   -- according to System Settings -> Details
but 10.04 knew it is a Nvidia GeForce 9400

3.2.0-35-generic #55-Ubuntu SMP Wed Dec 5 17:42:16 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

David

---

### Post by jopeto on 2012-12-28
Yes, I agree it is annoying. I'm surprised the Ubuntu developers haven't picked up on it since it seems like it is a problem for quite a few people.

---

### Post by audiomick on 2012-12-28
> **david stevenson said:**
> ...
Graphics unknown   -- according to System Settings -> Details
but 10.04 knew it is a Nvidia GeForce 9400


What does 
```
sudo lshw -C video
```
tell you? That should show the exact type of the video card.

I think what you describe could be a problem with the graphics driver, particularly when you say the system does not now know what video card it has and did previously. I don't think I will be able to help you sort this out completely, but post the output that you get from that command for a start.

---

### Post by abrianb on 2012-12-28
Please subscribe to  Bug #993187
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/993187](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/993187)

---

