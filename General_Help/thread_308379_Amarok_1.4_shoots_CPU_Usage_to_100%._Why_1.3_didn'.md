---
title: "Amarok 1.4 shoots CPU Usage to 100%. Why? 1.3 didn't."
date: 2006-11-28
forum: General Help
---

### Post by Roasted on 2006-11-28
Kind of upsetting, because I love Amarok since I have a few songs that are in wma format, but that didn't matter since Amarok played it all.

It's strange, because my system monitor doesn't show 100%. Yet if I hover the mouse over the icon I have in the lower taskbar, it shows "Processor Usage 100%" even if the blue bar is only idling around 20-30%. 

XMMS and VLC do not yield the same reactions at all. Amarok 1.3 did not yield this reaction either. How can I get 1.3 back? apt-get install amarok gives me 1.4. This blows. ](*,)

---

### Post by iamhugeinjapan on 2006-11-28
Do you mean Amarok 1.4.3 and 1.4.4 or 1.3?   1.3 is quite old now.

---

### Post by Roasted on 2006-11-28
I forget, I think it was 1.3 vs 1.4. 1.3 worked so nicely, too. That's why I used it. I had 1.4 at another time and it gave me the same trouble, but somehow I got back to 1.3 and kept it ever since. Then a recent system update changed it to 1.4 where it now sucks.

After making this thread I stopped caring, because I just set BEEP media player as my default since it plays mp3s and wmas. But out of the blue, all of the sudden, it's giving me an error for playing ANY song. It's pissing me off. ](*,)

edit - now all of the sudden beep works great. What the hell happened? Arg.

---

### Post by ntetreau on 2006-12-08
Hi,
If you are still interested in fixing the high CPU problem, amarok 1.4.4 seems to fix the issue for me. I upgrading to 1.4.4 using the link provided in drFUNK's post in another thread.

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

### Post by Roasted on 2006-12-08
Screw it.

I did what you said. It's still running at 100%.

Good thing I got VLC.

---

