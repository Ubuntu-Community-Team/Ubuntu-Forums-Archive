---
title: "no sound with earphones on Ubuntu Mate 20.04"
date: 2020-04-25
forum: General Help
---

### Post by entropy1 on 2020-04-25
I just installed Ubuntu Mate 20.04, and when I play audio (or video with audio) I hear sound from the speakers, but when I plug in my earphones, there is no sound. This is true even when I "Try without installing" Ubuntu Mate 20.04 from a startup flashdrive.

How can I fix this?

When I installed Ubuntu Mate 18.04 a couple of days ago, this problem did not arise.

---

### Post by CelticWarrior on 2020-04-25
Please check sound settings. Unlike other DEs, the MATE DE has a couple of settings in dropdown menus.

---

### Post by entropy1 on 2020-04-25
I have opened sound settings and looked at the different tabs while inserting and removing the earphone jack. Everything looks OK, but I can't hear anything when the jack is inserted.

---

### Post by CelticWarrior on 2020-04-26
I said "dropdown menus"...

---

### Post by entropy1 on 2020-04-26
Yes, within each tab of Sound Settings, there are drop down menus, which I have thoroughly tried out. Under the Sound Effects tab, there is a drop down menu for Sound theme. I tried Yaru and Default, but neither helped. Under the Hardware tab, there is a Profile drop down menu --- I tried Analog Stereo Duplex and Analog Stereo Output, but neither helped. Under the Output tab is the Connector menu --- I tried Speakers and Headphones, which are also automatically changed correctly by inserting and removing the jack, but even selecting manually does not help.

---

### Post by entropy1 on 2020-04-28
Bump. Does anyone else have this problem?

---

### Post by entropy1 on 2020-05-09
While your speakers are playing sound, plug in your headphone jack.

Open Sound Settings

Select the Input tab (yes, ***Input***).

In the Connector dropdown menu,
select either Internal Microphone or Headset Microphone (even if your headphones don't have a microphone). The you should hear sound in your
headphones.

If you remove the headphone jack, you'll get sound from your speakers. But if you then plug in the jack, you will have to repeat the steps in Sound Settings to get sound in the headphones.

Reference: [https://www.reddit.com/r/UbuntuMATE/comments/g95nmx/headphone_issues_2004/]("https://www.reddit.com/r/UbuntuMATE/comments/g95nmx/headphone_issues_2004/")

---

### Post by cpn-here on 2020-10-19
I have the same issue (Thinkpad). Headphone jack worked on 18.04. But now it does not work after 20.04 upgrade. Speakers and bluetooth speakers work. But not the headphone jack. I checked the available hardwares in the sound settings. I think the headphone jack is not recognized as a sound output.

---

