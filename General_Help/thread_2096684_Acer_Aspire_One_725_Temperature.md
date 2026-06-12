---
title: "Acer Aspire One 725 Temperature"
date: 2012-12-20
forum: General Help
---

### Post by jodlajodla on 2012-12-20
I just got my AO725 and I have sucessfully installed Xubuntu 12.10. It's all okay except the temperature which is pretty high if I look to some reviews on the web - it's about 70 to 85° C. I don't have any additional drivers installed, because I only installed the system and some programs.

What could be a problem or it's that the normal temperature for netbook like this?

---

### Post by TOMBSTONEV2 on 2012-12-20
What are you using to monitor temps? What processor does this netbook come with? AMD processors usually run just a little hotter than Intel. If you are running AMD processor C-60 the max operating temperature is 90C. I would say 70 - 85C is quite hot. Is it consistently this hot? Is it this hot while idling?

You should use System Monitor (Dash > Type System) Processes tab and see if anything is running your processor hard.

My netbook always ran hotter with windows. With ubuntu my HP MINI 110-3700 usually averages 30C no load. My Processor is the Intel ATOM N570. I did cut 2 slots in the bottom cover on my netbook to allow better airflow though. Back in windows I always idled my computer when it got to 72. (Usually from transcoding an AVI file to DVD files)

---

### Post by jodlajodla on 2012-12-21
It's C-70 which is almost same as C-60. Max temperature which I saw is about 85° C. Now I have installed fglrx-updates driver and constant temperature in idle is about 60° C and in load about 75° C.

I don't know for Windows because I don't have it and I won't install it ;)

---

### Post by TOMBSTONEV2 on 2012-12-21
Yeah I got rid of windows too. So did you check to see if anything is running your processor above 70%?

---

### Post by jodlajodla on 2012-12-22
Yes, I put some program to make its binary and the highest temperature which I saw is 85° C. I was reading about problems with k10temp sensor and other temperatures - do I need to add any special command to boot (acpi,...)?

---

### Post by TOMBSTONEV2 on 2012-12-22
For the acpi thing perhaps refer to "http://ubuntuforums.org/showthread.php?t=874041"
And when I asked if there is a program running it at 70% I mean is there a process that is utilizing 70% or greater of the processor computing power. 

:) If there is a process hogging all of your processor resources that will lead to an excess of heat, and maybe some slow downs. System monitor is handy for seeing what is running on your computer and the % of CPU the process is using. If you find a process that is utilizing a lot of CPU resources post its name here.

All that aside, is there any dust in the computer that could be causing a lack of air flow? A program called Psensor can be installed in xubuntu ```
sudo apt-get install Psensor
``` which gives you an idea of other temperatures in your computer as well.
Psensor gives temps like the northbridge chip, or cpu socket as well as hd temp.

---

### Post by jodlajodla on 2012-12-23
> And when I asked if there is a program running it at 70% I mean is there a process that is utilizing 70% or greater of the processor computing power.
> Yes, I put some program to make its binary and the highest temperature which I saw is 85° C.
There was 100% CPU load and max 85° C (max working temperature for this processor is 90° C :???:).

Before Psensor I have installed lm-sensors and xsensors but there is no any difference between number of sensors and temperatures.

> All that aside, is there any dust in the computer that could be causing a lack of air flow?
I think this isn't possible because the computer is 4 days old.

What would be different if I enable ACPI?

---

### Post by TOMBSTONEV2 on 2012-12-23
What was the process that was running your system cpu to 100%, doing anything else could leave you in the same spot a process is just going to keep running your system hard. I have a feeling if we get the processor down to 2% or less on idle your problem will be solved.

---

### Post by jodlajodla on 2012-12-26
Now I cooled down netbook to 60° - 65° C in idle. I load nomodeset and pcie_aspm=force booting commands. I also see there are some modules like battery, thermal and others which can cool down temperature of computer. Is this real and it will have effect?

Is 60° C in idle normal for netbook like these?

---

### Post by vksingh on 2012-12-26
use powertop to check what is consuming more power in your machine

---

### Post by jodlajodla on 2012-12-26
Where can I check this?

---

### Post by TOMBSTONEV2 on 2012-12-26
Well you first would need to have powertop installed.

```
sudo apt-get install powertop
```

Power statistics > processor this will tell you what power is being used for in your processor.

---

