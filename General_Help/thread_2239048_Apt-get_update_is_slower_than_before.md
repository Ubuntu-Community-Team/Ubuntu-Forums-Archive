---
title: "Apt-get update is slower than before?"
date: 2014-08-11
forum: General Help
---

### Post by crazygoose92 on 2014-08-11
I've been using the 'sudo apt-get update' for ages but for some reason it takes *significantly* longer than it has in the past - usually hanging up around 95%-100% [Waiting for Headers] and then taking up to 5 minutes to finish. I have tried to improve speed by switching to "best server" and have went through multiple suggested solutions. Can anyone help?&#8203;

---

### Post by Impavidus on 2014-08-11
Have you added any PPAs? They might be slow and are not changed when you change the server for the normal repositories.

---

### Post by ian-weisser on 2014-08-11
Could be the mirror you are using.
Could be network congestion or an ISP issue.

My apt-get update works as speedy as ever today.
So I doubt it's an issue with your Ubuntu system.

---

### Post by crazygoose92 on 2014-08-11
I know it is not an issue with my ISP or network, though I'm not sure about the mirror - there is no prefix to any listed archive.ubuntu.com links. Also, when I noted this there hadn't been any PPAs added prior, I believe I can rule that out.

---

### Post by ian-weisser on 2014-08-11
> **crazygoose92 said:**
> there is no prefix to any listed archive.ubuntu.com links.

Try a mirror that is topologically close to you.

You can select a different mirror using the *software-properties-gtk* application. 
Access that application from Software Center (menu item: Software Sources) or Synaptic or the command line (software-properties-gtk).
It even has a nifty little feature that tries different mirrors and selects the fastest for you.

---

### Post by crazygoose92 on 2014-08-12
I gave that a try but it was no better, none of my nearby mirrors seem to help. I'll keep testing them but so far nothing works better. It usually hangs up on '*Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en*'

---

### Post by crazygoose92 on 2014-08-12
ok, for some reason there is no longer a problem - it just started working, randomly, no restart, no adding or removing of packages. Not quite sure why but I''ll guess changing the mirror took some additional time to work, though it was connected.

---

### Post by ian-weisser on 2014-08-12
Boo for mysterious slowdowns.
Hooray for mysterious speedups.

---

### Post by Impavidus on 2014-08-13
I think it was a temporary problem with a PPA server, nothing to do with your computer. Anyway, good that is has been solved.

---

