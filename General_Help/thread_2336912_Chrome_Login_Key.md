---
title: "Chrome Login Key"
date: 2016-09-12
forum: General Help
---

### Post by sasafrass452 on 2016-09-12
I've been trying to make chrome work the way I want, but this has become VERY aggrivating. Everytime I boot up my computer & turn on chrome, I get a popup asking for a password, then still have to log into chrome afterward. I also get logged out of any website that I previously signed into. I tried setting up the sync passphrase in chrome, but to no avail. I then clicked on system settings-->online accounts, & set up my google account there which I thought did the trick, but when I rebooted again, the same popup appeared before I even turned on chrome. GRRR!!! How do I stop this from happening? How do I stay logged into the various websites I visit? I accepted the cookies, but even that didn't help. What do I do to make this work?

---

### Post by sasafrass452 on 2016-09-12
I think I fixed it!!! It seems all I had to do was turn off the auto-login for my ubuntu user account. Go figure.... Not the answer I was hoping for, but I can live with it. It's far too annoying to log into multiple sites every morning when I turn my computer on....

---

### Post by DuckHook on 2016-09-12
To understand what is going on here, you should understand the underlying security model of Ubuntu and how it at least *tries* to be a better security OS than the security joke that is Windows. Considered from a basic security perspective: when you choose auto-login, you are in essence choosing to bypass authentication. It then follows that any service requiring real security will not have been unlocked. Otherwise, why even bother to pretend that it constitutes security? The service that needs to be unlocked in order to auto-fill your passphrases, etc is accessed through an app called *seahorse* (you can find it among your apps). This service remains locked if you don't authenticate at login *and that's the way it should be*. If security operated any other way, it wouldn't be worthy of being called security; it would just be a bad joke.

Auto-login is one of the stupidest and most pernicious pseudo-features that Ubuntu has ever succumbed to. I suspect this was done to appease new users immigrating from Windows, but its effect is to enable and continue truly awful Windows habits and import them into Linux. There's no way to suger-coat this: it's a stupid, poisonous habit and the faster it is stamped out, the better.

While you may feel that enforced login authentication is inconvenient, it is actually the first step you are taking towards practising real security. If you want to learn more about real security, feel free to follow the link in my signature: Security Basics.

---

### Post by sasafrass452 on 2016-09-13
While I appreciate that auto-login may leave the system vulnerable, I'm the only person using this laptop, & I never take it out of the house. So, what's the harm? Having said that, I don't mind logging into the system when I boot up, but I can't stand logging into multiple websites every morning.... that's what cookies are for! It's just not worth the annoyance.... But before you rant about why we shouldn't allow cookies, I only keep the ones required to log into my various web accounts, then I set chrome to not allow any more. I agree that window$ is pathetically insecure.... someone always finds a loophole!



> **DuckHook said:**
> To understand what is going on here, you should understand the underlying security model of Ubuntu and how it at least *tries* to be a better security OS than the security joke that is Windows. Considered from a basic security perspective: when you choose auto-login, you are in essence choosing to bypass authentication. It then follows that any service requiring real security will not have been unlocked. Otherwise, why even bother to pretend that it constitutes security? The service that needs to be unlocked in order to auto-fill your passphrases, etc is accessed through an app called *seahorse* (you can find it among your apps). This service remains locked if you don't authenticate at login *and that's the way it should be*. If security operated any other way, it wouldn't be worthy of being called security; it would just be a bad joke.

Auto-login is one of the stupidest and most pernicious pseudo-features that Ubuntu has ever succumbed to. I suspect this was done to appease new users immigrating from Windows, but its effect is to enable and continue truly awful Windows habits and import them into Linux. There's no way to suger-coat this: it's a stupid, poisonous habit and the faster it is stamped out, the better.

While you may feel that enforced login authentication is inconvenient, it is actually the first step you are taking towards practising real security. If you want to learn more about real security, feel free to follow the link in my signature: Security Basics.

---

### Post by DuckHook on 2016-09-13
Apologies for the rant. I tend to go overboard when it comes to imported Windows habits. Using cookies for login IDs are acceptable (barely) but not for passwords. That would not constitute security at all. That's why they are kept under lock and key in seahorse. FF has a separate encrypted place it keeps passwords but I believe that it too must be unlocked with authentication. I could be wrong about that.

Linux is about freedom, so if you want to continue with auto-login try FF instead.

---

### Post by #&amp;thj^% on 2016-09-13
I'm not sure this was a rant...but rather making sure the OP is as safe as possible.
No harm in reminding one on safety. After all the choice is still yours at the end of the day.
Thanks for the input Duck Hook

---

### Post by sasafrass452 on 2016-09-13
I'm fine with my current configurations. Just as long as I don't have to type my username, password, & press "sign in" 6 times every morning.... I've used Firefox for years, but only just switched to chrome for a specific reason that I explain in another thread I posted a few days ago.

> **DuckHook said:**
> Apologies for the rant. I tend to go overboard when it comes to imported Windows habits. Using cookies for login IDs are acceptable (barely) but not for passwords. That would not constitute security at all. That's why they are kept under lock and key in seahorse. FF has a separate encrypted place it keeps passwords but I believe that it too must be unlocked with authentication. I could be wrong about that.

Linux is about freedom, so if you want to continue with auto-login try FF instead.

---

