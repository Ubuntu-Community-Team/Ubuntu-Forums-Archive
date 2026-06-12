---
title: "W10 Duel Boot Problem"
date: 2021-02-09
forum: General Help
---

### Post by mountainman70 on 2021-02-09
I have a Dell Model 9020 Small Form Computer I am working on for a friend.

First I have been Dual Booting Windows & Ubuntu for years on different computers & have never run into this problem.

The Dell 9020 has W10 Pro installed & it opens fine as a single OS on HD. When I install Ubuntu 20.04 on the HD  I start having problems with W10.
The first time I open the Dual Boot, W10 or Ubuntu open normally. The next time I open W10 it takes several seconds to open. After that every time I try to open W10 it shows a blank screen & takes longer& longer to open, until it won't open at all. Ubuntui opens every time as it should.

I have tried clean installs of both OS's on several HD's with the same results. Has anybody had this problem or know how to correct?


Thanks for any replies.

---

### Post by CelticWarrior on 2021-02-09
No, not a dual boot problem. If any, it's a Windows problem.

(And yes, it's "dual" as in "two", not "duel" as in "fighting each other")

For any dual boot with Windows 8 or newer disabling the Fast Startup feature is a must. Then, as usual, users shouldn't access the Windows system partition (the "drive C:\") from the other OS and specifically should avoid writing to it from outside Windows. If users need to share files between OSes that can should be done in a different data only partition.

When the aforementioned conditions are met then whatever happens with one OS or the other has nothing to do with the dual or multi boot.

---

### Post by mountainman70 on 2021-02-09
Thanks for the reply. As for the spelling I could say they are fighting each other. But I will blame the spelling on "old age" which I do qualify. LOL

---

### Post by oldfred on 2021-02-09
How much did you shrink the NTFS partition?
Windows NTFS really likes 30% free to work well. At 10% free it gets really slow and you just about cannot do a defrag.

Regular maintenance like chkdsk & defrag often required if issues.

---

### Post by mountainman70 on 2021-02-10
> **oldfred said:**
> How much did you shrink the NTFS partition?
Windows NTFS really likes 30% free to work well. At 10% free it gets really slow and you just about cannot do a defrag.

Regular maintenance like chkdsk & defrag often required if issues.

Thanks for replying oldfred. My HD's are all 1TB. I have this one set at 474.18 for W10 & the ubuntu partition is set at 457.33. I do run sfc /scannow, dism and chkdsk on W10 just to make cloning easier.

---

### Post by dragonfly41 on 2021-02-10
[COLOR=#000000]> I have tried clean installs of both OS's on several HD's with the same results. 
I am on Dell 3268 with W10 in my main internal drive with a dormant version of Ubuntu in another partition.
Over a year ago I gave up on sharing Windows 10 and Ubuntu on the same internal HD.
All my Ubuntu work is now on external USB 3.0 Crucial 1TB SSD's (in dual docking bay with own power).
I do not see any great loss of performance through USB 3.0.[/COLOR]

---

### Post by oldfred on 2021-02-10
I have done multiple full installs to USB3 flash drives.
But then installed to a SSD I converted to a USB adapter.

Plesently surprised how fast it was.
Full install to internal SSD is about 10 min.
Full install to internal HDD is about 12 min. HDD is faster 7200rpm.
Full install to flash drive USB3 over 45 min.
Full install to SSD in USB3 adapter 11 to 12 min. Or about as fast as a faster HDD.

In all cases installing from RAM, using toram parameter and prepartitioned, so just selecting the ext4 partition as / (root).

---

### Post by dragonfly41 on 2021-02-10
[COLOR=#000000]> and prepartitioned, so just selecting the ext4 partition as / (root).

**+1** ..  Using GParted in LiveUSB/DVD.[/COLOR]

---

### Post by mountainman70 on 2021-02-10
An update on my problem. After turning off Fast Boot W10 started to boot. From the time I choose W10 it takes 20-25 seconds to boot. Using Startup or Restart it still takes the same amount of time. I can live with it so they will also.

---

### Post by CelticWarrior on 2021-02-10
[https://www.windowscentral.com/how-disable-windows-10-fast-startup](https://www.windowscentral.com/how-disable-windows-10-fast-startup)

That feature is only to give users the illusion that Windows boots fast

---

### Post by mountainman70 on 2021-02-10
> **CelticWarrior said:**
> [https://www.windowscentral.com/how-disable-windows-10-fast-startup](https://www.windowscentral.com/how-disable-windows-10-fast-startup)

That feature is only to give users the illusion that Windows boots fast

I don't like Windows and I rarely use it. In fact I have to stop and think how to do anything in it. Love Ubuntu.

---

