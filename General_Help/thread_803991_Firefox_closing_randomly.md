---
title: "Firefox closing randomly"
date: 2008-05-22
forum: General Help
---

### Post by lakotajames on 2008-05-22
Firefox decides to randomly close. I upgraded to Hardy not to long ago, so that might have something to do with it. Could someone help? I read that totem had something to do with it. I already disabled it, but that didn't fix the problem.

---

### Post by Genius314 on 2008-05-22
Are you using Flash? The Flash plugin seems to have a bug that causes it to crash (but only when used... if you're not on a site that uses Flash when it happens, then it's something else)
I wish it were fixed, though. Firefox crashed twice on me on Youtube just a few minutes ago.

---

### Post by lakotajames on 2008-05-22
Nope. Not flash. It used to crash on flash, but  fixed it. Don't remember how, though. But it isn't crashing on sites with flash. And, if your crash was the same as mine with flash, then it got really slow, then stopped completely, and you had to force quit. 
This just closes instantly at random intervals.

---

### Post by jlacroix on 2008-05-22
This is the "Incredible Disappearing Firefox" bug that won't go away.

It is likely due to Flash. Even if you're not viewing a Flash video, sites still use Flash on banner ads and that's enough to cause it. I heard upgrading to Flash 10 Beta will fix it, but since that's beta, you'll likely have other problems.

This bug has been reported already, and they've been working on it for a long time. Sadly, I don't foresee it being fixed anytime soon, if ever. Personally I've had this problem since Ubuntu's inception on several machines. I haven't had this problem on any other distribution. Systems with onboard sound cards are the ones affected the most.

---

### Post by sizzam on 2008-05-27
I was having the same problem with Flash videos crashing Firefox.  There is an open bug ticket for this here:

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/192888](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/192888)


I corrected the problem for myself with steps gleaned from the bug ticket, details are in this post:

[http://ubuntuforums.org/showpost.php?p=5057137&postcount=5](http://ubuntuforums.org/showpost.php?p=5057137&postcount=5)

I have been crash-free since performing these steps.

---

