---
title: "Any way to use the snap-based Chromium browser inside a network namespace?"
date: 2020-07-18
forum: General Help
---

### Post by iexpectspam on 2020-07-18
Since Chromium is snap-based now, and, at least with the default configuration, snaps [don't work inside network namespaces]("https://forum.snapcraft.io/t/cannot-run-snaps-apps-inside-a-custom-netns-or-a-tmux-session/17501"), is there any way to run Chromium on Ubuntu when using a network namespace?

I was previously able to run Chromium in my network namespaces without issue, but the snap switch to snaps has made it impossible. I'm assuming there must be some work-around.

Or is the work-around just to install a Chromium PPA or use Firefox instead?

---

### Post by ajgreeny on 2020-07-18
I've been using the PPA for chromium dev version from [https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev](https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev) in 20.04 partly because I prefer not to use snaps, and also as a test for the purpose of discussing chromium in  more detail in this forum and it is working absolutely fine for me.
There is also a beta version PPA at [https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-beta](https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-beta) which I've also used without problem.

I presume either of these two would give you the ability to run them how you want to, but I can't be sure of that as I have never needed such use.

I have not bothered to add the Google APIs that are missing from this version (85.0.4173.0-0ubuntu1~ppa3~20.04.1) as I personally don't need what they would offer.

---

### Post by iexpectspam on 2020-07-18
Thanks!

I ended up just going the PPA route as well.

And, on another note, I just can't help but mention that the move to snap seems like a strange choice for such a major package as Chromium, especially considering it makes the package not work with one of the Linux kernel's major features (network namespaces).

Anyway, thanks again!

---

