---
title: "Daily ISO image use limits"
date: 2020-04-20
forum: General Help
---

### Post by Mel_Blakey on 2020-04-20
I have downloaded:-

 daily ISO image
focal-desktop-amd64.iso

Can I install this and use it beyond the official launch date or will I have to download and replace it with the 20.04 LTS version.

TIA

---

### Post by howefield on 2020-04-20
You can install the daily iso and updating as normal will keep it current. No need to download a fresh iso on the official launch date.

---

### Post by Mel_Blakey on 2020-04-20
Great Thanks!

I am on a limited data allowance (20gb pm). So, I need to keep the downloads to a minimum :<)

---

### Post by oldfred on 2020-04-20
I use zsync to update daily and convert daily to final version.
I just manually change last daily to name of final ISO. Then zsync only downloads changes.
If daily is only from a few days before release I have has little or no changes downloaded.
I have to run the zsync in same folder as I have ISO.

This updates daily which will stop being focal after release.
[noparse]zsync http://cdimage.ubuntu.com/daily-live/current/focal-desktop-amd64.iso.zsync[/noparse]

I also often change to local repository/mirror when released.
This was the last one I did, after I copied & renamed daily:
[noparse]zsync http://mirrors.gigenet.com/ubuntu/19.10/ubuntu-19.10-desktop-amd64.iso.zsync[/noparse]

---

