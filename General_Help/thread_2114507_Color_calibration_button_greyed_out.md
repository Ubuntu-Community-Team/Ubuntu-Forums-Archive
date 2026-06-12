---
title: "Color calibration button greyed out"
date: 2013-02-10
forum: General Help
---

### Post by roy17 on 2013-02-10
Hi,

I want to calibrate my monitor, but the calibration button in System settings > Color  is greyed out, see attachment for picture.


Can someone help me on how to get this working? I'm new to Ubuntu.

---

### Post by roy17 on 2013-02-10
Bump, someone please help

---

### Post by l6griffin on 2013-02-13
I have the same problem, I have an HP2000z-300 laptop, AMD Wrestler 6310 video, Ubuntu 12.1, fglrx installed per - [Alexislavie]("http://ubuntuforums.org/member.php?u=1138228") thread 1930450, using AMD driver 13.2 Betya3, and a DataColor Spyder3 Colorimeter,

Problem - System Setting, Color, select the HP laptop, click 'Add Profile', a profile(?) is added. I select the profile, but the 'Calibrate' button is greyed out. I place the cursor on Calibrate, and get the message 'The  measuring device is not detected. Please check that it is turned on, and correctly connected', The Spyder3 is USB, I run *lsusb*, and it shows it as ID 8.

Roy hope this helps you better define your problem. I'm going to post in Hardware.

Larry

---

### Post by lunaphiles on 2013-03-20
I am having the same problem - wow.

---

### Post by l6griffin on 2013-03-20
> **lunaphiles said:**
> I am having the same problem - wow.

I was able to solve the problem and run calibration. Unfortunately I don't remember the solution reloading Ubuntu or the video driver.

Larry

---

### Post by lunaphiles on 2013-03-20
> **l6griffin said:**
> I was able to solve the problem and run calibration. Unfortunately I don't remember the solution reloading Ubuntu or the video driver.

Larry


My problem is that I am hooking up my 8" Acer to a 19" Dell, and I want to make the colors the same. The 19" seems to be highly muted in the green-blue area.

It would seem that I should be able to use the Acer WebCam to calibrate the 19"

It is easy enough to set the Acer upside-down on the 19"

Which is what a colorimeter would seem to be.

I noticed that the 19" has a mode that goes through the colors, but the screen powers down when there is no activity.

---

### Post by l6griffin on 2013-03-20
> Which is what a colorimeter would seem to be.

I noticed that the 19" has a mode that goes through the colors, but the screen powers down when there is no activity.

The colorimeter that I have is a Spyder3 by Datacolor. It is a separate device that attaches (suction cups, ugh) to the screen. I'm not recommending the Spyder3, and there are other devices out there. IIRC there are programs(?) free to download that are a series of screens that you visually adjust for best viewing. I found them in searching for a work around to my original problem. One of these should work to determine where the fault is between you Acer and monitor.

Larry

---

### Post by simonrodan on 2014-02-07
Does anyone have a solution (that they can remember...)?
Thanks
Simon

---

### Post by l6griffin on 2014-02-08
The button is greyed out because Ubuntu the device you are using to calibrate. Trouble your calibration device. I quit working on my laptop with Ubuntu 12.10 when I found the brightness lock didn't qappear to be an easy fix. I turned on the laptop a few months ago and it was updated 13.04 then 13.10. The last update to 13.10 fixed the brightness problem. I'm currently working with a Nexus 7 and the laptop. Don't know when I'll get to calibrating it again. Blame Windows 8, MSFT hasn't got a clue what to do with desktop, smartphones, and phablets.

Larry

---

