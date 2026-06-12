---
title: "How do I use terminal to upgrade to 18.04.1 ? Update manager isn't working!"
date: 2018-12-22
forum: General Help
---

### Post by pretty_whistle on 2018-12-22
18.10 is already out but I want to upgrade to 18.04.1 so how do I use the terminal for this and not end up with 18.10??  Is there a way to specify 18.04.1??

The update manager is set to show me LTS, it does but it won't upgrade and don't know why so I'd like to use the terminal to upgrade to 18.04.1 if I can.

Thanks for any help.

---

### Post by pretty_whistle on 2018-12-22
I reinstalled update manager hoping it would upgrade then, it's working.  Thanks anyway!!!!

This solution works people if you have this issue.

---

### Post by Impavidus on 2018-12-23
If you set the upgrade manager to inform you about upgrades to LTS only, it will offer the upgrade from 14.04 to 16.04 or from 16.04 to 18.04. If you set it to any release, it will offer an upgrade to the next supported release. There are no upgrades to separate point releases (18.04, 18.04.1, 18.04.2 etc.). Those point releases only really apply to the live disk releases. If you install the regular updates, you get to the same point automatically. You didn't specify which release you were running.

---

### Post by pretty_whistle on 2018-12-23
> **Impavidus said:**
> If you set the upgrade manager to inform you about upgrades to LTS only, it will offer the upgrade from 14.04 to 16.04 or from 16.04 to 18.04. If you set it to any release, it will offer an upgrade to the next supported release. There are no upgrades to separate point releases (18.04, 18.04.1, 18.04.2 etc.). Those point releases only really apply to the live disk releases. If you install the regular updates, you get to the same point automatically. You didn't specify which release you were running.

I'm running 16.04.4.

---

### Post by pretty_whistle on 2018-12-23
Have you successfully upgraded to 18.04? If so, how did you do it? I haven't been able to do it and am wondering why.  It would help if you shared your experience with me so I can figure this out.

A history of my attempts:

> Tried to update to new kernel, 4.15.0-33, then upgraded to 18.04 from 16.04 - it wouldn't successfully boot.  (used terminal to update & upgrade)

Tried to update to new kernel, 4.15.0-36, then upgraded to 18.04 from 16.04 - it wouldn't successfully boot.  (used terminal to update & upgrade)

Tried to update to new kernel, 4.15.0-43, then upgraded to 18.04 from 16.04 - it wouldn't successfully boot (booted good 4 out of 10 tries).  (used update-manager to update & upgrade)

As you can see each attempt I make at upgrading fails with the same problem, won't boot.  Weird!!  The question I have is, what's going on?  Were you able to successfully upgrade, how did you do it then maybe I can do what you did.

Thanks for any help.

---

### Post by howefield on 2018-12-23
Threads merged.

---

### Post by pretty_whistle on 2018-12-23
I'll say they did.  Can you fix that? Sorry!

---

### Post by pretty_whistle on 2018-12-23
> **howefield said:**
> Threads merged.

First I thought you were saying the threads merged accidentally but now I think you mean the opposite.  Can you clarify?

---

### Post by howefield on 2018-12-23
> **pretty_whistle said:**
> First I thought you were saying the threads merged accidentally but now I think you mean the opposite.  Can you clarify?

Your second thread on the subject and therefore a duplicate, was merged into this one.

---

### Post by Impavidus on 2018-12-25
You lost me.

In post #1 you asked about upgrading to 18.04 while 18.10 was already released. I explained in post #3 that that would be no problem. In post #2 you wrote your issue was solved by reinstalling update manager. In post #5 you write that you tried multiple times to do a kernel upgrade followed by a release upgrade, making your computer unbootable. How? Did you restore the system from a backup? Because otherwise you can't attempt the same upgrade twice, in particular if your system doesn't boot after the first attempt. Did the computer boot between the kernel upgrade and the release upgrade? Anyway, a booting problem after upgrading is different from being unable to upgrade.

BTW, I upgraded from 17.10 to 18.04 back in June using upgrade manager. It worked without any problems (as usual).

---

### Post by gsahli on 2018-12-25
Confirm - Did you use:
sudo apt dist-upgrade
or 
sudo do-release-upgrade
?

---

### Post by pretty_whistle on 2018-12-28
> **gsahli said:**
> Confirm - Did you use:
sudo apt dist-upgrade
or 
sudo do-release-upgrade
?

Here's what I did, in this order:


sudo apt-get update


sudo apt-get upgrade


sudo apt-get dist-upgrade


sudo do-release-upgrade

---

### Post by pretty_whistle on 2018-12-28
> **Impavidus said:**
> You lost me.

In post #1 you asked about upgrading to 18.04 while 18.10 was already released. I explained in post #3 that that would be no problem. In post #2 you wrote your issue was solved by reinstalling update manager. In post #5 you write that you tried multiple times to do a kernel upgrade followed by a release upgrade, making your computer unbootable. How? Did you restore the system from a backup? Because otherwise you can't attempt the same upgrade twice, in particular if your system doesn't boot after the first attempt. Did the computer boot between the kernel upgrade and the release upgrade? Anyway, a booting problem after upgrading is different from being unable to upgrade.

BTW, I upgraded from 17.10 to 18.04 back in June using upgrade manager. It worked without any problems (as usual).

Sorry to be unclear.

Yes, I restored my system from a backup each time it wouldn't boot.
I had the booting issue after upgrading to 18.04.

Right now I'm waiting for the new kernel to come out and will try updating to it first (before upgrading).  If it goes well then I'll try the upgrade.  I'm wondering if the screen light simply went dark and that's what actually happened (I got that on Windows once) so I'll try that in case that's all it did.  Maybe it did because I did have my screen dimmed way down so perhaps it dimmed all the way when I upgraded.

---

### Post by Impavidus on 2018-12-29
So you get a black screen? Maybe your graphics don't like the new Ubuntu release. Although you already were on the 4.15 kernel. Can you boot into recovery mode?

After a failed release upgrade, I wouldn't restore from a backup and try to upgrade again. Chances are the same thing will go wrong again. I'd just try a fresh install. Have you tried 18.04 using a live disk?

---

### Post by pretty_whistle on 2018-12-29
> **Impavidus said:**
> So you get a black screen? Maybe your graphics don't like the new Ubuntu release. Although you already were on the 4.15 kernel. Can you boot into recovery mode?

After a failed release upgrade, I wouldn't restore from a backup and try to upgrade again. Chances are the same thing will go wrong again. I'd just try a fresh install. Have you tried 18.04 using a live disk?

Don't know if I could boot into recovery mode, I would have to try it next time I try upgrading again.

I did try a fresh install with a live disk and it happened again.

The problem occurs at the same point each time, right as it should reach the login screen it goes black.

Also noteworhty to mention is this:

I upgraded then restarted to test it.  It booted ok the first 4 times, then it went black.  That's weird to be able to boot 4 times ok. Very odd.

---

