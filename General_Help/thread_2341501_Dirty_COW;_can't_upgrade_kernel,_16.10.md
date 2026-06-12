---
title: "Dirty COW; can't upgrade kernel, 16.10"
date: 2016-10-28
forum: General Help
---

### Post by Jason_Hunter on 2016-10-28
If I do uname -r

4.8.0-15-generic

I then do apt-get update && apt-get upgrade, but I don't get any updates. 

Reading this: 

[http://www.lifehacker.com.au/2016/10/how-to-protect-linux-servers-and-android-phones-against-dirty-cow-security-bug/](http://www.lifehacker.com.au/2016/10/how-to-protect-linux-servers-and-android-phones-against-dirty-cow-security-bug/)

, I should be getting:


[LIST]
[*]4.8.0-26.28 for Ubuntu 16.10
[/LIST]
Any clue why I dont' get any updates?

---

### Post by Jason_Hunter on 2016-10-28
I've also done apt-get dist-upgrade, btw, and still nothing

---

### Post by Jason_Hunter on 2016-10-28
ok, my fault;)

I've gotten the update before and I have not rebooted; it was in /boot;)

Sorry for the noise.

---

