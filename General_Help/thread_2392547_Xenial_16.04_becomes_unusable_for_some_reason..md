---
title: "Xenial 16.04 becomes unusable for some reason."
date: 2018-05-22
forum: General Help
---

### Post by Cavsfan on 2018-05-22
I installed Xubuntu Xenial Xerus 16.04.4 on a new PC UEFI/GPT.  Just when I got every thing like I wanted, the screen began to go gray and nothing would respond.
Although Xubuntu comes with just a top panel, I create a bottom panel.
The bottom panel became the top panel and all I could do was press Cntl+Alt+t to get a terminal to open, then press F11 to get it full screen then I could use it.

I had the Nvidia 384.111 driver installed (nvidia-384.) as I have a  NVIDIA  GeForce GTX 980 Ti card. So, I un-installed the driver but, no change.

I could not figure it out so I just re-installed from ISO and yesterday it began doing the same thing.
So, I logged in as guest and had zero problems. Then I knew there was just something wrong with my logon.

I first purged the Nvidia driver and then entered this in terminal:
```
mv ~/.local ~/local-bak
mv ~/.compiz ~/compiz-bak

```
I then rebooted and all was back to normal.

Reinstalled the 384.111 driver, restarted and the screen began doing the same thing.
I installed it via additional drivers.

[ATTACH=CONFIG]279795[/ATTACH]

So, I am using the Nouveau driver and it seems to be working ok.

Just sort of wondering if any one might have a clue as to why this is happening.

I've also got 18.04 and 18.10 installed and haven't had this same problem with either one of those.

It could be almost anything in my mind, compiz being one but, I've been using compiz for several years and am pretty comfortable with it.

---

### Post by #&amp;thj^% on 2018-05-22
Cavsfan I had problems with 384.xx driver on 16.04 also, but the driver form ppa:graphics-drivers/ppa has been good for me. (On 16.04)
On 18.04 I just use for the time being is from the repos "nvidia-driver 390" and that works well there. (With Compiz & Emerald)
BTW my card is a "GeForce GTX 560 Ti" 
**Special Note**: I lock my "xrog.conf' from being over written though.

---

### Post by Cavsfan on 2018-05-22
> **1fallen said:**
> Cavsfan I had problems with 384.xx driver on 16.04 also, but the driver form ppa:graphics-drivers/ppa has been good for me. (On 16.04)
On 18.04 I just use for the time being is from the repos "nvidia-driver 390" and that works well there. (With Compiz & Emerald)
BTW my card is a "GeForce GTX 560 Ti" 
**Special Note**: I lock my "xrog.conf' from being over written though.

Thanks! I was in Windows 10 for a while playing Need For Speed Most Wanted - Black Edition :P
If you've never played it, you're missing out. It's from 2005 and it's unreal!
There is a new version out in 2018 but, although I've now got the machine and card to play it I haven't gotten it.
We've tried it on Wine and it did not work (Linux).

I decided to check on Xenial and it was still messed up with no panels top or bottom.
I added the PPA. Then I installed nvidia-396 (396.24). Rebooted and the top panel appeared for about a second maybe.

The only thing saving the whole thing is Cairo Dock which has an Application menu, my Vivaldi browser, some other stuff along with a logout button that I can logout, restart, etc. from.
I doubt switching to the 390 driver will help because Windows is set to update to the most recent Nvidia driver that comes along.

Depending on how it goes, I may just install something else. Right now I dunno...

---

### Post by Cavsfan on 2018-05-24
I went ahead an did another clean install of Xubuntu 16.04.4 LTS.
I added the nvidia-390 driver from that ppa. I noticed on the page with the info that the 390 driver is  the "Current long-lived branch release".
While the nvidia-396 driver is the "Current short-lived branch release".

Can't say it won't happen again but, I'm going to try to not do whatever it was I did twice. :P

---

