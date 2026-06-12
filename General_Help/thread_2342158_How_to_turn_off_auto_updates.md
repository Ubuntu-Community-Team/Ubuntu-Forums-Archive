---
title: "How to turn off auto updates?"
date: 2016-11-04
forum: General Help
---

### Post by silverfox2 on 2016-11-04
I recently upgraded from Ubuntu 14.04 LTS to 16.04 LTS. I had auto updates shut off before the upgrade, so I could pick and choose what/when to update on the machine. It took forever to do this, as simply un-ticking the option to turn off auto updates was useless.

Since I see no option to turn the auto updater off, I have it set to check every 2 weeks. Yet, in the last week alone, I have turned my machine on to be told that software updates are available..... 3 or 4 times. Is there something I am missing as far as turning the updates off, or at least stopping the system from checking on its on constantly? Or is the system designed to ignore whatever the owner tells it, and check for updates whenever it wants?

---

### Post by #&amp;thj^% on 2016-11-04
> **silverfox2 said:**
> I recently upgraded from Ubuntu 14.04 LTS to 16.04 LTS. I had auto updates shut off before the upgrade, so I could pick and choose what/when to update on the machine. It took forever to do this, as simply un-ticking the option to turn off auto updates was useless.

Since I see no option to turn the auto updater off, I have it set to check every 2 weeks. Yet, in the last week alone, I have turned my machine on to be told that software updates are available..... 3 or 4 times. Is there something I am missing as far as turning the updates off, or at least stopping the system from checking on its on constantly? Or is the system designed to ignore whatever the owner tells it, and check for updates whenever it wants?

Hello Using your favorite editor open the file /etc/apt/apt.conf.d/10periodic and change:
```
APT::Periodic::Update-Package-Lists "1";
``` 
To:
```
APT::Periodic::Update-Package-Lists "0";

```
My method went like this:
```
sudo -H gedit /etc/apt/apt.conf.d/10periodic
```
But now all security updates and upgrades and such fall in your hands. (Just friendly advice)
Cheers

---

### Post by silverfox2 on 2016-11-04
Thank you, I will try that. Yes, I am aware that keeping it secure with updates is now on me to do manually, and thats how I want it.

I dont understand why Ubuntu makes you jump through hoops to disable auto updates. Why put the option there (in the older versions) or even the option for every 2 weeks/month.... if those selections are ignored and the system checks for updates whenever it chooses? If it would have followed my selections and checked every 2 weeks, I could have lived with it. But it aggravates me when software doesnt recognize my choices, and does whatever it wishes.

The file originally looked like this:```

APT::Periodic::Update-Package-Lists "14";
APT::Periodic::Download-Upgradeable-Packages "0";
APT::Periodic::AutocleanInterval "0";
APT::Periodic::Unattended-Upgrade "0"; 
```

and now looks like this:```

APT::Periodic::Update-Package-Lists "0";
APT::Periodic::Download-Upgradeable-Packages "0";
APT::Periodic::AutocleanInterval "0";
APT::Periodic::Unattended-Upgrade "0";      
```

Thanks again!

---

### Post by mcduck on 2016-11-04
> **silverfox2 said:**
> 
Since I see no option to turn the auto updater off, I have it set to check every 2 weeks. Yet, in the last week alone, I have turned my machine on to be told that software updates are available..... 3 or 4 times. Is there something I am missing as far as turning the updates off, or at least stopping the system from checking on its on constantly? Or is the system designed to ignore whatever the owner tells it, and check for updates whenever it wants?

The option is for how often you want to be *notified about* updates. Since installing security updates as quickly as possible is absolutely critical for keeping your Linux system safe, it will check for updates daily, and if there are no important security updates, then waits until your configured time before bothering you about the less-critical updates. However if there are important security updates available, you are notified about them immediately so you hopefully get them installed before the security holes are exploited by someone.

---

### Post by #&amp;thj^% on 2016-11-04
> **mcduck said:**
> The option is for how often you want to be *notified about* updates. Since installing security updates as quickly as possible is absolutely critical for keeping your Linux system safe, it will check for updates daily, and if there are no important security updates, then waits until your configured time before bothering you about the less-critical updates. However if there are important security updates available, you are notified about them immediately _**so you hopefully get them installed before the security holes are exploited by someone**_.

