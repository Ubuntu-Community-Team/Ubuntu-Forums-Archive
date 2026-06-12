---
title: "a couple of issues with Feisty Fawn"
date: 2007-04-21
forum: General Help
---

### Post by mariavon on 2007-04-21
Ok so I have a Acer Aspire 3681WXMI laptop with now ubuntu 7.04 installed.
And I have a couple of problems with it.

1.  I have no sound at all
2. Wifi doesn´t work   (Orange Livebox router & Broadcom 4318 ) -  FIXED
3. I can´t get root access to edit the apt/sources.lst in ubuntu  -  FIXED
4. su command doesn´t work in terminal
5. I can´t find a way to configure my the touchpad. I do not want the click function enabled

Some help please!

---

### Post by montgoej on 2007-04-23
I can't help you with anything but 4 yet, although I have an Acer Aspire 3680 on the way, but I can tell you that su isn't supposed to work, because the root account is disabled.  If you need a root terminal type "sudo -s -H" but unless you enable the root account, you can't use SU...at least I think you can't.
~Jordan Montgomery

---

### Post by tonywhelan on 2007-04-25
> **mariavon said:**
> Ok so I have a Acer Aspire 3681WXMI laptop with now ubuntu 7.04 installed.
And I have a couple of problems with it.

1.  I have no sound at all

5. I can´t find a way to configure my the touchpad. I do not want the click function enabled

Some help please!

SOUND - try this which has worked for me on my Acer Aspire 3680. 
:
In a terminal window I ran "alsamixer" which brings up a graphical mixer window. Alll my speaker values were set off ("MM").

Use the right cursor arrow to move to the desired 'column' and then press the "M" on your keyboard to toggle that column on or off. MM is off, 00 is on. Then use up arrow to raise volume to desired level (suggest max except maybe for MIC)

---

### Post by iamhugeinjapan on 2007-04-25
Touchpad clicking is disabled using the  /etc/X11/xorg.conf file.

This thread should help you: [http://ubuntuforums.org/showthread.php?t=421236&highlight=touchpad](http://ubuntuforums.org/showthread.php?t=421236&highlight=touchpad)

---

### Post by cmat on 2007-04-27
I typed **alsamixer** and it said that there was no device. I have had it work with 6.10 but not with 7.04. It's a realtek HD sound card on my Acer 5040 laptop. It said that my card was "SB" but it was a realtek HD card. Maybe the wrong driver is being used for my chipset.

---

