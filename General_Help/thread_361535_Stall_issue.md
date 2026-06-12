---
title: "Stall issue"
date: 2007-02-14
forum: General Help
---

### Post by asnd16 on 2007-02-14
OK weird stuff that I would like explained.  . . . .  
Today was the first time I took a look at my load menu in quite some time (GRUB MENU).  there was 2 others added, I have never used Ubuntu before so I have never gone threw a FULL kernel Update, but is it now automatically loading the .11 instead of the .10 and should I remove the .10 if the .11 is the primary??? Second weird but I think that is the issue why as soon as I turned on my computer today as soon as I started clicking on my shortcut buttons (could open one = like skype then I would try and click on the little Azures button and it has that little effect when you press a button. . . well it goes down but the animation does not release the button thus you cannot click on the Ubuntu menu or any other shortcuts, then I tried going to the file system and open the apps directly. . . Same issue and not only did the buttons go away so does all your panels BUT the ONE app you did get open is still open and running. . . WEIRD . . you cant even restart and my power button usually with one push I get the shutdown menu. . . that is not responsive. . . 

Another little muffin happened today as well my Microphone is not responding, I can hear audio but none of the apps will respond, It worked fine in the morning yesterday then after what I think was an update, by the evening I tried to make a skype call and out bound audio was not to be heard.  . . This whole deal has not been tested yet today but will this evening. . maybe just needed a restart. 

Third after I had the issues with the shortcuts and buttons I tried to run update manager to see if additional updates are needed, MAYBE A FIX to my little issue.   But there were none . . five minutes later and 10 power downs I got this pop up deal stating that Your system is being updated 6.10 .. but it was an update dialog that I have never seen before and as stated before I have never been with Ubuntu long enough to see a Kernel or huge system update. . . but some of those tasks timed out . . HOW DO I GET THAT to run a little test again or update test if possible?

I have horrible grammar and spelling so please excuse. . .

---

### Post by dcstar on 2007-02-14
> **asnd16 said:**
> OK weird stuff that I would like explained.  . . . .  
Today was the first time I took a look at my load menu in quite some time (GRUB MENU).  there was 2 others added, I have never used Ubuntu before so I have never gone threw a FULL kernel Update, but is it now automatically loading the .11 instead of the .10 and should I remove the .10 if the .11 is the primary??? Second weird but I think that is the issue why as soon as I turned on my computer today as soon as I started clicking on my shortcut buttons (could open one = like skype then I would try and click on the little Azures button and it has that little effect when you press a button. . . well it goes down but the animation does not release the button thus you cannot click on the Ubuntu menu or any other shortcuts, then I tried going to the file system and open the apps directly. . . Same issue and not only did the buttons go away so does all your panels BUT the ONE app you did get open is still open and running. . . WEIRD . . you cant even restart and my power button usually with one push I get the shutdown menu. . . that is not responsive. . . 

Another little muffin happened today as well my Microphone is not responding, I can hear audio but none of the apps will respond, It worked fine in the morning yesterday then after what I think was an update, by the evening I tried to make a skype call and out bound audio was not to be heard.  . . This whole deal has not been tested yet today but will this evening. . maybe just needed a restart. 

Third after I had the issues with the shortcuts and buttons I tried to run update manager to see if additional updates are needed, MAYBE A FIX to my little issue.   But there were none . . five minutes later and 10 power downs I got this pop up deal stating that Your system is being updated 6.10 .. but it was an update dialog that I have never seen before and as stated before I have never been with Ubuntu long enough to see a Kernel or huge system update. . . but some of those tasks timed out . . HOW DO I GET THAT to run a little test again or update test if possible?

I have horrible grammar and spelling so please excuse. . .

The Updates will eventually run themselves again, if you want to force the issue:

System-Administration-Synaptic, then do a "Reload" and then a "Apply All Updates".

You can leave the old kernel version in your system - in fact if you are having issues with the new version, select the old on when you boot up.

You can edit you Grub menu to always default to the last selected option (instead of the top one), do a forum search for instructions on this.

---

### Post by asnd16 on 2007-02-14
> **dcstar said:**
> The Updates will eventually run themselves again, if you want to force the issue:

System-Administration-Synaptic, then do a "Reload" and then a "Apply All Updates".

You can leave the old kernel version in your system - in fact if you are having issues with the new version, select the old on when you boot up.

You can edit you Grub menu to always default to the last selected option (instead of the top one), do a forum search for instructions on this.

Well I got the stall issue in both kernals and in recovery modes as well.

---