+1:)
And Nicely put.

---

### Post by silverfox2 on 2016-11-04
Then I may be going back to windows. I refuse to have any software on my system, that controls my system, rather than allowing me to control it, for any reason.... regardless of anyone else's opinion of that. I dont consider an update to Fotoxx an important that the system needs to warn me about immediately. Like I said, being notified 3 or 4 times in 1 week, when the option was set to every 2 weeks, is ridiculous.

---

### Post by pauljw on 2016-11-04
That's what happens when the primary interest is making linux more user friendly so windows users can switch.  They're accustomed to having the OS do their thinking for them.  Now they're complaining when linux acts like windows...

---

### Post by silverfox2 on 2016-11-05
> **pauljw said:**
> That's what happens when the primary interest is making linux more user friendly so windows users can switch.  They're accustomed to having the OS do their thinking for them.  Now they're complaining when linux acts like windows...

Only those who dont know what they are doing (which I admit, is the big majority) and dont care to have control of their systems. Im not a Windows fan either (hence using Linux) but at least when I turn off auto updates, it actually turns them off.

---

### Post by mcduck on 2016-11-05
The very first answer to this thread gives you the instructions how to turn off the update system, what's the problem? You can have full control (and responsibility...) of your system, all you need to do is take it. (Then again, assuming you know what you are doing you'd just end having to run manual commands to check for those security updates every day, or build automatic system of your own ;))

---

### Post by RobGoss on 2016-11-05
I would have to say Ubuntu makes it easier to control updates it's up to you how you want to approach it, Question why wouldn't you want security updates installed on a daily basis as a Ubuntu and Linux user I trust what updates are installed never had any issues. The updater is merely letting you know updates are available doesn't mean you have to install them

---

### Post by silverfox2 on 2016-11-05
> **mcduck said:**
> The very first answer to this thread gives you the instructions how to turn off the update system, what's the problem? You can have full control (and responsibility...) of your system, all you need to do is take it. (Then again, assuming you know what you are doing you'd just end having to run manual commands to check for those security updates every day, or build automatic system of your own ;))

Why do people like you get attitudes? Yes, I can have "full control".... but only after having to use the internet to find commands to enter in a terminal, and I did that... and even THANKED the person for the information. The problem is I shouldnt have to do this. I set the system to do something particular, and it did what it wanted anyway. Why have the option to set something, if it doesnt in fact, change the setting? THATS my issue. I never said I dont want my system secure or updated... but every time a issue like this is raised, thats the attitude you get from people. "Why" I want it set to every 2 weeks, and want it to follow that regiment, isnt the issue here... yet people make it an issue. If checking every 2 weeks is a bad thing, why is the option for the system to do that, even available to select? For all I know, there was a problem with my upgrade to 16.04. I didnt know, so I came here to ask. Geeeesh.

> **RobGoss said:**
> I would have to say Ubuntu makes it easier to control updates it's up to you how you want to approach it, Question why wouldn't you want security updates installed on a daily basis as a Ubuntu and Linux user I trust what updates are installed never had any issues. The updater is merely letting you know updates are available doesn't mean you have to install them

Im well aware of what it does. But that doesnt change the fact that it isnt doing what it was set to do..... which was check every 2 weeks. You may have never had any issues, and you may trust it to install what is suggested whenever they are available. Thats you. Not everybody feels that way, or handles things that way. Ive seen too many updates with problems/bugs. Case in point, I have upgraded 2 of my machines from 14.04 to 16.04, and am experiencing the widespread problem like so many others.... of my HDMI audio disappearing after the machines come out of suspend. The HDMI source even disappears from the audio output options. I have to log out, and log back in.... to have sound. 16.04 has been out for a good while, yet no updates have fixed this issue. So yeah, just because the powers that be "suggest" a certain update, doesnt mean its a good idea, or doesnt have bugs/issues.

