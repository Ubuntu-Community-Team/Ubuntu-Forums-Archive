---
title: "firmware-addon-dell"
date: 2014-03-23
forum: General Help
---

### Post by scollar1971 on 2014-03-23
Recently while thumbing through forums I read a post about dell having added a tool to update bios ... well up untill this point hadn't managed to mess anything up in ubunto and was quite impressed on how easily I could undo things I had done incorrectly ie. by going back through history and with help on this forum and I was feeling quite    	 	 	 	     invincible (lol) well to make a long story short I grabbed this 'tool' and installed and when I rebooted ubunto would not restart .... any suggestions on how to undo my wrong doings?

---

### Post by deadflowr on 2014-03-23
Do you happen to remember the name of said tool?

---

### Post by scollar1971 on 2014-03-23
[h=2]firmware-addon-dell[/h]

---

### Post by deadflowr on 2014-03-23
Truly beats me, but I did find this
[https://wiki.ubuntu.com/DellBIOS](https://wiki.ubuntu.com/DellBIOS)

which somewhere in there alludes to the use of that package.

---

### Post by scollar1971 on 2014-03-24
Tis there

[http://packages.ubuntu.com/lucid-updates/all/firmware-addon-dell/download](http://packages.ubuntu.com/lucid-updates/all/firmware-addon-dell/download)

---

### Post by scollar1971 on 2014-03-24
Gotta be a way to undo this....... I tried recovery and repair broken pkg's NG funny thing is because boot process seems to nearly completes then I get one of two things followed by a funny looking mouse cursor 1st either a 1/2 screen of colored horizonal lines then black screen withi funny looking cursor or my desktop backgroung VERY large and like split into pieces followed by same screen & cursor so tried low graphics .... ng

---

### Post by scollar1971 on 2014-03-24
I going to try this:
[https://help.ubuntu.com/lts/installation-guide/i386/rescue.html](https://help.ubuntu.com/lts/installation-guide/i386/rescue.html)

---

### Post by scollar1971 on 2014-03-24
Can't seem to make that work either

---

### Post by pqwoerituytrueiwoq on 2014-03-24
are you able to get to a recovery console?
when you try to boot normally can you ctrl+alt+f1 and login to a console?
once you get there try to purge the thing you installed
sudo apt-get purge $packageName

---

### Post by scollar1971 on 2014-03-24
Yes grub loads and recovery console comes up however failsafe returns back to console.

---

### Post by scollar1971 on 2014-03-24
This thread appears to be generating little to no response. Please let me know if anyone feels I should change the title or if anyone could use a little more information to help [SOLVE]

Thanks

---

### Post by coffeecat on 2014-03-24
> **scollar1971 said:**
> This thread appears to be generating little to no response.

Please be patient. The thread is less than a day old. This is an international forum and people who may be able to contribute suggestions may live in different timezones from yourself and will not have seen the thread yet. This is why we have a do not bump more than once in 24 hours rule.

---

### Post by deadflowr on 2014-03-24
Well, maybe some information about the machine would be helpful.
Like is it a laptop, desktop, server(?), phone?
Which model?

And probably most helpful, when you installed it, do you remember it doing anything beyond the installation of the package?

If it did anything, then I think your solution might be within the BIOS settings.
Such as resetting some configurations, like maybe it mucked up the graphics card memory settings or something like that.

---

### Post by scollar1971 on 2014-03-24
Well after many painful hrs of trying to recover from a fatal error I threw in the towel and re-installed but I have a few questions 
[LIST]
[*]Where did all the packages that I downloaded previously get stored?
[*] I was able to find alot of stuff ie. my documents and downloads from before but what about updates and such any chance they are readily available for easy re-install?
[*]Grub is a mess for some reason I now have three ubunto distro to load from (obviosly only one works) but I'd like to get rid of other two
[*]Is there a way to create a emergency repair disk to save system data for a less painful recovery if this ever happens again?
[/LIST]

---

### Post by pqwoerituytrueiwoq on 2014-03-24
1. /var/cache/apt/archives
2. see above, sounds like the same question
3. install [gparted](apt:gparted) on the working install and delete the bad ones (if you need to resize your good install usea live usb/dvd)
4. try remastersys or clonezilla

---

### Post by scollar1971 on 2014-03-25
Thanks, that was quite easy

---

### Post by mörgæs on 2014-03-25
If the problem is solved please mark the thread so.

---

### Post by scollar1971 on 2014-03-25
Actually I never did anything after 'dell-addon-firmware' or what ever the heck it was called , was never asked to make any changes in fact I was actually never even able to even see an installed program ... Didn't think much of it at the time and carried on with daily routines it wasn't untill several hours later that machine seemed to be responding a little sluggish so I figure after several days of 'UP' time that a restart may be in order.... And poof


By the way machine I'm using for my Linux experience is a Dell Dimension 4700 4gb  ddr2 ram (Desktop) 
It's a dual boot win8.1/ubunonto machine I have  Win 8.1  installed on primary 500 gb and ubunto intaslled on a 2nd partitioned 500gb drive.

I am unfortunately required to keep windows around to run some of the office managemnt software I run at my business which I have tried both wine and and on a VM no luck with wine works on VM but does't but not as well

---

### Post by scollar1971 on 2014-03-25
Thanks

---

### Post by mörgæs on 2014-03-25
SOLVED is in the 'Thread tools' menu.

---

