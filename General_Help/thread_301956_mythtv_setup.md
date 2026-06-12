---
title: "mythtv setup"
date: 2006-11-17
forum: General Help
---

### Post by Kethinov on 2006-11-17
After most painfully following many a vague mythtv setup guide, I appear to have the ivtv driver working as mplayer /dev/video0 displays whatever's currently playing on Fox.

I also have mythtv installed, but I keep stumbling all over the mythtv-setup program, not quite knowing how to proceed through the multitude of options and settings and tweaks.

Anyone want to lend a hand?

My card is a Hauppage PVR 150.

---

### Post by superm1 on 2006-11-19
Your in luck....

Just wrote this a few days ago:

[https://help.ubuntu.com/community/MythTV_mythtvsetup](https://help.ubuntu.com/community/MythTV_mythtvsetup)

---

### Post by Kethinov on 2006-11-19
Great. I've got it working now, but I can't seem to get the channel info. I tried registering with zap2it, but when I try to fetch the channel info with the setup util using my username / pass, I get nothing. No errors, and no channel info either.

Furthermore, I can't change the channel with mythtv very easily. The up/down arrow keys do nothing except bring up a box that says "Adding Char, Unknown (current time)"

However, changing the channel does work if I type the channel number and hit enter.

Thanks again for your help!

---

### Post by Kethinov on 2006-11-19
Also, it seems MythTV breaks my sound balance. I have my PCM right balance lower than my left balance to correct surroundsound issues, but MythTV locks them and maxes them out whenever I go to watch TV, making the sound balance wrong. Is there a way for me to tell MythTV to leave my sound controls alone?

---

### Post by Cadoo on 2007-03-06
If you want to watch TV without using mythTV use VLC. I only use mythTV to record tv. I use mythWeb to schedule recordings. 

In VLC File>Open Capture Device>PVR>OK
To change channels ivtv-tune -c <channel number>

---

