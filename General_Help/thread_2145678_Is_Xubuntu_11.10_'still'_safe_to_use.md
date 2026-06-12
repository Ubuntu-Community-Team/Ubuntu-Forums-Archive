---
title: "Is Xubuntu 11.10 'still' safe to use?"
date: 2013-05-16
forum: General Help
---

### Post by kippers on 2013-05-16
Hi, I've been happy (ish) using version 11.10 on laptop and desktop for some time.
On my laptop (NVidia GeForce 8200m) I often reduce screen resolution from 1366x768 to 1024x768
 and clone the display to the vga port, all done through nvidia 173 driver and nvidia-settings, easy.

In the last month I have tried 12.04, 12.10, and 13.04, all of which have nvidia issues. 
(Only 1366x768 resolution available for laptop, and 640x480 to vga port)

After many days searching, I've decided it's either, go back to 11.10 or drop buntu (last resort).
13.04 does offer the 173 driver, but no compatible nvidia-settings.
Is there a version that will recognise the 173 driver?

So back to my question, when I reinstall 11.10, I'm constantly reminded that this version is no longer
supported by buntu (fair enough), but am I exposing myself to security (or any other) problems sticking with 11.10?

Yesterday I installed Debian 7, which does include the 173 driver and a compatible nvidia-settings, so I know
it's possible. Unfortunately debian felt very sluggish (probably why they call it Wheezy).

Thanks (Sorry for waffling!)

---

### Post by mastablasta on 2013-05-16
security and repository will need to be changed. you can run the old one htough if any of the new ones really don't work.

Debian sluggish? that's new. usually it was faster.

---

### Post by alan9800 on 2013-05-16
Have you already tried to follow the instructions of the [NdiviaManual](https://help.ubuntu.com/community/NvidiaManual) page?

---

### Post by kippers on 2013-05-16
> **alan9800 said:**
> Have you already tried to follow the instructions of the [NdiviaManual]("https://help.ubuntu.com/community/NvidiaManual") page?

Yes, I have tried many fixes over the last couple of weeks, which would result in no effect at all, or worse, booting to a blank screen
where it seemed easier to re-install xubuntu.

The nearest I came to a solution was a correct display from the vga socket but a blank laptop screen, unfortunately I re-installed
again and couldn't replicate that result.

At the moment I have returned to 11.10 so all is working at the moment.

Thanks.

---

### Post by kippers on 2013-05-16
> **mastablasta said:**
> security and repository will need to be changed. you can run the old one htough if any of the new ones really don't work.

Debian sluggish? that's new. usually it was faster.

I think I'll go back to 11.10 on my laptop and 13.04 on desktop to keep experimenting.

Maybe debians sluggishness was imagined, maybe it's my 5yr old laptop.

Thanks for the quick response.

---

### Post by kleenex on 2013-05-16
Hi **Kippers**. Unfortunately Ubuntu 11.10 ("Oneiric Ocelot") is no longer supported. Please check this announce: [http://article.gmane.org/gmane.linux.ubuntu.security.announce/2138](http://article.gmane.org/gmane.linux.ubuntu.security.announce/2138) You should update your Ubuntu to for example 12.04, 12.10 etc.

---

### Post by kippers on 2013-05-16
Hi kleenex, yes I would like to upgrade but 12.10 was a pain, as many times on shutdown the screen goes blank but the laptop appears to still be running 
or at least the fans keep running. 

I may have another look at 12.04  as I've just discovered nvidia driver 280.13 works on 11.10, so I may have this option on 12.04.

As far as I understand there have been changes to xorg that have caused nvidia problems, although I may just be confused (that's more likely).
11.10 used 2:1.10.4-1ubuntu4.5
12.04 uses 2:1.11.4-0ubuntu10.13 .........  I may have some luck here
12.10 uses 2:1.13.0-0ubuntu6.2
13.04 uses 2:1.13.3-0ubuntu6

Thanks

---

### Post by sudodus on 2013-05-16
> **kippers said:**
> 
I may have another look at 12.04  as I've just discovered nvidia driver 280.13 works on 11.10, so I may have this option on 12.04.


I suggest that you download 12.04.2 instead of 12.04 and a lot of updates. This is a long time support version (LTS), which means that by now, one year after the original release, it is quite stable and polished.

Ubuntu 12.04 has LTS until April 2017 and Xubuntu 12.04 until April 2015 while Lubuntu has end of life October 2013.

With a light-weight desktop environment (Xubuntu with XFCE) or ultra light-weight desktop environment (Lubuntu with LXDE) you might not need a proprietary graphics driver. The nouveau driver is performing quite well with aging nvidia graphics chips for me. And in this case you might also try 13.04.

-o-

I do not recommend that you use 11.10, because it has passed end of life and will receive no security updates. If you do not connect to the internet it is OK, otherwise there will be an increased risk. Maybe not big, but definitely increased.

---

### Post by kleenex on 2013-05-16
Hi **Kippers**. I also have an nvidia (ge force 7100) graphics card. I did not have anything to do during Xubuntu 12.04 install - no **xorg.conf** file generate etc. Everything works out-of-the-box. 

```
**## /etc/X11/xorg.conf file contains:**

Section "Device"
    Identifier    "Default Device"
    Option    "NoLogo"    "True"
EndSection
```

I have also installed these packages: [COLOR=#006400]nvidia-common 1:0.2.44.2[/COLOR], [COLOR=#006400]nvidia-current 304.88-0ubuntu0.0.2[/COLOR] and [COLOR=#006400]nvidia-settings                        304.88-0ubuntu0.0.2.[/COLOR] That's all.

**edit:** One more thing: another reason for upgrading to e.g. Xubuntu 12.04 is that this release is LTS - continues to be actively supported with security updates and select high-impact bug fixes. For upgrade process, please check: [https://help.ubuntu.com/community/PreciseUpgrades](https://help.ubuntu.com/community/PreciseUpgrades)

Best regards **Kippers**.

---

### Post by kippers on 2013-05-18
Thanks for all the advice, all is now (sort of) working.

Xubuntu 12.04.2 LTS with the default nouveau driver and arandr (no nvidia success at all).
This gives access to all available resolutions on laptop screen and vga port.

I always switch off all fancy effects and clutter so this works ok for me.
Not sure if that would be enough for some users.

The only 'problem' seems to be the laptop fans sound to be working quite hard, not full speed but but not as quiet on idle as nvidia can be. 

Still, it works, now to install 13.04 on my desktop so I can keep watching for an nvidia fix. 
I'll probably 'if the wife allows' have a new laptop by the time LTS support runs out.

Thanks again to everyone, (Any advice how to mark this thread as solved?)

---

### Post by claracc on 2013-05-18
How to mark the thread as solved: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

