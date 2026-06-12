---
title: "CPU at 100% w/amarok"
date: 2006-12-06
forum: General Help
---

### Post by DougieFresh4U on 2006-12-06
Hi Every One! :p  While using amarok only, CPU jumps to 100%.Using other music players it doesn't happen.Please don't say "Well don't use amarok" as I happen to think amarok is about the best Ubuntu offers. Not many of the players have 'Equalizer'. Another question, I have inquired before about, what is up with the 'Master' volume switch not working? The 'Headphone' and 'PCM' switches control the volumes, but the 'Master' switch in the top right corner has absolute no function

---

### Post by drFUNK on 2006-12-06
Have you tried version 1.4.4?
[http://kubuntu.org/announcements/amarok-1.4.4.php](http://kubuntu.org/announcements/amarok-1.4.4.php)

---

### Post by DougieFresh4U on 2006-12-06
I must check that as I have 1.4.3. Thanks! Question, your link says Kubuntu and I have Ubuntu so how would I manage upgrading my amarok or should I un-install and re-install? Any suggestions on that alsa issue? I have read numerous threads on same problem I am having with sound and I have tried many of the solutions offered, but nada solved my issue.

---

### Post by ntetreau on 2006-12-08
Hi guys,
I had the same problem as you and I fixed it my upgrading to 1.4.4 using the link provided in drFUNK's post.

For those newbies affected by this problem, just add the kubuntu amarok repository to your /etc/apt/sources.list:

sudo gedit /etc/apt/sources.list

Add:

deb [http://kubuntu.org/packages/amarok-144](http://kubuntu.org/packages/amarok-144) edgy main

then

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install amarok

For some reason though, amarok would not start after install and I had to delete my tune database this way:

rm ~/.kde/share/apps/amarok/collection.db

Now my cpu stays cool when I'm playing my tunes with amarok!

Good luck!

Nic

---

