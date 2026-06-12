---
title: "What's wrong with sleep and hibernate?"
date: 2007-01-14
forum: General Help
---

### Post by rekahsoft on 2007-01-14
Hi all, i have never been able to sleep or hibernate my laptop and was just wondering why this is?  I have also found that this is a very common issue...that sleep and hibernate are flaky. why? (I am a developer so if possible it would be nice if you could go into a little detail :))

---

### Post by TheFoe92 on 2007-07-12
I am having similar problem. I have never been able to use my Suspend and Hibernate options. I am using a Gateway 7330GZ laptop. I do not know why this happens. Any suggestions?

---

### Post by Al3xK3aton on 2007-07-12
Why don't you simply turn it off when you're not using it? That saves even more battery, and it only takes a little longer to boot up if you do this. Also, make sure you're not moving your mouse or typing on your keyboard or playing music or videos while you wait for sleep mode to kick in, it won't start if your computer is active.

---

### Post by malfist on 2007-07-12
On my desktop sleep/hibernate are there sometimes, sometimes not.

---

### Post by Erdaron on 2007-07-12
I know one issue that causes hibernate to not work properly is proprietary ATI graphics card drivers. The latest version of these drivers is supposed to have fixed this, but I haven't tried it.

Al3x: it's very nice to boot up and have all your programs in the same state as you had left them. I use hibernate all the time on my work computer because I can leave all the files open.

---

### Post by hardyn on 2007-07-12
> **Al3xK3aton said:**
> Why don't you simply turn it off when you're not using it? That saves even more battery, and it only takes a little longer to boot up if you do this. Also, make sure you're not moving your mouse or typing on your keyboard or playing music or videos while you wait for sleep mode to kick in, it won't start if your computer is active.

Thats not the point, it should work; its really inconvenient to to have a notebook that will not reliably suspend/hibernate, shutting down to walk across the hall is a big waste of time.

---

### Post by Sunflower1970 on 2007-07-12
> **TheFoe92 said:**
> I am having similar problem. I have never been able to use my Suspend and Hibernate options. I am using a Gateway 7330GZ laptop. I do not know why this happens. Any suggestions?

Have you tried, maybe, this? [http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/](http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/)

I just tried it out on a Thinkpad R40 with Feisty. To my amazement, it worked. It's not very pretty, but as long as I can suspend now, I'll live with this hack till until it can be fixed in the kernel.

---

### Post by sunspots on 2007-08-29
I have been testing Gutsy Gibbon Tribe-5 and found the sleep to work but not the hibernate. Actually, it hibernates but I can't revive the system from hibernation.

Have a look at the following bug report.
[https://bugs.launchpad.net/ubuntu/+bug/135088](https://bugs.launchpad.net/ubuntu/+bug/135088)

It would be good if you applied your comments to it. It is unlikely that it will be fixed on anything before Gutsy. I had similar comments on another problem I found, but they fixed it for Gutsy Tribe-5.

---

