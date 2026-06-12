---
title: "Slow graphics since upgrading to 14.10"
date: 2015-01-05
forum: General Help
---

### Post by guscavge on 2015-01-05
I upgraded my machine from 14.04 to 14.10 over the weekend. I have had no issues apart from one which is pretty major from my point of view. The graphics are working horribly ever since the upgrade. I can watch Youtube videos all right but as soon as I make them full screen they become choppy. Playing videos (on VLC) is equally choppy no matter what, to the extent where they're unwatchable.

I see that a similar issue [has been raised by other posters]("http://ubuntuforums.org/showthread.php?t=2249797&highlight=graphics+14.10") but there are no definitive answers. Can anyone help? My graphics card is NVidia GeForce GT 540M

---

### Post by ibjsb4 on 2015-02-02
What video driver are you running?

---

### Post by guscavge on 2015-02-02
> **ibjsb4 said:**
> What video driver are you running?

X.Org X server - Nouveau display driver from xserver-xorg-video-nouveau

The 'Additional Drivers' tab on Software & Updates suggests a few NVIDIA binary / legacy binary drivers but I struggle to know which one would be best

---

### Post by ibjsb4 on 2015-02-02
The 331 driver works for me.  Maybe worth a try.

---

### Post by guscavge on 2015-02-02
> **ibjsb4 said:**
> The 331 driver works for me.  Maybe worth a try.

I'll give it a try, thanks.

I see two different 331 drivers: one is open source, one is proprietary. In your experience, is there any practical difference between those?

---

### Post by ibjsb4 on 2015-02-02
I run the proprietary driver.  I did not know there was a open source driver.  Could it be not open source, but source code?

---

### Post by guscavge on 2015-02-02
No, it does say open source. Only difference is that the proprietary one is 331-updates, whereas the open source one is just 331. I'll try with the proprietary one and see how it goes. Thanks again!

---

### Post by Tar_Ni on 2015-02-02
I had a graphic issue in both Lubuntu and Xubuntu 14.10, in my case it was the splashboot screen who did not show up at all. My graphic card is an NVIDIA Geforce as well. Here's the topic: [http://ubuntuforums.org/showthread.php?t=2263521](http://ubuntuforums.org/showthread.php?t=2263521) In my case, installing the non-legacy, NVIDIA proprietary driver did not help.

My suggestion would be to fall back on 14.04.1 LTS by doing a clean installation. There seems to be a kernel issue with some NVIDIA graphic cards in 14.10. It's just not worth the trouble for a short-term release and one can only hope that this will be fixed in 15.04 (to be expected in April.)

From now on I've made the decision to stick only to the LTS releases.. More stability and less issues.

---

### Post by guscavge on 2015-02-02
> **Tar_Ni said:**
> I had a graphic issue in both Lubuntu and Xubuntu 14.10, in my case it was the splashboot screen who did not show up at all. My graphic card is an NVIDIA Geforce as well. Here's the topic: [http://ubuntuforums.org/showthread.php?t=2263521](http://ubuntuforums.org/showthread.php?t=2263521) In my case, installing the non-legacy, NVIDIA proprietary driver did not help.

My suggestion would be to fall back on 14.04.1 LTS by doing a clean installation. There seems to be a kernel issue with some NVIDIA graphic cards in 14.10. It's just not worth the trouble for a short-term release and one can only hope that this will be fixed in 15.04 (to be expected in April.)

From now on I've made the decision to stick to the LTS releases.. More stability and less issues.

I have considered going back to 14.04, but downgrading is so much more time-consuming than upgrading so I decided against it.

I did what **ibjsb4** helpfully suggested and it's now working like a charm. Full screen videos play smoothly, no over-heating, just what I was looking for. I think some damage may have been done to the splash boot (it looks very small and ugly for a few seconds, then goes back to normal) but I can live with it

---

### Post by ibjsb4 on 2015-02-02
Congratulations :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

