---
title: "Using Ubuntu  LTS after support has ended"
date: 2017-11-18
forum: General Help
---

### Post by dellboy on 2017-11-18
Hi,
in the next few months, I will be launching a start-up where we hope to be using Ubuntu for most of our PCs. We will have a lot of remote workers and only really developers will be using non-Ubuntu systems. So we plan to use the LTS version so that is not much management to be done by our in office and remote IT support team

The question I have is when the support does end for the LTS. How would we go about updating the system to the next newest version of the LTS is it  a simple terminal command. We can run in order to update the systems. we will have all pcs on are remote software 


Also, as we may be setting this up before  17.10 or the version of Ubuntu with gnome will be the default desktop environment. If we were to install 17.10 and right now, how could we upgrade to the latest LTS as I would like to start our employees on the interface. We plan to use going forward

Thanks for your help.
Many thanks

---

### Post by coldraven on 2017-11-18
> in the next few months, I will be launching a start-up
In the ten years that you have been on this forum have you not learned about LTS distributions?
The mods might not like this but it needs to be said.

---

### Post by deadflowr on 2017-11-18
You should be given an option to upgrade at least 3 months after the next LTS is release.
(LTS to LTS upgrades become available after the 1st point release)

You can run either the terminal command
```
do-release-upgrade
```
to upgrade to the next release.

Or open the software updater and after you run a normal update it should give an optional added button marked as Upgrade which will allow you to upgrade using a more graphical approach.

Depending upon how you've set the system, there maybe a setting you have to toggle.
The upgrader has 3 settings that the system can be set to upgrade to, 
1 is LTS to LTS; simply marked as lts or long term support
2 is any release to the next available release; also known as normal
3 is nothing; the system will not look for any available upgrade nor try to upgrade; marked as never, typically.

To check what the setting is, in a terminal you would need to look at a file
```
cat /etc/update-manager/release-upgrades
```
look at the Prompt= setting
You would need to edit this file if it isn't the setting you want.

To check the setting in a graphical way open the program Software and Updates and go to Updates,
there will be a line that reads: Notify me of a new Ubuntu release: and a toggle bar. Simply toggle to the setting you wish to set.

> Also, as we may be setting this up before 17.10 or the version of Ubuntu with gnome will be the default desktop environment. If we were to install 17.10 and right now, how could we upgrade to the latest LTS as I would like to start our employees on the interface. We plan to use going forward

If you are going to deploy 17.10 then it should be set to upgrade to normal which will allow you to upgrade immediately when the next LTS release (18.04 is an LTS release) comes out.

If you were to install anything before 17.10 then avoid 17.04 since that only has around a month or so left of support (maybe more but it's end of life is sometime around new year)
I think, not sure, but think 17.04 will only upgrade to 17.10. So you would have to do a double upgrade to get from 17.04 to 18.04.


Hope it makes sense.

---

### Post by Yellow Pasque on 2017-11-18
Try to do some googling first:
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2FSupport.A16.04.x_Ubuntu_Kernel_Support](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2FSupport.A16.04.x_Ubuntu_Kernel_Support)
[https://askubuntu.com/questions/110477/how-do-i-upgrade-to-a-newer-version-of-ubuntu](https://askubuntu.com/questions/110477/how-do-i-upgrade-to-a-newer-version-of-ubuntu)

> So we plan to use the LTS version so that is not much management to be done by our in office and remote IT support team

Yeah, the least amount of fuss would be to use Ubuntu 16.04.1 and then you're good until April 2021 (assuming your hardware is not very recent and works with Ubuntu 16.04.1). 

> If we were to install 17.10 and right now, how could we upgrade to the latest LTS as I would like to start our employees on the interface.
Personally, I wouldn't start with 17.10, as then I'd have to do a major upgrade fairly quickly. I don't see why it's a huge deal to start on the Gnome-based interface when it's made to "feel" similar to the old interface (pure Unity). It would be low on my list of considerations. The other alternative is to wait until 18.04 is released.

---

### Post by dellboy on 2017-11-18
thank you all for your help i am not used Ubuntu for an few years as an main os 

thank you to Temüjin  and deadflowr  , especially
> **coldraven said:**
> In the ten years that you have been on this forum have you not learned about LTS distributions?
The mods might not like this but it needs to be said.

---

