---
title: "Distro with alternative to Pulseaudio?"
date: 2014-06-13
forum: General Help
---

### Post by jimford on 2014-06-13
In the 10 to 15 years I've been using Ubuntu/Xubuntu on various machines, I can't say I've had sound using Pulseaudio working reliably on any of the installations. More recently I
it's also reluctant to communicate with any bluetooth devices I've tried.

I've carried out each upgrade, hoping that sound would be fixed, but 14.04 is still not working properly.

I'm now considering looking for a distro that doesn't use Pulseaudio as a sound server, and would welcome any suggestions.

Jim

---

### Post by mörgæs on 2014-06-13
Lubuntu.

---

### Post by jimford on 2014-06-13
> **mörgæs said:**
> Lubuntu.

Won't Lubuntu still have the wretched Pulseaudio sound server, that I want to get away from?

Jim

---

### Post by Bucky Ball on 2014-06-13
Perhaps this:

[http://www.hecticgeek.com/2012/01/how-to-remove-pulseaudio-use-alsa-ubuntu-linux/](http://www.hecticgeek.com/2012/01/how-to-remove-pulseaudio-use-alsa-ubuntu-linux/)

---

### Post by whatthefunk on 2014-06-13
What problems are you having specifically?

I used to have problems with it and I simply deleted it.  Worked like a charm.  Since then, I have found a solution to my problems and now use pulse without problem.

---

### Post by prj44 on 2014-06-14
Please point to a solution.  I cannot get any sound out of 14.4 and my goodwill towards Ubuntu is disappearing.

---

### Post by anakai on 2014-06-14
Why don't you just uninstall pulse and use alsa? I don't use pulse myself

---

### Post by Bucky Ball on 2014-06-14
There are solutions in posts#2 and #4. You missed them?

---

### Post by 3rdalbum on 2014-06-14
> **jimford said:**
> In the 10 to 15 years I've been using Ubuntu/Xubuntu on various machines, I can't say I've had sound using Pulseaudio working reliably on any of the installations.

Amazing that you've been having problems with Pulseaudio for the last 15 years. It's only been around since 2008. Ubuntu has only been around since 2004.

You say you have "problems" - what actually are the problems you've been having? Pulseaudio has been working well for most people for years. Depending on your problem, the solution might be a lot simpler than finding a different distro. It might not even be a Pulseaudio problem, but a driver issue.

> Please point to a solution. I cannot get any sound out of 14.4 and my goodwill towards Ubuntu is disappearing. 

PRJ, please post your problem in a different thread. If you have no sound, it's most likely a missing driver, so you need to tell us what sound card you have.

---

### Post by robin7 on 2014-06-14
Unless you're using an application that *requires* Pulseaudio (like Skype does I think), just remove it and use good ol' time-tested Alsa in its place. But if you really want some help, include some system specs in your original post.

---

### Post by jimford on 2014-06-14
> **3rdalbum said:**
> Amazing that you've been having problems with Pulseaudio for the last 15 years. It's only been around since 2008. Ubuntu has only been around since 2004.

My Linux experience goes back to the 0.9 kernel (or was it 0.95?) on Slackware in the 90s, so my memory is a bit hazy when I changed over!

I've googled around and it seems I'm not the only one with Pulseaudio problems. The 'solution' appears to be to consign it to the bit bucket, which I shall shortly do so.

Thanks for the replies.

Jim

---

