---
title: "xubuntu 12.04 system sensors interpretation problems"
date: 2012-12-13
forum: General Help
---

### Post by andypearce on 2012-12-13
Hi
I have been having a number of problems with my Toshiba Satellite pro l100 going slow on ubuntu 10.04 lts so upgraded (following advice from here) to xubuntu 12.04lts. It runs ok but the flash seems to use much cpu and cannot play iplayer or youtube on large screen without the picture being pixellated and 'choppy' and sound out of sync. I have been told on a previous thread that my prcessor, celeron m, is probably not up to the job and it is true that this is the most basic model of the range produced, but all worked fine on ubuntu 8.10, 9.04 and for a while on 10.04. I have done all I can with the common fixes (chrome instead of firefox for the flash etc ect), so have come to a dead end there

So I have decided it probably is not upto the job but might benefit from a bit of a clean inside, which is next, but also a bit of a look at the temperature the laptop was running at. So I have downloaded the xubuntu sensor plugin from this page

[https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)

then there was a bit of a problem getting it to work 
which was like this
[http://ubuntuforums.org/showthread.php?t=1214242](http://ubuntuforums.org/showthread.php?t=1214242)

but got it going....

right clicked my top panel, clicked panel, then add new items, then sensor pluging and added it.

I have the word 'sensors' at least. It does not look like the thing on the sensors install howto page...

So double clicking it brings up a menu box called sensors viewer and it tells me that sensor type 'acpitz-0' gives a temp1 of 61c and sensor type 'hard disks' 37c

Firstly, can anyone interpret these results for me... what am I looking at here... hard disk temperature of 37 c seems quite straight forward but is it ok. What does sensor type 'acpitz-0 mean and is 61c ok?

Secondly, why doesn't it look like the thing on the SensorInstallHowto page?
Have I got the right thing?
Thanks
A

---

### Post by andypearce on 2012-12-14
I knew it would probably be not a usual thing to use as I have not come accross this before, temperature senors within the laptop, so I will leave it up for a bit longer and see if anyone out there in linux land is using this particular one. I am intending to get this laptop opened up and cleaned to see if that improves the cooling of the cpu and performance of flash. 
I do understand adobe flash issues in firefox, I have tried chrome with the supported flash but the same issues occur. It is not my connection,this one is hardwired and my other slightly different old toshiba laptop running on wifi using U10.04 is still running perfectly....so I have to agree with the conclusion on this thread I started last week

[http://ubuntuforums.org/showthread.php?t=2090181](http://ubuntuforums.org/showthread.php?t=2090181) 

I will report back after cleaning to see if that makes a difference. If anyone is using this xubuntu plug in who can give me a bit of advice on what I am looking at.

---

### Post by Impavidus on 2012-12-14
Here is a screenshot of my xfce sensor plugin. My ambient (room) temperature is 16 &#8304;C.

The easiest way of changing the settings of the plugin is to edit panel preferences (right click somewhere on it), select the sensors plugin and click the edit button.

61 &#8304;C is quite hot and shouldn't occur when running idle.

---

### Post by andypearce on 2012-12-14
Thanks Impavidus for your reply and taking the time to attach the screen shot. I do not have what you have.
Following right clicking the top panel and choosing panel-add to panel and adding the sensor, the word 'sensors' is now on my panel. Double clicking it I get a box called 'sensors viewer' with three options... 'overview' with the choice of sensors type acpitz-0 with a reading of a temp1 only, hard disks with a reading of /dev/sda, or ACPI which has nothing seemingly. The alternative to 'overview' is 'tachometers' which comes up blank when chosen.
As we speak my room is warm with a roaring fire and the sensor is telling me
when selecting acpitz-0 temp1 is 71c, and hard disks 47c.My wife is listening to the radio on I player while I try to get my head around this and system monitor tell me I am using, hovering about 48% of my cpu.
Looks like I do have some sort of sensor... looks like I am running too hot...I will carry on and clean my fan and vents but maybe I have incorrectly intalled the sensor somehow...I will have a look. I will go for editing the settings too.
Thanks
A

---