Im not bashing Linux... Im really not. I REALLY want it to work for me, as I hate MS. But it gets old reading the attitudes people get, when someone has an issue. My issue and question were legitimate. Its no different than if I changed the setting for the video resolution, and the system ignore my setting, and set the resolution at whatever it wanted, whenever it wanted.

---

### Post by &amp;KyT$0P# on 2016-11-05
silverfox2, I agree with you there.  This is why I just [FONT=Courier New]sudo apt-get purge unattended-upgrades[/FONT] on every 16.04 machine that I don't want auto-updating.

---

### Post by QIII on 2016-11-05
Hello!

When you first started using Windows, did you know how to do everything or did you sometimes have to google or otherwise ask for help?

Just something to bear in mind as you learn a new OS.

I see halogen2 has given you the same solution I use.

---

### Post by #&amp;thj^% on 2016-11-05
> **silverfox2 said:**
> Why do people like you get attitudes? Yes, I can have "full control".... but only after having to use the internet to find commands to enter in a terminal, and I did that... and even THANKED the person for the information. The problem is I shouldnt have to do this. I set the system to do something particular, and it did what it wanted anyway. Why have the option to set something, if it doesnt in fact, change the setting? THATS my issue. I never said I dont want my system secure or updated... but every time a issue like this is raised, thats the attitude you get from people. "Why" I want it set to every 2 weeks, and want it to follow that regiment, isnt the issue here... yet people make it an issue. If checking every 2 weeks is a bad thing, why is the option for the system to do that, even available to select? For all I know, there was a problem with my upgrade to 16.04. I didnt know, so I came here to ask. Geeeesh.



Im well aware of what it does. But that doesnt change the fact that it isnt doing what it was set to do..... which was check every 2 weeks. You may have never had any issues, and you may trust it to install what is suggested whenever they are available. Thats you. Not everybody feels that way, or handles things that way. Ive seen too many updates with problems/bugs. Case in point, I have upgraded 2 of my machines from 14.04 to 16.04, and am experiencing the widespread problem like so many others.... of my HDMI audio disappearing after the machines come out of suspend. The HDMI source even disappears from the audio output options. I have to log out, and log back in.... to have sound. 16.04 has been out for a good while, yet no updates have fixed this issue. So yeah, just because the powers that be "suggest" a certain update, doesnt mean its a good idea, or doesnt have bugs/issues.

Im not bashing Linux... Im really not. I REALLY want it to work for me, as I hate MS. But it gets old reading the attitudes people get, when someone has an issue. My issue and question were legitimate. Its no different than if I changed the setting for the video resolution, and the system ignore my setting, and set the resolution at whatever it wanted, whenever it wanted.

You Are Very Welcome:D
I think you are misunderstanding everyone here.
First there are many people that visit threads like this...and I feel it would be irresponsible for us not to mention the safety aspects of disabling auto-updates. (For New users)
I am very much like you...disliking Nag-Windows or Notifications nagging me I have to do something.
But bear in mind the growth of Linux currently... we are seeing a lot of inexperienced users, so again this is meant to be informative... and not so much meant to be a Lecture to a more experienced user. So No offense meant.:grin:
Kind Regards

---

### Post by silverfox2 on 2016-11-05
> **halogen2 said:**
> silverfox2, I agree with you there.  This is why I just [FONT=Courier New]sudo apt-get purge unattended-upgrades[/FONT] on every 16.04 machine that I don't want auto-updating.

Thank you. At least somebody gets it.

> **QIII said:**
> Hello!

When you first started using Windows, did you know how to do everything or did you sometimes have to google or otherwise ask for help?

Just something to bear in mind as you learn a new OS.

You still dont get it. You "assume" I am new to Linux, simply because I have a legitimate issue of a setting not responding correctly, when I changed the setting. It has nothing to do with me "learning the system" as I have been using Linux off and on for 10yrs or more. Stop making this about me, or acting like I dont know what I am doing because I didnt know the commands to enter. I changed a setting.... plain and simple. It didnt work. THATS the issue. One thing is for sure, when I first "found" the update options in Windows years and years ago, and changed it to what I wanted.... the setting took effect and worked.


