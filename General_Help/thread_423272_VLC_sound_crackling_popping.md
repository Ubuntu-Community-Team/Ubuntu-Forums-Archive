---
title: "VLC sound crackling popping"
date: 2007-04-25
forum: General Help
---

### Post by SnowPunk98 on 2007-04-25
So I was watching a divx and listening to a MP3 the other day in VLC and it was crackling and popping really bad during some parts, it seemed to be when it got loud. Does anyone happen to know a fix to this problem? I am using feisty, fully updated, on a Dell E1705 laptop.

---

### Post by SnowPunk98 on 2007-04-26
bump

---

### Post by SnowPunk98 on 2007-04-30
One more bump

---

### Post by zgerrz on 2007-05-06
From this thread: [http://ubuntuforums.org/showthread.php?t=402321&highlight=crackling]("http://ubuntuforums.org/showthread.php?t=402321&highlight=crackling")


> I think I've found a solution to this problem (or at least it fixed mine).
In the VLC go to -> Settings -> Preferences
then choose Audio -> Output Modules -> ALSA
Hit "Refresh List" and under ALSA Device Name choose the right one (for me it was set to "Default" and I had to change it to the one saying "hw:0,0").
Click "Save" and it should instantly fix the sound issue.

I had the same issue and this fixed it. Credit goes to user lazork for this fix.

---

### Post by lowebb on 2007-05-07
Many thanks for this. This should to stickied to a problems link. I was lost until I found this. Cheers

---

### Post by SnowPunk98 on 2007-05-07
When I choose anything but Default I get no sound. My other options under Audio -> Output Modules -> ALSA are "HDA Intel: HDASTAC92xx Analog (hw:0,0)" and "HDA Intel: HDASTAC92xx Digital (hw:0,0)"

---

### Post by twistedneck on 2007-05-08
The only options i have are Linux OSS and ALSA.. both dont work.  There is no 'refresh list' button.

---

### Post by SnowPunk98 on 2007-05-09
The menu is weird, you have to drill down, there will be ALSA and then ALSA below it.

---

### Post by dmjones500 on 2007-05-19
Worked for me.  Thanks guys!

---

### Post by watmough on 2007-06-08
Wow, thank-you sooo much. I figured there must be something shady going on.

My VLC streams thank-you.

:D

---

### Post by herorev on 2007-06-09
This is the first result on Google for "VLC crackling popping". It was exactly what I was looking for. Thanks!

---

### Post by croc1 on 2007-06-13
:D Thanks worked for me.

---

