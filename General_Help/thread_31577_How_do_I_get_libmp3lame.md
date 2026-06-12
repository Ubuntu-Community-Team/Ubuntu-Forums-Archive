---
title: "How do I get libmp3lame ?"
date: 2005-05-03
forum: General Help
---

### Post by wwwolf on 2005-05-03
Is there an easy way of apt-get installing it? Or do I need to run alien on another distro's rpm?

Thanx,

wwwolf

---

### Post by wwwolf on 2005-05-04
Well, I found these two repositories:

deb [http://apt.cerkinfo.be/](http://apt.cerkinfo.be/) unstable main contrib non-free
deb-src [http://apt.cerkinfo.be/](http://apt.cerkinfo.be/) unstable main contrib non-free

and after running 'sudo apt-get update' I get the following:

Reading package lists... Done
W: GPG error: [http://apt.cerkinfo.be](http://apt.cerkinfo.be) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A35A4E6EF00175CA
W: You may want to run apt-get update to correct these problems

That's funny, running apt-get update tells me to run apt-get update. ](*,) 

anyway, I could now install the MP3lame libraries through Kynaptic but I got the warning:

WARNING: The following packages cannot be authenticated!
  lame
Install these packages without verification [y/N]? y
Get:1 [http://apt.cerkinfo.be](http://apt.cerkinfo.be) unstable/main lame 3.96.1-0.2 [389kB]
Fetched 389kB in 2m5s (3116B/s)

So, I hope I havn't totally fudged my system but the libraries seem to be working OK.   :) 

Thanks me,

wwwolf

p.s. Your welcome, self. ;)

---

### Post by ceti on 2005-05-24
Man, you saved my day.
Unfortunately, Audacity crashes everytime I try to change the bit-rate in Preferences.
Is it just me?
Thanks anyway

---