> **1fallen said:**
> You Are Very Welcome:grin:
I think you are misunderstanding everyone here.
First there are many people that visit threads like this...and I feel it  would be irresponsible for us not to mention the safety aspects of  disabling auto-updates. (For New users)
I am very much like you...disliking Nag-Windows or Notifications nagging me I have to do something.
But bear in mind the growth of Linux currently... we are seeing a lot of  inexperienced users, so again this is meant to informative and not so  much meant to be a Lecture to a more experienced user. So No offense  meant.:grin:
Kind Regards

Again, I thank you for your help. I in no way took any of your comments as a lecture, or you having an attitude. Im sorry if you thought that. But when people basically say "you were given the answer, whats the problem?"..... that denotes attitude. Some people dont like you saying anything negative about their beloved operating system in any way. I had an issue, you answered me, and I "think" so far it has worked, and I thanked you for your help. I even stated I like to update my systems manually. I never said I wanted the unattended and never updated. yet, thats where other comments took the thread, and the other comments come in that were not called for.... like I was some stupid newbie who didnt know what he was doing, and had done something wrong. The issue had already been handled before the other comments (which were nothing but opinion ad had nothing to do with the issue) started. Its those comments that run people away from Linux. Ive read comments like that and worse, for years. Its the main reason I only come to a forum for a "have to" case. So I am going to stop responding on this thread. I think the issue is fixed, if not, I will revisit the thread. But Im not going to sit hear and be part of the irrelevant conversations, simply because I dont maintain/handle my systems the way others want me to. Thanks again for your help, it was VERY much appreciated!

---

### Post by QIII on 2016-11-05
> **silverfox2 said:**
> 
You still dont get it. You "assume" I am new to Linux, simply because I have a legitimate issue of a setting not responding correctly, when I changed the setting. It has nothing to do with me "learning the system" as I have been using Linux off and on for 10yrs or more. Stop making this about me, or acting like I dont know what I am doing because I didnt know the commands to enter. I changed a setting.... plain and simple. It didnt work. THATS the issue. One thing is for sure, when I first "found" the update options in Windows years and years ago, and changed it to what I wanted.... the setting took effect and worked.

No, I most certainly do "get it".  Clearly, what you did was not what needed to be done. The issue is still one of learning -- you did, in fact, need to learn something.  And now you have.  I have been using Linux for over 20 years.  I started using Unix in the 70s.  I still have much to learn and I take the tuition of others thankfully.  

You have taken as a personal attack a simple observation -- I could not have known you had been using Linux for 10 years.

---

### Post by silverfox2 on 2016-11-05
> **QIII said:**
> No, I most certainly do "get it".  Clearly, what you did was not what needed to be done. The issue is still one of learning -- you did, in fact, need to learn something.  And now you have.  I have been using Linux for over 20 years.  I started using Unix in the 70s.  I still have much to learn and I take the tuition of others thankfully.  

You have taken as a personal attack a simple observation -- I could not have known you had been using Linux for 10 years.

NO, you most certainly do NOT get it! I am AWARE what I did by changing the setting IN the update settings section, was NOT all that was needed to be done! THATS the problem! When a person is presented with ANY type of setting change, we fully and rightfully expect that setting to change from "A to B" as we select it. If not, then we should be presented with something that tells us that "this will not take affect until...." and be informed of what else needs to be done.... even if a simple reboot. I was told I had to enter codes via CLI, and I entered those codes. But that should NOT have to happen. If we cant change a setting, that the system offers us an option to change.... then there is absolutely NO reason to offer that setting in the first place. THATS the issue. When I set it to check every 2 weeks, it should check every 2 weeks. End of story.... no exceptions. Your opinion, my opinion.... nobody's opinion matters. I have NO issue with learning, and again, that is NOT the issue. The fact is, I shouldnt have HAD to learn anything. I changed a setting, thats did nothing. Thats the issue. We can either keep dragging this out and arguing, or you all can just stop. Because there is absolutely no reason to keep dragging this out. This issue was solved and I thanked the person who offered the solution. I "took the tuition thankfully".  But then all the opinions came in after the fact, and THATS where the thread derailed.

---

### Post by oldos2er on 2016-11-05
Closed for staff review.

---

