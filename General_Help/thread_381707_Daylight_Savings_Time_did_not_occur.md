---
title: "Daylight Savings Time did not occur"
date: 2007-03-11
forum: General Help
---

### Post by SteveF on 2007-03-11
Hi,

I booted up my PC today expecting my clock to have changed.  Nothing happened.  I waited a while and saw there was a software update which included tzdata so I installed and rebooted.  Still no time change.  I read online about running zdump, here's my output:

/etc/localtime  Sun Mar 11 06:59:59 2007 UTC = Sun Mar 11 01:59:59 2007 EST isdst=0 gmtoff=-18000
/etc/localtime  Sun Mar 11 07:00:00 2007 UTC = Sun Mar 11 03:00:00 2007 EDT isdst=1 gmtoff=-14400
/etc/localtime  Sun Nov  4 05:59:59 2007 UTC = Sun Nov  4 01:59:59 2007 EDT isdst=1 gmtoff=-14400
/etc/localtime  Sun Nov  4 06:00:00 2007 UTC = Sun Nov  4 01:00:00 2007 EST isdst=0 gmtoff=-18000

I'm running Ubuntu Edgy Eft and all software is up to date.

Any ideas?

Thanks,

Steve

---

### Post by SteveF on 2007-03-11
Some more information:
I booted into Kubuntu to see if that would work.  It had the same problem.  Still no change to my clock.  I opened the clock and clicked on automatically set time (I forget the exact wording - I'm in Ubuntu right now) which sets the time according to some server.  This changed my clock to the right time.  I unchecked the box again because I do not usually sync with other servers for time.  It kept the changes.

I just don't understand why this didn't happen automatically.  Does it only work if my machine is syncing with servers?

Steve

---

### Post by Trapper on 2007-03-11
Yup, same here on my box. Ubuntu would not update to the revised Daylight Saving Time. Fedora 6 and Win2K on the same box did update successfully. I set the clock back manually and rebooted into Ubuntu several times. No clock update.

---

### Post by yabbadabbadont on 2007-03-11
I have a Dapper install with the updated tzdata.  My machine was running at 1:59:59 this morning (I never sleep) and it automatically jumped ahead to 3:00:00 like it was supposed to.

---

### Post by cmost on 2007-03-11
I'm on Ubuntu 6.10 x86-64, fully up-to-date and the time was updated perfectly when I booted up today!

---

### Post by alanbe on 2007-03-11
Hey All

Running fully up-to-date Dapper.

Time change did not automatically occur when I turned my machine on this morning.

I manually synced it though.

Still much love for Ubuntu.

---

### Post by _Agrajag_ on 2007-03-11
I'm running Edgy, when I booted up this morning (around 10am) the Daylight Savings Time did not/had not adjusted either.  I received the tzdata update several days ago and applied it immediately.  I'll just manually adjust it I guess.

---

### Post by vav on 2007-03-11
I'm running Edgy, and a couple of days ago had done the tzdata or such update. So my system is COMPLETELY up to date, and STILL NO TIME CHANGE TODAY. I had done the zdump or whatever command and seen the Mar11 date. So I'm really surprised.

I even opened the time prefs and said synchronize with server now... STILL NO TIME CHANGE.
If it had problems syncing with server it should have at least told me that. :mad: 

In any case, syncing with server is kinda the brute force way of doing it.

---

### Post by helpdeskdan on 2007-03-11
With much pride, I announced to my friends that the recently downloaded updates to Ubuntu would mean that I wouldn't even have to think about the new daylight saving time.  With much shame, I turned on my computer today to see, like so many others, that such was not the case & I had to manually rdate!!  

Half the time servers in date/time don't really work if you rdate -p them, and if you add your own it mysteriously disappears.  My windows friends are going to have a hay day over this.  

**I absolutely can not believe this!  **

And,  yes, of course I've updated:
 sudo zdump -v /etc/localtime |grep 2007
/etc/localtime  Sun Mar 11 06:59:59 2007 UTC = Sun Mar 11 01:59:59 2007 EST isdst=0 gmtoff=-18000
/etc/localtime  Sun Mar 11 07:00:00 2007 UTC = Sun Mar 11 03:00:00 2007 EDT isdst=1 gmtoff=-14400
/etc/localtime  Sun Nov  4 05:59:59 2007 UTC = Sun Nov  4 01:59:59 2007 EDT isdst=1 gmtoff=-14400
/etc/localtime  Sun Nov  4 06:00:00 2007 UTC = Sun Nov  4 01:00:00 2007 EST isdst=0 gmtoff=-18000

---

### Post by DarkN00b on 2007-03-11
Mine worked perfectly. I didn't have to manually change a thing.

---

### Post by ofb on 2007-03-11
My Ubuntu 6.10 did not update the time either.

o@redfish:~$ sudo zdump -v /etc/localtime |grep 2007
/etc/localtime  Sun Mar 11 09:59:59 2007 UTC = Sun Mar 11 01:59:59 2007 PST isdst=0 gmtoff=-28800
/etc/localtime  Sun Mar 11 10:00:00 2007 UTC = Sun Mar 11 03:00:00 2007 PDT isdst=1 gmtoff=-25200
/etc/localtime  Sun Nov  4 08:59:59 2007 UTC = Sun Nov  4 01:59:59 2007 PDT isdst=1 gmtoff=-25200
/etc/localtime  Sun Nov  4 09:00:00 2007 UTC = Sun Nov  4 01:00:00 2007 PST isdst=0 gmtoff=-28800

Clicking on 'sync once with internet servers' did not move the time forward. Currently sync'd with the default 'ntp.ubuntu.com' and '127.127.1.0'.

A local friend with the same setup has the same results. His machine was on till 4am, just in case that helps.

Exactly what does isdst=0 and isdst=1 mean?

---

### Post by FLPCGuy on 2007-03-11
> **ofb said:**
> My Ubuntu 6.10 did not update the time either.

o@redfish:~$ sudo zdump -v /etc/localtime |grep 2007
/etc/localtime  Sun Mar 11 09:59:59 2007 UTC = Sun Mar 11 01:59:59 2007 PST isdst=0 gmtoff=-28800
/etc/localtime  Sun Mar 11 10:00:00 2007 UTC = Sun Mar 11 03:00:00 2007 PDT isdst=1 gmtoff=-25200
/etc/localtime  Sun Nov  4 08:59:59 2007 UTC = Sun Nov  4 01:59:59 2007 PDT isdst=1 gmtoff=-25200
/etc/localtime  Sun Nov  4 09:00:00 2007 UTC = Sun Nov  4 01:00:00 2007 PST isdst=0 gmtoff=-28800

Clicking on 'sync once with internet servers' did not move the time forward. Currently sync'd with the default 'ntp.ubuntu.com' and '127.127.1.0'.

A local friend with the same setup has the same results. His machine was on till 4am, just in case that helps.

Exactly what does isdst=0 and isdst=1 mean?

My Edgy likewise did not change the time but has the dates & times shown above in /etc/localtime and I confirmed I am in the America/NY [EST] time zone.  I have all updates except the Ofc updates.  Clearly, there is some other issue not yet identified in this forum.  

Obviously, gmtoff is the offset in minutes which changed from 5 hrs to 4 (14,400 min) for me.  I would imagine the isdst flag is whether Daylight Saving Time is ON (1) or off (0).  So it reads Mar 11th at 06:59:59 UTC it is localtime 01.59:59 and DST is off.  The next line, one second later it is on and local time is 03:00 rather than 02:00.

sam@Dell4100:~$ sudo zdump -v /etc/localtime |grep 2007
/etc/localtime  Sun Mar 11 06:59:59 2007 UTC = Sun Mar 11 01:59:59 2007 EST isdst=0 gmtoff=-18000
/etc/localtime  Sun Mar 11 07:00:00 2007 UTC = Sun Mar 11 03:00:00 2007 EDT isdst=1 gmtoff=-14400
/etc/localtime  Sun Nov  4 05:59:59 2007 UTC = Sun Nov  4 01:59:59 2007 EDT isdst=1 gmtoff=-14400
/etc/localtime  Sun Nov  4 06:00:00 2007 UTC = Sun Nov  4 01:00:00 2007 EST isdst=0 gmtoff=-18000
sam@Dell4100:~$

---

### Post by ofb on 2007-03-11
> **FLPCGuy said:**
> Clearly, there is some other issue not yet identified in this forum.

What I can't find under "Adjust Date & Time" is any toggle to use DST or not. I'm wondering if that hasn't been set to true for some machines.

So I'm thinking the questions are:

Where is that information?
How is it set?
Why wasn't it set?

---

### Post by WW on 2007-03-11
I have two computers running dapper. When I booted them today, my desktop had the correct time, but my laptop didn't.  I had to give the command
> sudo /etc/network/if-up.d/ntpdate
to get the correct date on the laptop. (Thanks to soundray on #ubuntu.)  (I suspect I could have also used System->Administration->Time and Date, and clicked on "Synchronize Now".)

By the way, there is no tzdata package in dapper.

---

### Post by jimbob on 2007-03-11
...  (sorry, wrong thread)

---

### Post by wpshooter on 2007-03-11
All 4 of my machines (3 Dapper & 1 Feisty) came out with the correct time this morning.  All updates had been applied to all of these machines before mid-night yesterday.

But I am wondering if this is due to the fact that I have them all set to sync to the Virginia, USA server **OR** because of some fix in the Ubuntu O/S.

After hearing the above posts, I am beggining to suspect that it is because of the syncing to the time server.

Am I wrong ?

Thanks.

---

### Post by Benchrest on 2007-03-11
I wish all problems were no worse than this. It was rather simple to right click on time and select adjust. I was more disappointed with my xp machine that it changed the time without asking me to confirm as indows used to. Or my 98SE system that is no longer supported for time changes.

---

### Post by milehigh on 2007-03-11
My laptop and desktop are both running fully updated Ubuntu 6.10. Both displayed the correct time when I started them up today.:)

---

### Post by tagra123 on 2007-03-11
All of our worked correctly -- 7 machines .


2 of them sync externally and the rest sync to those 2.

---

### Post by Pikestaff on 2007-03-11
My Dapper updated the time correctly... not sure when it did, it was sometime when I was asleep.  I haven't checked my other 'buntu machine yet though, that will be interesting if one updated and the other didn't.

---

### Post by ofb on 2007-03-11
> **wpshooter said:**
> After hearing the above posts, I am beggining to suspect that it is because of the syncing to the time server.

To be clear, I sync'd to internet timeservers manually this morning to see if that changed things. (It did not.)

My box does not stay sync'd otherwise.

As you see from the output above, the box supposedly knows when to change for DST, yet did not apply the change.


Benchrest, I agree it is simple to reset the time manually. However it is worth finding out why DST was not respected now, rather than reset every 6 months. Also we have the mystery that some machines worked while others did not. 

(Bonus issue: what is going to happen when we dual booters use our 98/XP again? I  think their DST adjusts the BIOS time. Would that change then be carried through to the next Ubuntu boot, shifting things off an hour?)

---

### Post by SuSUntu on 2007-03-11
> **wpshooter said:**
> All 4 of my machines (3 Dapper & 1 Feisty) came out with the correct time this morning.  All updates had been applied to all of these machines before mid-night yesterday.

But I am wondering if this is due to the fact that I have them all set to sync to the Virginia, USA server **OR** because of some fix in the Ubuntu O/S.

After hearing the above posts, I am beggining to suspect that it is because of the syncing to the time server.

Am I wrong ?

Thanks.

I won't say your wrong, as its fairly clear that some people are having unexplained issues with the changeover.

I can say, however, with surety that I do not have Ubuntu Edgy set to sync regularly with any timeservers , and the update occurred as expected here.

I was up early this morning with the computer on, and actually confirmed the switchover within a few minutes of it occurring.

I wonder if most of those having issues had their PCs off when the changeover was to have taken place?

---

### Post by ButteBlues on 2007-03-11
I have my Feisty laptop synced to the Virginia and NY servers, and it transitioned perfectly. :)

---

### Post by wpshooter on 2007-03-11
Yes, I run mine 24/7.

I wonder if the computer needed to be actually running for the change to take place **AUTOMATICALLY **?

Thanks for your reply.

---

### Post by _Agrajag_ on 2007-03-11
> **SuSUntu said:**
> 

I was up early this morning with the computer on, and actually confirmed the switchover within a few minutes of it occurring.

I wonder if most of those having issues had their PCs off when the changeover was to have taken place?

My Edgy box was off when the rollover occurred, and didn't update.

---

### Post by helpdeskdan on 2007-03-11
Well, this makes little sense, why does it work perfectly for some and not for others?  

A quick fix: 
sudo apt-get install rdate
sudo rdate clock.psu.edu

Substitute a NTP near you if outside of US.  You may use the -p (print only) option to double check the time is right before setting the time if you like.

---

### Post by WW on 2007-03-11
How can I check if my computer does a network time sync at boot?   Something in /etc/init.d?

---

### Post by qamelian on 2007-03-11
> **wpshooter said:**
> Yes, I run mine 24/7.

I wonder if the computer needed to be actually running for the change to take place **AUTOMATICALLY **?

Thanks for your reply.

Neither of my PCs were running nor do they sync to a time server, but both updated perfectly when I booted them up today. One is a laptop running Feisty. The other is a desktop running Edgy.

---

### Post by qamelian on 2007-03-11
> **WW said:**
> How can I check if my computer does a network time sync at boot?   Something in /etc/init.d?

Right-click on your clock and select Adjust Date & Time. If Configuration is set to manual, it does not do a network time sync.

---

### Post by SuSUntu on 2007-03-11
> **ofb said:**
> 
(Bonus issue: what is going to happen when we dual booters use our 98/XP again?**I  think their DST adjusts the BIOS time.** Would that change then be carried through to the next Ubuntu boot, shifting things off an hour?)

My experience was different than what you theorize. Here's how it went for me:

- Ubuntu Edgy was running at time of DST changeover - update occurred successfully

- Booted into Win XP Pro Partiton 1 - clock updated but was 1 hour fast (should have been 4:00 PM but indicated 5:00 PM); I had to manually revert to 4:00 PM

- Booted into Win XP Pro Partition 2 - same as occurred with Partition 1 (see immediately above)

- Restarted, checked BIOS, everything OK

- Booted into Ubuntu Edgy, everything OK 

A Win XP Home PC (not dual booting) switched over as expected (i.e., it was not an extra hour forward over and above the expected DST change).

---

### Post by WW on 2007-03-11
qamelian: Thanks, but when I do that, I see nothing labeled "Configuration".  (I am using dapper.)  However, there is check-box followed by "Periodically synchronize clock with Internet servers", followed by a button labeled "Select Servers".  I do not have that checked.

Is there *also* an option somewhere to synchronize at boot, or is the "Time and Date Settings" window the only setting that control network time synchronization?

EDIT: After poking around some more, I am beginning to think that there is no attempt to do a network time sync at boot. Older versions of ubuntu used to do this (and it could be annoying if you weren't on the net).

---

### Post by FLPCGuy on 2007-03-11
> **WW said:**
> I have two computers running dapper. When I booted them today, my desktop had the correct time, but my laptop didn't.  I had to give the command

to get the correct date on the laptop. (Thanks to soundray on #ubuntu.)  (I suspect I could have also used System->Administration->Time and Date, and clicked on "Synchronize Now".)

By the way, there is no tzdata package in dapper.

This could be the issue for me.  While I've selected the two nearest time servers (Texas) and checked 'keep synchronized',  the button to Synchronize Now is grayed out even though I used System Admin Time&Date and entered my password correctly.  Any idea why?  

Could this be an iptables issue?  Do I have to open the TCP/UDP ports for NTP?

---

### Post by FuturePilot on 2007-03-11
On Feisty my time was correct this morning. I'll have to go check Edgy as I haven't booted that today.

---

### Post by FLPCGuy on 2007-03-11
My problem is related to Edgy Networking which has never seen my external modem because there is no /dev/modem.  Thus Networking can't connect via the modem configuration and won't even save all the settings, though it does save /dev/ttyS0 somewhere.   The modem init scripts are hard coded in error.

Since Networking never sees my manual dial-up connection via KPPP it won't install or activate any network related utilities like Firestarter, sync to time server, etc. 

There is a bug report on this [#22119] and a work around.   Perhaps others with the correct localtime settings for DST have network connection awareness issues like mine.

What bugs me is that I can't manually update via ntpdate -u ntp.ubuntu.com or any of a dozen other time servers I've tried.  It never finds a suitable server even though I can ping them all.

---

### Post by vav on 2007-03-12
I have another Edgy installation at work. That computer was on all night, and updated by itself...

So does this thing work automagically only if the computer is on through the DST change date?

---

### Post by AusIV4 on 2007-03-12
I can speak for three machines - one on all night, one sleeping, one off. All three updated. On a fourth machine, which I've not checked yet, I had to adjust the time zone before the time change, because it was apparently set to central time in Mexico instead of the US, and the DST is different there.

---

### Post by WW on 2007-03-12
> **vav said:**
> So does this thing work automagically only if the computer is on through the DST change date?
No; the computer of mine that worked correctly (running dapper) was not on over night.

---

### Post by ofb on 2007-03-12
> **vav said:**
> So does this thing work automagically only if the computer is on through the DST change date?

Nope. A 6.10 over here was on till 4am and did not update.

As yet, I don't see a pattern.

---

### Post by WW on 2007-03-12
Just to see what would happen, I took my laptop (the one that *didn't* automatically update to the correct time yesterday) off the network, set the date back to 11 March 2007 01:55, rebooted, logged in, and watch as it successfully jumped from 1:59 to 3:00.  I then set the time to 01:55 again, turned off the power, waited 10 minutes, and turned it on, and when it booted, it had the 'correct' DST time.

So, why didn't it work the first time?  I don't know.  After it didn't work on Sunday, I ran **tzconfig**, to make sure I had the correct time zone set. (Unfortunately, I didn't check first if it was already set correctly, but it probably was.)  That did not fix the time.  I didn't get the correct time until I ran **sudo /etc/network/if-up.d/ntpdate**.  For all I know, that command had *never* been run on the computer before.

So, whatever I changed after it first failed to correctly make the change to DST, it now appears to work, and I am guessing that in November, it will correctly set the time back to standard.

Unfortunately, I have no definite conclusion to draw from this little experiment.  I still don't know why it didn't work on Sunday.

---

### Post by haiku99 on 2007-03-12
two laptops, one on Dapper, the other on Edgy...both updated OK....

---

### Post by scooper on 2007-03-12
One of two Ubuntu systems did not update.  The one that failed had /etc/localtime as a file, rather than a symlink.  Don't know if that was the cause.

I changed it to a symlink, but still couldn't get the shift to happen after rebooting a few times, interspersed with tzconfig, checking other settings, etc.  I "fixed" it using ntp sync, but the dual boot system is now an hour fast when booted to Windows XP.  Arg!

Any clues, other than wait 3 weeks? :)  I don't want to set the clock each time I boot back to a different OS.

---

### Post by SuSUntu on 2007-03-12
> **scooper said:**
>  ... I changed it to a symlink, but still couldn't get the shift to happen after rebooting a few times, interspersed with tzconfig, checking other settings, etc.  I "fixed" it using ntp sync, but the dual boot system is now an hour fast when booted to Windows XP.  Arg!

Any clues, other than wait 3 weeks? :)  I don't want to set the clock each time I boot back to a different OS.

Something else fishy is going on here if you are saying that once you get the time set correctly in Ubuntu (however you achieve it), XP is messed up every time you boot to it.

XP should have only been messed up (1 hour fast on top of the DST change) the first time you did these things in this order:

- set correct time in Ubuntu (automatically, ntp or otherwise)
- restart PC
- boot into XP (shows time 1 hour fast on top of DST change)

After manually setting XP's  time back one hour, it should stay correct as long as you don't mess with Ubuntu (or XP) time settings anymore.

The reason XP is initially fast by one hour in the above sequence is that at the first boot since the DST switchover, XP adds its DST adjustment to its reading of an already DST-adjusted BIOS clock, the latter having been adjusted when you set Ubuntu's clock. 

Please confirm that you cannot make the time change stick in XP and Ubuntu once you set them both to the correct time (and then make no other changes). Perhaps you only thought the adjustment would be required each time because you were doing so much trial-and-error testing to see if you could make the auto-DST update work in Ubuntu and you lost track of where you were in the reboot-and-check process?

By the way, see my related post #30 in this thread.

Thanks.

---

### Post by helpdeskdan on 2007-03-12
Just turned on yet another edgy machine this morning only to find the wrong time despite the fact that it has all the updates.  No idea why.

---

### Post by scooper on 2007-03-12
> **SuSUntu said:**
> Something else fishy is going on here if you are saying that once you get the time set correctly in Ubuntu (however you achieve it), XP is messed up every time you boot to it.

XP should have only been messed up (1 hour fast on top of the DST change) the first time you did these things in this order:

- set correct time in Ubuntu (automatically, ntp or otherwise)
- restart PC
- boot into XP (shows time 1 hour fast on top of DST change)


Thanks, I didn't actually try setting it in XP.  I expected it to be correct.  I guess I commited a think-o. :)  I'll confirm when I reboot to XP (which I do as little as possible:))

---

### Post by WW on 2007-03-12
A bug report has been filed here: [https://bugs.launchpad.net/ubuntu/+source/tzdata/+bug/91418](https://bugs.launchpad.net/ubuntu/+source/tzdata/+bug/91418)

The title of the bug refers to edgy, and the package the bug is attached to is tzdata, but I suspect the bug isn't actually tied to either (since I am using dapper, which doesn't have the package tzdata).

Add your comments to the bug report, especially if you can provide specific details.

---

### Post by computerwiz3491 on 2007-03-13
I found a fix.

```
sudo gedit  /etc/default/rcS
```

Change the line UTC=no tp UTC=yes

---

### Post by SuSUntu on 2007-03-13
> **computerwiz3491 said:**
> I found a fix.

```
sudo gedit  /etc/default/rcS
```

Change the line UTC=no tp UTC=yes

?

My Ubuntu Edgy installation is deliberately set to UTC=no, and it updated correctly.

For those of us multi-booting with Windows, the "fix" you propose would be worse than the auto-DST changeover not working.

---

### Post by FLPCGuy on 2007-03-13
> **computerwiz3491 said:**
> I found a fix.

```
sudo gedit  /etc/default/rcS
```Change the line UTC=no tp UTC=yes
Interesting.  I assume I'd have to restart to have these changes applied.  

It is implied but not stated throughout this thread that the localtime settings are only applied when a time server update is obtained and the fellow whose time keeps getting set wrong obviously has bad time zone/DST offsets in either XP or etc/localtime.  If a timeserver update is not always obtained automatically upon startup, that would explain why some machines didn't show the change even with the correct offsets.

It is curious that I can't manually update the time with ntpdate -u *timeserver*.
If I pass no server it should use the ones set in my server choices but instead it returns the message 'no servers can be used'.  When I pass a timeserver it delays (polls the server) then responds 'no suitable time server can be found'.

I'm going to reboot and try again now that I've changed the default UTC flag.  Does anyone know of any other files that could be preventing a time server update?

---

### Post by peabody on 2007-03-13
Guys, I'm pretty sure this is not a bug.

I think it would be advantageous for people to report the following information in this thread to see if a pattern can be discerned about what's causing the problem.  Something along these lines:

Ubuntu version: Dapper
Time Zone: PDT
Machine UTC or Localtime?: UTC
Do you sync to an Internet time server?: No
Timezone Setting: America/Los Angeles

Those are my specs and the update went perfectly for me.  I have a hypothesis but I'm not sure if it's correct or not.  My hypothesis is that the people who are experiencing this problem are running localtime and were powered down for the time change.

Here's some evidence to support that claim:

Linux basically handles time in two different ways.  Either you can have your BIOS clock set to UTC (greenwitch median time) and Linux will display the correct time for your timezone by adjusting the UTC time to your timezone.  Or, you can have your BIOS clock set to your localtime.  Linux will still convert this time to UTC internally, but the BIOS clock will reflect your localtime.

The UTC method is the superior method, but it does have its problems: 1) when you look at the time in your BIOS it's not representative of the localtime and 2) windows doesn't treat time in this way, so for dual booters, once you boot into Windows the time will be wrong.  Dual booters have no choice but to keep Linux set to the localtime setting.

Linux also has to handle Day Light's Savings Time differently in each case.  With UTC, it's known that your timezone observes daylight's savings time, so it simply changes its adjustment.  In my case it changes its time adjustment from -8 to -7.  However, for localtime, it has to change the acutal BIOS clock.  There are a lot of problems to this: 1) It better only change it once 2) it had better have a reliable mechanism to figure out it's been changed 3) both Windows and Linux had better not BOTH do it (but they probably will).

Here's a good read for those in doubt: [http://www.linux.com/howtos/Clock-2.shtml](http://www.linux.com/howtos/Clock-2.shtml)

---

### Post by ofb on 2007-03-13
Er... I'm not sure that failing to update to DST shouldn't be considered a bug.

A couple of questions before the poll starts:

"Machine UTC or Localtime?"
What's the quick way to confirm this?

"Do you sync to an Internet time server?"
Do you mean automatically, or manually, or at all?

... and I suppose we should add, "Was the machine on during the changeover?"


But I like your idea, so I set my Edgy back to just before the DST right now, to see what would happen as the hour turned.

Yup. Updated DST fine. Interesting.

Strictly IMHO, if the machine has to be on during a 2am changeover, I do think that's a bug. At least for "average" users that Ubuntu is targeted at.

---

### Post by SuSUntu on 2007-03-13
> **ofb said:**
> Er... I'm not sure that failing to update to DST shouldn't be considered a bug.


Agreed. I'm sure the intention was to have the DST changeover work regardless of:

- UTC=yes or UTC=no
- Mult-booting or not Mult-booting
- Computer on during changeover or off during changeover
- Any combination of the above

> **ofb said:**
> 
A couple of questions before the poll starts:

"Machine UTC or Localtime?"
What's the quick way to confirm this?


Check your /etc/default/rcS for:

UTC=no      #Local Time

or 

UTC=yes    #Self-explanatory

> **ofb said:**
> 
"Do you sync to an Internet time server?"
Do you mean automatically, or manually, or at all?


For the sake of the theory, I beleive it would have to be automatic and it likely should occur at start-up. Otherwise I don't believe such syncing would even have a theoretical impact. 

> **ofb said:**
> 
... and I suppose we should add, "Was the machine on during the changeover?"


And wasn't yours on per your post number #38:

> **ofb said:**
> 
Nope. A 6.10 over here was on till 4am and did not update.

As yet, I don't see a pattern.


> **ofb said:**
> 
But I like your idea, so I set my Edgy back to just before the DST right now, to see what would happen as the hour turned.

Yup. Updated DST fine. Interesting.


If you read WW's post #39, you will see he also experimented (a little more thoroughly) with setting back his machine which did not initially automatically update, and he also confirmed that the machine now updates no matter what the state (on during the changeover or off during the changeover).

Essentially, there seems to be enough information in this thread to suggest that some machines didn't update and which fall outside the criteria of Peabody's theory (including your own machine which was on and didn't update), but it is a good suggestion to be more methodical in narrowing the possibilities down. 

And I think it's safe to call this a bug.

---

### Post by ofb on 2007-03-13
> **SuSUntu said:**
> And wasn't yours on per your post number #38

No, mine was off. That was a local friend's box.

Scratch his from your tally for now - he's since said it's showing correct time, as is his unpatched 98 side. (That shouldn't update for a few weeks.) I either have a misunderstanding for him, or his situation got more interesting. 

mine:

*Ubuntu version:* Edgy
*Time Zone:* PDT
*Machine UTC or Localtime?:* Localtime
*Do you sync to an Internet time server?:* Not automatically
*Timezone Setting:* America/Vancouver

-Dual boot 98se, but that hasn't been used this month.
-Machine was off during changeover.

---

### Post by SteveF on 2007-03-13
Sine I started the thread, I probably should add to it.  Here's my settings when mine did not update:

Ubuntu version: Edgy
Time Zone: EDT
Machine UTC or Localtime?: Localtime
Do you sync to an Internet time server?: Not automatically
Timezone Setting: America/New York
Dual Boot with Windows: Yes

Steve

---

### Post by SuSUntu on 2007-03-13
> **ofb said:**
> No, mine was off. That was a local friend's box.

Scratch his from your tally for now - he's since said it's showing correct time, as is his unpatched 98 side. (That shouldn't update for a few weeks.) I either have a misunderstanding for him, or his situation got more interesting. 



Okay, I see now where you even mentioned that in an earlier post than post #38 (post #11) :

> **ofb said:**
> 
A local friend with the same setup has the same results. His machine was on till 4am, just in case that helps.


No sense in throwing unconfirmed or confused reporting into the mix. It's already muddy enough. :)

My setup won't confirm one way or the other whether Peabody's theory (i.e., error only occurs if machine is off during changeover and set to local time) is correct, but it doesn't dispell it either:

Ubuntu version: Edgy 32-bit
Time Zone: Eastern
Machine UTC or Local Time?: Local Time
Do you sync to an Internet time server?: Not automatically
Timezone Setting: America/New York

- Multi-boot  Ubuntu, 2 Instances of Win XP Pro
- Machine was ON during changeover.
- Update worked

Thanks.

---

### Post by SuSUntu on 2007-03-13
> **SteveF said:**
> Sine I started the thread, I probably should add to it.  Here's my settings when mine did not update:

Ubuntu version: Edgy
Time Zone: EDT
Machine UTC or Localtime?: Localtime
Do you sync to an Internet time server?: Not automatically
Timezone Setting: America/New York
Dual Boot with Windows: Yes

Steve

Since part of Peabody's theory is that the machine needed to be off and on local time, you should probably add that as a line in your specs. It seems from your first post that your PC was off ... is that correct?

---

### Post by doublecheese210 on 2007-03-13
Mine worked great, didn't even have to think about it

Dapper AMD 64

---

### Post by WW on 2007-03-13
My computer that didn't automatically convert to DST is running Dapper, and has UTC=no.  It also dual boots, with Win2000.  But, as I explained earlier, when I experimented with setting the clock back after running tzconfig and after doing a network time sync just once, it *worked* whether or not the power was on at 02:00. As far as I know, the only difference  between the first time (when it didn't work) and the experiments (which all worked) is that I ran tzconfig and ntpdate before doing the experiments.  I don't recall if these had *ever* been run before then.  The Ubuntu  installation was originally a fresh Breezy install,  and was later upgraded to Dapper.

---

### Post by FuturePilot on 2007-03-13
Is everyone here using the U.S. repos? Maybe I'm wrong but maybe the package regarding the DST new start and end dates was only released through the U.S. repos. Like I said I'm just guessing, could be completely wrong. I have a computer dual booting Windows and Dapper, the time changed fine on both. I have another dual booting Edgy and Feisty, both updated no problem.

---

### Post by Benchrest on 2007-03-13
FAILED
Edgy 
Localtime (dual boot)
sync to server
CDT

---

### Post by peabody on 2007-03-13
I think my theory has been pretty much confirmed at this point.  Everyone reporting trouble has a localtime setting.  Just in case none of you read the link I posted (which seems to be most people) the writer of that article stated that when Linux is set to localtime and it is off during the changeover Linux won't update the local clock.  Even if it's on, when the changeover happens, I don't think it actually changes the BIOS, it simply changes its internal UTC setting which will of course be reset upon reboot.

The reason for this policy is simple: it's implied that anyone using a localtime setting is a dual booter, in which case it's expected for Windows to perform the change.  This helps prevent a double change, which many would consider more troublesome and jarring.

Some people will protest and say that the policy is stupid.  It's not that easy a problem.  How do you get two operating systems that don't know about each other to cooperate in regards to a BIOS setting?  You can't do it easily.  Linux errs on the side of likelihood here; if the system's set to localtime, it's assumed some other operating system will be performing the BIOS clock update.

I will admit that it is a usability problem, but not a bug, since it's a documented feature of Linux.  I propose that something like a daylight savings control panel be added so users can configure how they would like Linux to behave in regards to daylight savings time.

For those not dual booting, now would be a great time to consider running your BIOS clock at UTC.

---

### Post by peabody on 2007-03-13
> **FuturePilot said:**
> Is everyone here using the U.S. repos? Maybe I'm wrong but maybe the package regarding the DST new start and end dates was only released through the U.S. repos...

Correct me if I'm wrong but I thought the US was one of the only places that observed DST?  If I'm wrong about that I'd be curious to know what other countries do.  I'd heard other countries had considered using DST.

---

### Post by SuSUntu on 2007-03-13
> **peabody said:**
> I think my theory has been pretty much confirmed at this point.  Everyone reporting trouble has a localtime setting.  Just in case none of you read the link I posted (which seems to be most people) the writer of that article stated that when Linux is set to localtime and it is off during the changeover Linux won't update the local clock.  Even if it's on, when the changeover happens, I don't think it actually changes the BIOS, it simply changes its internal UTC setting which will of course be reset upon reboot.

The reason for this policy is simple: it's implied that anyone using a localtime setting is a dual booter, in which case it's expected for Windows to perform the change.  This helps prevent a double change, which many would consider more troublesome and jarring.


Well, your theory is not confirmed with only a few posts. All it takes is for one person to report that the update failed while the computer was on. After all, your original criteria was that the PC had to be **off** and on local time. I would say it is too early to conclude, though, I am still open.

As far as your theory that Ubuntu was supposed to be leaving the changeover to Windows in a multi-boot environment, perhaps you should spend some time actually reading the testimonials here in this thread instead questioning whether we've read links you've posted. :)

I wrote more than one post here describing what happened with my set-up, and basically Ubuntu did change the BIOS and it did cause the Windows clocks to be 1-hour fast. I won't bother to go into detail again ... the posts are available for you to read.

We respect your theory, but maybe slow down a bit and make sure you understand fully all of the testimonials here before you claim to have unequivocally solved the mystery. :)

---

### Post by ofb on 2007-03-13
> **peabody said:**
>  I don't think it actually changes the BIOS, it simply changes its internal UTC setting which will of course be reset upon reboot.

Well, actually, no: I booted my 98 side and it's showing the correct time. It should have been an hour slow. 

98 doesn't do DST for a few more weeks. Also a dialog pops up to tell you it is doing it. So my UTC must have been changed by Ubuntu.

Which is not what I expected because I did read your very good link. Looks like we've got a bit more mystery left I'm afraid.

---

### Post by peabody on 2007-03-13
> **SuSUntu said:**
> Well, your theory is not confirmed with only a few posts. All it takes is for one person to report that the update failed while the computer was on. After all, your original criteria was that the PC had to be **off** and on local time. I would say it is too early to conclude, though, I am still open.

As far as your theory that Ubuntu was supposed to be leaving the changeover to Windows in a multi-boot environment, perhaps you should spend some time actually reading the testimonials here in this thread instead questioning whether we've read links you've posted. :)

I wrote more than one post here describing what happened with my set-up, and basically Ubuntu did change the BIOS and it did cause the Windows clocks to be 1-hour fast. I won't bother to go into detail again ... the posts are available for you to read.

We respect your theory, but maybe slow down a bit and make sure you understand fully all of the testimonials here before you claim to have unequivocally solved the mystery. :)

I apologize if that's the case.  I may have misunderstood the article; he mentioned that as long as Linux is on during the changeover everything will be fine.  My assumption was that Linux changed its UTC settings internally but not the BIOS clock.  Looks like I'm wrong about that.

However, I still might be right regarding those people who had their machine off during the change over.  Also, after having read all of your previous posts you do mention that you haven't synced to a time server.  I'd just like to confirm that you don't run ntpd, nor did you sync to a time server after the change over.  I'm guessing you haven't, but just to be sure; Manually syncing will update the BIOS clock, while not syncing shouldn't do anything to it.  I'm just trying to see what other light I can shed on the mystery.  Sorry if I come off as arrogant.

---

### Post by SuSUntu on 2007-03-14
> **peabody said:**
> I apologize if that's the case.


None necessary.

> **peabody said:**
> 
Also, after having read all of your previous posts you do mention that you haven't synced to a time server.  I'd just like to confirm that you don't run ntpd, nor did you sync to a time server after the change over.  I'm guessing you haven't, but just to be sure; Manually syncing will update the BIOS clock, while not syncing shouldn't do anything to it.  I'm just trying to see what other light I can shed on the mystery.


I did not sync with a time server using any **ntp** tools (or otherwise) prior to some investigating I conducted this morning. Here are more details about that:

- **ntp** is not installed on this PC (as an aside, this will result in a message saying that "NTP support is not installed" when attempting to set your PC to "keep clock synchronized with internet servers" in the Time & Date dialog. The dialog gives you the option to install ntp if you desire.

- **ntpdate**, normally a "component" of ntp, is installed by default when Ubuntu is installed, and it has several files related to it in /etc/*. The code in one of those files, /etc/network/if-up.d/ntpdate, directs ntpdate to run when the network becomes available (presumably during boot); however, I could find no evidence by examining logs or tracing the code back through various files that ntpdate actually ever runs (it also is absent from the list of services when sysv-rc-conf is run from the command line). As a final step, just to be sure for purposes of this discussion, I set my clock incorrectly (- 10 minutes) and then rebooted. **The clock was not corrected, so I can confirm that ntpdate is not run during boot.** 

**NOTE**: I was able to update the clock after login by issuing this command:

```

sudo ntpdate -u ntp.ubuntu.com

```

I chose the "-u" option and the server, ntp.ubuntu.com, because they are specified in **/etc/default/ntpdate**, and I wanted to be clear that these could be used successfully to update the clock.

> **peabody said:**
> 
Sorry if I come off as arrogant.


I'll just call it **frustration** from trying to get to the bottom of this issue, which is understandable. :)

---

### Post by peabody on 2007-03-14
Okay, that confirms that it should have worked if Ubuntu was on during the changeover.

I thought I'd construct a birds eye view of the thread:

SteveF:
Machine was set to localtime and machine was off during the changeover.  Machine did not update upon reboot.

alanbe:
Didn't update automatically, no word on his circumstances

_Agraja_:
Machine was off during the changeover.  No update.

vav:
Machine was off during the changeover.  No update.

helpdeskdan:
Machine was off during the changeover.  No update.

DarkN00b:
Update occured, no word on circumstances.

ofb:
Machine was set to localtime, machine was off during the changeover.  No update.

FLPCGuy:
No update.  Hasn't confirmed if machine was on or off during the changeover.

WW:
Two machines were off during changeover and did update.  Laptop did not update.  Do not know the circumstances of the machines.  WW set his laptop back in time and watched the update, then tried it again, but kept the machine off 'til 5 minutes after changeover.  Update occured **This stands as the biggest anomoly so far**

wpshooter:
4 machines updated, but all were set to sync to an Internet time server.

milehigh:
Both machines update and were off during the changeover.  Don't have any other info.

tagra123:
7 machines worked, but were all set to sync to time servers.

Pikestaff:
Machine update (sounds like it was on during the changeover?).  Other info unknown.

SuSUntu:
Machine was on and set to localtime.  Update occured.

ButteBlues:
Machine updated, but was set to sync to Internet time servers.

qamelian:
Machine was off during the changeover and updated correctly.  Machine did not sync to time servers.

scooper:
Did not update.  Don't know much about the circumstances.

computerwiz3491:
changed his machine over to UTC, fixed everything on the spot according to him/her.

Okay, I'm about to retract my hypothesis on the basis of WW's experiments.  However, the article I linked to early said something to the effect that DST wouldn't be correct if Linux was a) set to localtime and b) down between the changeover, which is what the basis for my original hypothesis was.  So, there's one of three possibilities...

1) The article's bunk and Linux time doesn't work that way anymore or...
2) The BIOS clock is updated at a different time than 2:00 A.M. sharp.  This doesn't affect Linux's internal UTC clock.
3) Linux updates to DST on reboot if it's started early enough after the changeover

Point 2 seems highly unlikely, but it's a possibility.  Point 3 is what I'm leaning toward.  But point 1 could be correct.

Any enlightened souls have the knowledge to set the record straight?  This has been getting confusing.

About the only thing I've been able to say for sure is that anyone running on UTC had no problems.

---

### Post by SteveF on 2007-03-14
> **SuSUntu said:**
> Since part of Peabody's theory is that the machine needed to be off and on local time, you should probably add that as a line in your specs. It seems from your first post that your PC was off ... is that correct?

You are correct, I forgot to include that.

My machine was off during the changeover.

Steve

---

### Post by WW on 2007-03-14
peabody: Thanks for your explanation a few posts back, and thanks for the link. Both have been helpful.

It turns out that my "experiments" were flawed.  For one thing, the **date** command does not change the hardware clock.  More importantly, when I did the experiment in which the change to DST occurred while the power was off, I only waited until the computer's time would have been, say, 2:05 AM.  But 2:05 AM on March 11 is not a valid time, and so (I am guessing here) the system was smart enough to realize that it needed to advance the clock by one hour.

I just did a new experiment, in which I set the clock with the following commands
> sudo date -s "11 March 2007 01:55" ; sudo hwclock --systohc
and then turned the computer off *for an hour and ten minutes*.  When I rebooted, the computer time was 03:05.  If the computer had correctly made the switch to DST, the time should have been 04:05.

So, it turns out I *can* reproduce the failure to switch to DST.  I suspect peabody's explanation is correct.

---

### Post by FLPCGuy on 2007-03-14
I think you may be on the right track investigating the time server angle. 

I have 6.10 Edgy America/NY Eastern time
All software updates have been installed except OpenOfc (via dial-up only)
 My machine has UTC set to NO in /etc/default/rcS so the BIOS is on localtime
Changing UTC to yes rebooting did not update the time anyway, I set it back.
I had the 2007 DST settings in /etc/localtime but got another update yesterday
I don't see any significant changes to this binary file (ran this command)
sudo zdump -v /etc/localtime |grep 2007
/etc/localtime  Sun Mar 11 06:59:59 2007 UTC = Sun Mar 11 01:59:59 2007 EST isdst=0 gmtoff=-18000
/etc/localtime  Sun Mar 11 07:00:00 2007 UTC = Sun Mar 11 03:00:00 2007 EDT isdst=1 gmtoff=-14400
/etc/localtime  Sun Nov  4 05:59:59 2007 UTC = Sun Nov  4 01:59:59 2007 EDT isdst=1 gmtoff=-14400
/etc/localtime  Sun Nov  4 06:00:00 2007 UTC = Sun Nov  4 01:00:00 2007 EST isdst=0 gmtoff=-18000

It is a dual boot WinME setup but I have not booted to Windows so far in 2007
It was OFF during DST changeover and did not change the time when booted
NTP, ntp-simple ntpdate are installed but sync now button is always disabled
I can't update from any of the listed time servers I chose in time & date or manually...similar errors
sudo ntpdate -u ntp.ubuntu.com
14 Mar 13:23:51 ntpdate[7118]: no server suitable for synchronization found
sudo ntpdate -u ntp.tmc.edu
14 Mar 13:26:56 ntpdate[7198]: no server suitable for synchronization found

It seems to me that the localtime offsets are applied against either a time server or the local BIOS clock if no timeserver is available. It would make no sense to change the BIOS clock if it was the only time source, but simply the Ubuntu local time display IF UTC is yes.  Is that your reasoning too?  

I believe DST would work correctly for me if I could update from a time server.

---

### Post by jeffathehutt on 2007-03-14
Just in case it will help...

Running fully up-to-date Dapper
UTC=yes (Dapper is the only OS installed)
Timezone: America/Chicago
No automatic sync with timeservers
Computer was turned off during changeover
Clock was correctly set to DST as expected once I booted up the next morning.

---

### Post by ancientconsole on 2007-03-15
I have a somewhat different problem than what everyone else seems to be having.  I have three Ubuntu boxes.  Two of them are on PCs that dual boot with at least Windows XP.  Those two work fine.  Just FYI, they were turned off during the switch.  I booted into Windows first which changed the time and then booted into Ubuntu and all was well.  The versions are Dapper-32bit & Edgy-64bit.

My third box is Xubuntu 6.10 on an iMac G3.  It has the latest updates.
Local time actually is: Thu Mar 15 20:02:09 PDT 2007
UTC actually is:        Fri Mar 16 03:02:09 UTC 2007
This is what OS X reports.
Xubuntu reports both of those times as 1 hour behind.  It does say the time is PDT though. zdump -v gives the correct dates for the switch as well.  If I use ntpdate, the correct time is updated.  

I did a test and set the clock to 5 minutes before the switch and it went from 1am to 3am as it should, yet this issue still exists.

Supposedly Xubuntu is set to update the time automatically.  I tried to change the server settings yet it would not update /etc/ntp.conf.  I updated /etc/ntp.conf manually but I don't know if ntpd actually works.  I noticed that regardless of whether or not update from time servers automatically is checked or not, there will be udp packets sent to 82.211.81.145 on port 123.  Which is ntp.ubuntu.com.

I have OS X set to update the time automatically and it actually does.  If I turn that off and set the time correctly in Xubuntu and then reboot to OS X, the time in OS X is 1 hour ahead.

If I set the correct time in Xubuntu and then reboot back to Xubuntu, the correct time is shown.  Likewise for OS X, even with ntp disabled.

Lastly, when I set Xubuntu's time correctly, this is what I get for hwclock:
```
$ hwclock
Thu 15 Mar 2007 07:02:25 PM PDT -1.401733 seconds
```

```
$ hwclock --utc
Thu 15 Mar 2007 12:03:33 PM PDT -0.115504 seconds
```

:confused:

---

### Post by Gorbachev on 2007-03-15
I recommend to anyone to just change the time in your BIOS, this will automatically change it for all (at least most) operating systems upon boot and will not change until you change it in BIOS.

---

### Post by SuSUntu on 2007-03-16
> **ancientconsole said:**
> I have a somewhat different problem than what everyone else seems to be having.  I have three Ubuntu boxes.  Two of them are on PCs that dual boot with at least Windows XP.  Those two work fine.  Just FYI, they were turned off during the switch.  I booted into Windows first which changed the time and then booted into Ubuntu and all was well.  The versions are Dapper-32bit & Edgy-64bit.


I presume that by 'all was well', you mean your Ubuntu installations' clocks were set correctly (without needing any manual adjustment) after having first booted to Windows XP.

If that is what you mean, then actually Windows did what it was supposed to do, but Ubuntu failed to perform its changeover routine. If Ubuntu had actually done as it should regarding DST, your Ubuntu clocks would have been 1 hour fast, over and above the correct DST time.

I haven't had time to adequately review the rest of your post, so no comment for now. :)

---

### Post by peabody on 2007-03-16
> **SuSUntu said:**
> 
If that is what you mean, then actually Windows did what it was supposed to do, but Ubuntu failed to perform its changeover routine. If Ubuntu had actually done as it should regarding DST, your Ubuntu clocks would have been 1 hour fast, over and above the correct DST time.


Actually, if what I read in that article I posted is correct, I think this is how Ubuntu (and all Linux) works in regards to DST:

BIOS Clock UTC?
Yes -> offset done internally, no changes necessary to BIOS clock, done.
No -> then time is localtime...next question...

Machine on during changeover?
Yes -> put BIOS clock one hour ahead.
No -> Do nothing to BIOS clock, assume other operating system did the trick.

I'm pretty sure this is the way it works.

---

### Post by SuSUntu on 2007-03-16
> **peabody said:**
> 

I'm pretty sure this is the way it works.

I should have definitely worded my post better than I did.

Essentially, ancientconsole stated that his problem was different than what others have experienced. But I read it as being the same:

**Ubuntu did not run / apply any DST routines**

To elaborate (though I'm sure you understand):

- In cases where Ubuntu was booted first in a multi-boot environment, **no DST routine was run**, resulting in a clock slow by one hour relative to the new DST time. In this case, to most users, it is obvious that something didn't work as might have been expected (thus the spawning of this thread).

- In the case where Ubuntu was booted second in a multi-boot environment, **no DST routine was run**, resulting in a clock correctly set relative to the new DST time (again, this statement is tentative depending on what ancientconsole confirms). In this case, to any user without knowledge of what we've all been discussing here, there may have been a false sense that Ubuntu had run its DST routine.  

So, our difference (mine and yours) only exists in whether we see not running the DST routine as a "failure" or a deliberate inaction (as per your reading of the article you posted).

If we have all agreed that it is deliberate at this point, then the thread can be "closed" as resolved. And I'm not denying that perhaps it can be. :)

---

### Post by SuSUntu on 2007-03-16
Since I had a little extra time, I thought I'd elaborate further on "failure" vs. "deliberate inaction". Everything that follows is strictly an opinion and takes as givens Peabody's very likely premise:

- that local-time / multi-booting and PC-OFF-during-changeover were the determining factors for those whose DST was not set automatically in Ubuntu; and   
- that the above was intentional / de rigueur for Linux generally and Ubuntu specifically.

Some of my opinion parallels common concerns / critiques outlined in the article posted by Peabody, but it is more specific in offering an alternative for Ubuntu **without regard for what other distributions may or may not do (or may or may not have done)**. Heresy, I know. But, here we go.

-----

If Ubuntu developers:

a) assume that a PC set to local time is in a multi-boot environment; and

b) defer / subordinate Ubuntu's DST routine to another OS; and

c) assume (when the PC is off during the changeover) that another OS will be booted first; and

d) assume that the other OS has support for automatically changing DST or otherwise setting time;


then Ubuntu should be designed to do the following:


1) detect 'UTC=no', and if TRUE, run the 'ntpdate' scripts (which test for network 'up' status) during boot. As it stands now, 'ntpdate' was installed by default, yet has been left idle on the HDD when it could actually be serving a purpose (here, I assume that the 'ntpdate' scripts in Edgy are inactive universally just as I have determined them to be for my own installation); and / or  

2) use the notification daemon to inform the user that: a) local time was detected; b) the DST changeover period has transpired but the new time may not have been applied to the PC; c) adjustment of the clock may be necessary; or

3) simply let the DST routine run in all cases regardless of other factors.

Handling the DST changeover via Items 1 & 2 above likely would have resulted in a congratulatory thread on this forum more geared toward confirming things worked as expected (assuming no other bugs).

However, without applying the above "safeguards" (Items 1 & 2) to the **overly broad assumptions** that may have been designed into the OS, then Ubuntu should simply run its DST routines without special regard to local time, multi-booting, or ON /OFF state of the machine during the changeover (as per Item 3). It seems to me any resulting clock errors due to the latter are more obvious in nature to the user who encounters them (as opposed to Ubuntu's use of different procedures depending on local-time settings, etc.). Here is my take on how this thread would have gone if the DST routine ran in all situations (and left 'ntpdate' dormant, as currently seems to be the case):

[quote=AnyOP]Windoze sux. My Ubuntu installation handled DST, but when I booted to Windoze, it was 1 hour fast. LOL
[/quote]

[quote=AnyOtherPoster]Nah. It was just the opposite for me. My Windows worked, but when I booted into Ubuntu it was 1 hour fast.
[/quote]

[quote=OddManOut]Hmm. Everything's fine for me, but I don't dual boot.
[/quote]

[quote=GuyWithAllTheAnswers]Ubuntu and Windows are both fine. It's just that when UTC=no, the BIOS gets changed by whichever OS is run first, therefore the second (or last) booted OS's clock will be fast because it adds its DST routine on top of the already-updated BIOS time.
[/quote]

[quote=Everybody]Oh. OK. Cool. Thanks
[/quote]

So, the way in which Ubuntu handled the changeover was a mixed bag: good for some, a failure for others and confusing to most. Even if it was deliberate.

---

### Post by nocturn on 2007-03-16
> **wpshooter said:**
> Yes, I run mine 24/7.

I wonder if the computer needed to be actually running for the change to take place **AUTOMATICALLY **?

Thanks for your reply.

No, it does not.  The timezone offset is calculated from UTC everytime you ask/display the time...

I cannot explain this, did anyone file a bugreport?

Note, I'm not in the US, so I cannot check this issue.

---

### Post by nocturn on 2007-03-16
> **qamelian said:**
> Right-click on your clock and select Adjust Date & Time. If Configuration is set to manual, it does not do a network time sync.

Ubuntu has ntpdate running against ntp.ubuntu.com automatically AT BOOT.  setting it to sync makes ntpd run constantly.

Note that NTP is based on UTC, the timezone offset is calculated locally.

---

### Post by nocturn on 2007-03-16
> **SuSUntu said:**
> Something else fishy is going on here if you are saying that once you get the time set correctly in Ubuntu (however you achieve it), XP is messed up every time you boot to it.

XP should have only been messed up (1 hour fast on top of the DST change) the first time you did these things in this order:

- set correct time in Ubuntu (automatically, ntp or otherwise)
- restart PC
- boot into XP (shows time 1 hour fast on top of DST change)

After manually setting XP's  time back one hour, it should stay correct as long as you don't mess with Ubuntu (or XP) time settings anymore.

This is normal, Linux keeps your hardware clock on UTC anc calculates the offset on a per user basis (your user can be in PST, mine in CEST, which is neat on international servers).

Windows however does not do this, it updates the hardware clock on timezone changes.

So, when dual booting, you need to tell Linux that the hardware clock is in local time instead of the expected UTC.

---

### Post by nocturn on 2007-03-16
> **computerwiz3491 said:**
> I found a fix.

```
sudo gedit  /etc/default/rcS
```

Change the line UTC=no tp UTC=yes

UTC= no is only for people that dual boot with windows.  Never make this setting on a Linux only system!

Which brings me to the question, is anyone having this problem on a computer without windows?  Does it occur even though tzinfo is corrected?

---

### Post by nocturn on 2007-03-16
> **ofb said:**
> if the machine has to be on during a 2am changeover, I do think that's a bug. At least for "average" users that Ubuntu is targeted at.

It does not have to be on, being on or off should not affect it in any way.  If the changeover doesn't occur offline, it's a bug.

---

### Post by nocturn on 2007-03-16
> **peabody said:**
> 
The reason for this policy is simple: it's implied that anyone using a localtime setting is a dual booter, in which case it's expected for Windows to perform the change.  This helps prevent a double change, which many would consider more troublesome and jarring.


I suspected this was the problem all along and this policy makes sense.
If they were to reverse it and update the BIOS clock when on local time, it would mean XP would update it too and your clock would always be incorrect. 

It wouldn't matter if the computer was off during the changeover, the first booted OS would do the change and the second would do it again always resulting in a faulty clock.

The root of the problem actually is the horrific way in which windows deals with time....

---

### Post by SuSUntu on 2007-03-16
> **nocturn said:**
> This is normal, Linux keeps your hardware clock on UTC anc calculates the offset on a per user basis (your user can be in PST, mine in CEST, which is neat on international servers).

Windows however does not do this, it updates the hardware clock on timezone changes.

So, when dual booting, you need to tell Linux that the hardware clock is in local time instead of the expected UTC.

I suspect, based on your last six posts, that something is wrong with your browser. It doesn't seem to be displaying threads in their entirety. :)

---

### Post by nocturn on 2007-03-16
> **SuSUntu said:**
> 
**Ubuntu did not run / apply any DST routines**



Just want to point out that Unix systems do not "run" anything timezone related.
The calculated the offset of your timezone defined you your locale to the internal Unix time (seconds since the epoch).

Unix time is completely linear (except for UTC leap seconds).

The problem arises when it has to live on the same system as an OS that has no linear time (Windows).

---

### Post by nocturn on 2007-03-16
> **SuSUntu said:**
> I suspect, based on your last six posts, that something is wrong with your browser. It doesn't seem to be displaying threads in their entirety. :)

Sorry, I often come in late on threads reading them from start and replying in the meantime.

---

### Post by ofb on 2007-03-16
> **nocturn said:**
> The root of the problem actually is the horrific way in which windows deals with time....

Oh dear. I would like to get this clear for a simpleton like myself:

A pure Ubuntu install should have UTC=yes to avoid all this trouble.

An Ubuntu/Win install should have UTC=no.

Dual-boot Ubuntu applies DST to its system clock, not the hardware clock. Windows applies DST to the hardware clock.

Dual-boot Ubuntu applies DST to itself if it is on during the changeover. If it is off, DST is not applied.

This is because Windows applies DST to the hardware clock. It is hoped Win gets booted first after changeover. If not, Ubuntu will be out an hour until Win is booted and changes the hardware clock.

This isn't ideal, but is a compromise choice because the other option is Ubuntu also applies DST to the hardware clock, messing things worse after both have booted.


... which makes some sense, but I've got the little detail that I'm Ubuntu/98, UTC=no. My machine was off during changeover, so I updated time in Ubuntu's GUI. 98 had not been booted for days, and it doesn't do DST for a while yet anyway because it's on the old system. 

Then I booted 98 to have a look, and to turn off its DST feature so things don't get bounced in a few weeks. And it shows the correct time. It should be an hour slow. Shouldn't it?

... and my logic must be wrong anyway. If Ubuntu had been on and applied DST to the system clock, it would still get bounced when Win updates the hardware clock after. No?

Trying to keep up with you lads is doing wonders for my coffee consumption, I must say. Plus about half a pack of smokes and two tylenol. All appreciated, and I thank you for the trouble.

---

### Post by ancientconsole on 2007-03-16
Let me clarify my previous post since there was a question about my PCs that dual boot.

On both, UTC=no.  They were off during the time change and I booted into Windows and the time changed forward one hour.  Next I booted into Fedora and the time was what it was supposed to be (remember I said they are at least dual boot)  Next I booted into Vista and the clock was set forward yet another hour, I changed it back in the bios and rebooted to Ubuntu where the time was correct.

On my other PC, I booted into Windows first which changed the time forward 1 hour and then rebooted to Ubuntu which didn't change the time luckily, so it was set correctly.

I have all operating systems on all my PCs set to update the time automatically with ntp so that could have something to do with it.

The time on my iMac, however, is still what I cannot figure out.

Lastly, UTC=no on my iMac as well!! :confused:   Back in Standard time, the clocks in OS X and Xubuntu were correct.  I always thought that the RTCs in Macs were set to UTC and the system clock was just displayed at the appropriate offset.  It seems not?

---

### Post by qamelian on 2007-03-16
> **peabody said:**
> I think my theory has been pretty much confirmed at this point.  Everyone reporting trouble has a localtime setting.  Just in case none of you read the link I posted (which seems to be most people) the writer of that article stated that when Linux is set to localtime and it is off during the changeover Linux won't update the local clock.  Even if it's on, when the changeover happens, I don't think it actually changes the BIOS, it simply changes its internal UTC setting which will of course be reset upon reboot.
Well, both my computers (one Edgy, one Feisty) are set to localtime and both were off, but they both updated for DST just fine.

---

### Post by peabody on 2007-03-16
I think they're might be some confusion on what ntpd actually does (even from myself).  From research, it looks like ntpd only adjusts time within a small radius:

[http://en.wikipedia.org/wiki/Ntpd](http://en.wikipedia.org/wiki/Ntpd)

In that case it seems running ntpd wouldn't have much of an effect on this problem either way.

---

### Post by Benchrest on 2007-03-16
My laptop did not work that is on localtime. It was off during the time period. UTC=no. Yet the bios clock was changed after I manually changed the time in Edgy. When I booted win 98se it had the changed time so the bios must have been updated. In anycase, it seems to me the time change should have worked whether you are UTC or Localtime as both are valid options.

---

### Post by SuSUntu on 2007-03-17
> **peabody said:**
> I think they're might be some confusion on what ntpd actually does (even from myself).  From research, it looks like ntpd only adjusts time within a small radius:

[http://en.wikipedia.org/wiki/Ntpd](http://en.wikipedia.org/wiki/Ntpd)

In that case it seems running ntpd wouldn't have much of an effect on this problem either way.

I'm not certain there's enough interest in this topic anymore for people to want to try to dig out of the setback caused by yesterday morning's unfortunate drive-by, post-just-to-increase-your-post-count-quality-be-damned extravaganza (no names mentioned), but I have some thoughts on your post that should be easy enough to convey without having to dig out of too much heaped-on confusion, so I'll give it a shot. 

Anyway, I think if we are going to discuss time synchronization in the context of the DST issue, the focus should be on 'ntpdate' instead of 'ntpd'. Here are a few of my reasons:

1) 'ntpdate' is installed by default in Ubuntu [Edgy] and there appears to be intent for it to run at boot; on the other hand 'ntpd' is not installed by default;
2) there are many reports of 'ntpdate' not running at boot-time though it appears it should; my own experience is the same, as was noted in a previous post:

> **SuSUntu Post #65]

<snip>

- ntpdate, normally a "component" of ntp, is installed by default when Ubuntu is installed, and it has several files related to it in /etc/*. The code in one of those files, /etc/network/if-up.d/ntpdate, directs ntpdate to run when the network becomes available (presumably during boot) said:**
> 

3) while you correctly state that 'ntpd' has a maximum adjustment that it can apply (without an additional parameter being set):

[quote=ntpd man page]
-g

 Normally, ntpd exits with a message to the system log if the offset exceeds the panic threshold, which is 1000 s by default. This option allows the time to be set to any value without restriction; however, this can happen only once. If the threshold is exceeded after that, ntpd will exit with a message to the system log. This option can be used with the -q and -x options. See the tinker command for other options. 


it appears that 'ntpdate' has no such restriction. To test this, run:

```

sudo su

```

and enter your password. Then set your clock back any number of hours (or even set your calendar back x number of days). Finally, run:

```

/usr/sbin/ntpdate -b -s -u ntp.ubuntu.com

```

The '-s' option diverts logging to Syslog from the terminal, so you should be able to see something like this in the log after the command runs:

```

Mar 16 23:48:29 user@comp ntpdate[15420]: step time server 82.211.81.145 offset 79203.074760 sec

```

As is evident, the offset is 79203.074760 seconds, or ~ 22 hours, and it was successfully applied to the clock.

The command '/usr/sbin/ntpdate -b -s -u ntp.ubuntu.com' does not include any options that force 'ntpdate' to perform large offset adjustments, yet it will perform them.

[b]--------
NOTE:[/b]
Though 'ntpdate' does not appear to have limitations on the size of the error it can correct, 'sudo' does have issues related to large clock-settings changes. If you attempt to run 'sudo' after setting the clock back more than a few minutes (exact minutes unknown by me, but minimal testing places it around 10 - 20 min., and certainly less than 1 hour), you will get the following error:

timestamp too far in the future

Cause:
'sudo' uses a time stamp in directory /var/run/sudo/<user>. If that timestamp is too far in the future (due to incorrect time settings either now or when the file was created), then sudo access is disallowed. That also means that you can't use sudo to reset the clock or delete that file.
Source: [http://wil.cs.caltech.edu/wiki/pmwiki.php?n=Linux.Sudo](http://wil.cs.caltech.edu/wiki/pmwiki.php?n=Linux.Sudo)

Thus, in order to test 'ntpdate' against a large clock "error", it is important to 'sudo su' to root before setting the clock error and running 'ntupdate' to make the correction. You will avoid the 'sudo' issue by doing so.
**--------**

**Additional Comments**

As I noted briefly in an earlier post, two main scripts associated with 'ntpdate' that are installed on my Ubuntu Edgy set-up are:

- /etc/network/if-up.d/ntpdate 
- /etc/init.d/networking

If you manually introduce a clock error (use a small one just to avoid the 'sudo' time stamp issue) and then run either of these commands:

```

sudo /etc/network/if-up.d/ntpdate 

```

or

```

sudo /etc/init.d/networking restart

```

you will see the clock correction successfully applied. By the way, I found a similarly-themed thread here:

[http://ubuntuforums.org/showthread.php?t=366041&highlight=ntpdate](http://ubuntuforums.org/showthread.php?t=366041&highlight=ntpdate)

but I could not reproduce Sodki's results (he concludes that 'ntpdate' runs at boot but something reverses the initial time correction) in Post #4 of that thread. My tests on my set-up lead me to conclude that 'ntpdate' never runs at all during the boot process.

If you are even more inquisitive, you may want to run 'strace' against the above commands (the sample commands below send the output to a text file on the user's Desktop):  

```

sudo strace -f -o ~/Desktop/strace_ntpdate.txt /etc/network/if-up.d/ntpdate   

```

```

sudo strace -f -o ~/Desktop/strace_networking.txt /etc/init.d/networking restart

```

If you dig through that output, you'll find the line:

```

13720 execve("/usr/sbin/ntpdate", [**"/usr/sbin/ntpdate", "-b", "-s", "-u", "ntp.ubuntu.com"**], [/* 33 vars */]) = 0

```

Does the highlighted text look familiar? It is the same command I used to test the abilities of 'ntpdate' to correct large clock errors.

Anyway, Peabody (or anyone else), if you have a chance, could you attempt to verify how your installation handles 'ntpdate' during the boot process.

One of the biggest hurdles in trying to maintain cohesion in this thread is balancing the discussion of **what should be occurring** with **what is actually occurring** on a given Ubuntu PC and then being able to distinguish between the two amongst all the static. I've already proven to myself with reasonable certainty that 'ntpdate' doesn't run at boot-time on my PC, but I'm still unclear whether it actually is supposed to run by default (my thought is it was intended to do so), and if so, how common are occurrences where it fails to run.

Thanks.

---

### Post by peabody on 2007-03-17
Wow, long post.  Informative.  I was aware of the ntpdate command, just didn't realize it ran at boot.  I'm pressed for time, I'll post again as soon as I can verify stuff in my own setup.

---

### Post by SuSUntu on 2007-03-17
> **peabody said:**
> Wow, long post.  Informative.  I was aware of the ntpdate command, just didn't realize it ran at boot.  I'm pressed for time, I'll post again as soon as I can verify stuff in my own setup.

Thanks.

By the way, I forgot to mention that I tested with UTC=no and UTC=yes with the same results.

---

### Post by Chazall1 on 2007-03-19
I have Edgy 6.10 on one HD and Win XP on a separate HD. I was Dual Booting on a simgle HD. I was reading the posts and the Time change took about 3 days to take effect. IWhen I run the
sudo zdump -v /etc/localtime | grep 2007 I get the same output on the 1st page. My XP had the correct  time first and I changed my time manually in Edgy, Adjust Date & Time and selected Synchronize Now and set my time up by one hour. In the past couple of days If I boot back into Edgy, I get a forced Fsck on /root, "Superblock last write time is in the future" and it will be fixed.  I would have to re-boot back into Edgy
I ran
sudo /etc/network/if-up.d/ntpdate 
Mar 19 10:17:49 localhost ntpdate[6447]: step time server 82.211.81.145 offset 2.722933 sec
My time is Eastern, UTC=No. My XP has the correct time and Edgy Has the correct time, But I still get the Error in root  "Superblock last write time is in the future"

Any Suggestions ?
Thanks

---

### Post by rayofash on 2007-03-19
I'm on a fully up to date Dapper install (dual booting with Windows XP), and it is still set to change on April 1st. I tried using rdate and ntpdate to sync with a server, and it hasn't fixed the problem. Windows XP has also failed to set itself to use DST.

Edit: I followed the instructions here [http://www.nukesilo.com/2007/03/07/how-to-check-and-update-daylight-savings-time-information-in-linux/](http://www.nukesilo.com/2007/03/07/how-to-check-and-update-daylight-savings-time-information-in-linux/)

And it worked.

---

### Post by bg1256 on 2007-03-20
I am running Kubuntu 6.10, and originally, and I was away from this machine when the time change occurred.

Upon my return yesterday, it had not updated; however, after viewing this thread, I simply did:

sudo apt-get install tzdata

and then I rebooted.

All is good.

---

### Post by rayofash on 2007-03-20
Ugh! It stopped working!

What's wrong with Ubuntu!?

Edit: I did sudo ntpdate -u ntp.ubuntu.com and my screen went black and I had to reset the XServer. But now my time is set correctly. I bet it will break again if I reset though.

I dual boot Ubuntu Dapper and Windows XP. Windows hasn't updated for DST yet.

Edit: There we go.

---

### Post by Chazall1 on 2007-03-20
I got mine working. My BIOS was 1 hour behind, thats why I got the root error, last write time was in the future. However, after getting the time back I am having some sudo problems, whenever I am in a regular terminal, and type, gksudo, I get "Missing command to run" I have to open a root terminal to be root?  I did see the sudo info and I had two files /var/run/sudo/<user> One was named "0" and the other with no name, there was no Info in eather. I deleted them and I still get the "Missing command to run" 

Any Ideas???

Thanks

---

### Post by SuSUntu on 2007-03-21
> **Chazall1 said:**
> I got mine working. My BIOS was 1 hour behind, thats why I got the root error, last write time was in the future.

> **Chazall1 said:**
> 
My XP had the correct time first and I changed my time manually in Edgy, Adjust Date & Time and selected Synchronize Now and set my time up by one hour.


Glad you got it "working". Getting the "Superblock last write time is in the future" message makes some sense based on what you have described in the second quote above. However, what you write in the second quote itself does not square with **how my  system currently works**. For example, this is **how it might have worked on my system**:

- Boot into XP
- XP switches to new DST time (equivalent to original BIOS clock + 1 hour)
- the new time setting in XP conversely updates / changes the BIOS clock to match XP time (now BIOS = original BIOS time + 1 hour = XP clock = correct, updated DST time)
- Boot into Edgy (UTC=no, ntpdate does not run) 
- Edgy reads new BIOS time and sets clock to match (now Edgy clock = BIOS clock, = XP clock, and = correct DST )

However, you said (in Edgy) you had to **set [your] time up by one hour.** That's the part I can't reconcile and that's evidently what caused the 'Superblock last write time is in the future' problem.

It almost seems as if your BIOS is not picking up the changes you make in your OSes (mine does ... and vice versa). For example, the following sequence **may** explain what happened to you (compare this to **how it works on my system**):

- You boot into XP
- XP switches to new DST time (equivalent to original BIOS clock + 1 hour)
- the new time setting in XP **does not** (for some reason) update / change the BIOS clock to match XP time (now BIOS still = original BIOS time  <> XP clock <> correct, updated DST time)
- You boot into Edgy (first time)
- Edgy reads BIOS time and sets Edgy clock accordingly (now Edgy clock = original BIOS clock, and <> correct DST time )
- You then have to set Edgy **up by one hour** to match correct DST time; now, Edgy = correct DST time, but, since your BIOS (for some reason) is remaining unchanged despite clock changes in your OSes, the BIOS still = original BIOS time (i.e., BIOS clock <> Edgy clock, and <> correct DST)   
- During your next boot to Edgy, Edgy compares the last superblock "time-stamp" to a time based on the BIOS clock and "sees" that the superblock "time-stamp" is in the future; the superblock "time-stamp" that is being compared, I believe, is stored in the dynamic superblock field, fs_time, which was based on the correct DST time you manually set in Edgy
- On next boot, Edgy believes it needs to correct the file system with fsck based on the time-stamp comparisons
- As a fix, you **set the BIOS** so that BIOS = original BIOS + 1 hour = correct DST; the new BIOS clock setting will pass to OS clocks on next boot; furthermore, BIOS clock is now > last Edgy superblock "time-stamp"
- On next Edgy boot, boot proceeds without error because there is no conflict in superblock "time-stamp" comparison

Question: Why does it appear that your BIOS is not being updated by either a clock change in XP nor a clock change in Edgy, but that a BIOS clock change does properly affect the OS clocks (it should flow both ways, should it not)?

> **Chazall1 said:**
> 
However, after getting the time back I am having some sudo problems, whenever I am in a regular terminal, and type, gksudo, I get "Missing command to run" I have to open a root terminal to be root?  I did see the sudo info and I had two files /var/run/sudo/<user> One was named "0" and the other with no name, there was no Info in eather. I deleted them and I still get the "Missing command to run" 

Any Ideas???

Thanks

I've never seen this error except in cases when 'gksudo' is run without the application argument. For example, running

```

gksudo

```

exactly as shown normally produces the message, "Missing command to run". 

Running the complete command (gksudo application_name) works. For example: 

```

gksudo gedit

```

does not produce such an error (it may produce a different error if 'gedit' isn't installed. :)  )

Other than that, I have no idea, and I don't see any apparent  connection to your time issues.

---

### Post by Chazall1 on 2007-03-21
Thanks for the Info. My sudo is functioning properly. However tonight when I logged in to Edgy, I got the fsck on /root last write time was in the future!!!!!  I read your info, and I am trying to get the big picture. Does the BIOS clock stay constant and the OS change to DST? So if my XP has the correct time and I am showing Edgy as correct time, Where should I start? I have the updated DST time change info in Edgy, I have not checked my BIOS tonight, I will check after I post this. I need to figure out a plan of action to correct this on Edgy.

Be Back Shortly!

---

### Post by Chazall1 on 2007-03-21
My BIOS was the same with the 1hour that I had added yesterday. I changed my BIOS -1hour to see what would happen. My XP and Edgy indicate time -1hour. I dont know how often I get the "write in the future" after its fixed with fsck,  I have re-booted 2 times into Edgy and all is functioning as it was   yesterday?

---

### Post by Chazall1 on 2007-03-22
After changing my BIOS back and having Both OS time incorrect IWhile in Edgy I entered, sudo ntpdate -u ntp.ubuntu.com and Edgy indicated the correct time. I also ran, 
/usr/sbin/ntpdate -b -s -u ntp.ubuntu.com and here was my return,
Mar 21 23:58:57 localhost ntpdate[6111]: step time server 82.211.81.145 offset 0.001766 sec

I then re-booted into XP and the time was correct.

I just logged into Edgy and I did not get the /root last write time in the future. I will try later tonight to see what happens. Dont give up on me!!!!!!!!!!!!

---

### Post by SuSUntu on 2007-03-22
> **Chazall1 said:**
> 
However tonight when I logged in to Edgy, I got the fsck on /root last write time was in the future!!!!!

> **Chazall1 said:**
> 
My BIOS was the same with the 1hour that I had added yesterday. I changed my BIOS -1hour to see what would happen. My XP and Edgy indicate time -1hour. I dont know how often I get the "write in the future" after its fixed with fsck, I have re-booted 2 times into Edgy and all is functioning as it was yesterday?

> **Chazall1 said:**
> 
After changing my BIOS back and having Both OS time incorrect IWhile in Edgy I entered, sudo ntpdate -u ntp.ubuntu.com and Edgy indicated the correct time. I also ran,
/usr/sbin/ntpdate -b -s -u ntp.ubuntu.com and here was my return,
Mar 21 23:58:57 localhost ntpdate[6111]: step time server 82.211.81.145 offset 0.001766 sec
I then re-booted into XP and the time was correct.
I just logged into Edgy and I did not get the /root last write time in the future. I will try later tonight to see what happens. Dont give up on me!!!!!!!!!!!!


I'm not sure I'm completely understanding your posts. Basically what I am getting is:

- you thought it was fixed
- you determined it really wasn't fixed
- now you think it's fixed again, but you aren't sure

If you noticed in my first post addressing your issue, I wasn't very confident in whether it was actually fixed (I congratulated you in the first line by saying, "Glad you got it "working" ... notice the quotes :) )

More importantly, I still don't fully get how your BIOS is reacting to clock changes in the OSes. It just seems too strange how you have described it, but I can only go by what you are writing in your posts, and I give you the benefit of the doubt since you are there and I am not.   

> **Chazall1 said:**
> 
I read your info, and I am trying to get the big picture. Does the BIOS clock stay constant and the OS change to DST? So if my XP has the correct time and I am showing Edgy as correct time, Where should I start? I have the updated DST time change info in Edgy, I have not checked my BIOS tonight, I will check after I post this. I need to figure out a plan of action to correct this on Edgy.


You really do need to get a handle on how your BIOS and OS clocks are interacting irrespective of DST, which at this point has come and long gone. I'm not even sure this is totally on topic any more, to be honest with you.

However, to help out with the "big picture", I conducted quite a few tests to confirm how the BIOS clock and the OS clock interact in various situations. The effort was made almost a week ago to address confusion caused by misinformation or perhaps misinterpretation of accurate information. However, I never posted the results just because the debate here was getting tired. I've changed my mind based on your most recent inquiry ... so here it is.

The tests included:

1) BIOS clock & OS clock interaction under local time (UTC=no) where time changes are initiated in Ubuntu Edgy
2) BIOS clock & OS clock interaction under UTC time (UTC=yes) where time changes are initiated in Ubuntu Edgy 
3) BIOS clock & OS clock interaction under local time (UTC=no) where time changes are initiated in BIOS
4) BIOS clock & OS clock interaction under UTC time (UTC=yes) where time changes are initiated in BIOS

Comparisons were made of clock readings in BIOS (American Megatrend on Asus MB), a boot manager (BootIt NG), two Win XP SP2 installations and Edgy, all on the same PC.

A reading of the test results leads to some fairly simple (and I say, not surprising) conclusions about my Edgy installation, including but not limited to these:

1) any direct clock change in Edgy (this does not include a time zone change) changes the BIOS clock regardless of whether Edgy is set to UTC (UTC=yes) or local time (UTC=no);

2) any clock change initiated in the BIOS changes the Edgy clock regardless of whether Edgy is set to UTC (UTC=yes) or local time (UTC=no);

3) if Edgy is set to local time (UTC=no), a time zone change (e.g., America/New_York changed to America/Chicago) will change the BIOS clock just like a direct clock change from within Edgy would have changed the BIOS clock;

4) if Edgy is set to UTC time (UTC=yes), a time zone change (e.g., America/New_York changed to America/Chicago) will not change the BIOS clock (note: after initially setting Edgy to "UTC=yes", the BIOS clock is changed/set to UTC + 0 offset; thereafter, as long as Edgy is still set to "UTC=yes", any time zone change within Edgy leaves the BIOS alone, i.e., the BIOS clock remains set at UTC + 0 offset).

Please understand that a direct clock change (per my definition) may be made (and often is made) independent of the time zone setting and includes such things as:

- changing the clock with ntpdate
- manually setting the clock via the panel applet clock utility

On the other hand, a time zone change should be self-explanatory, but if not, an example of this would be switching from EDT (America/New_York) to CDT (America/Chicago) via the panel applet clock utility or by other means.

Because there seems to be conflicting information or conflicting interpretation of this interaction, I will not bother stating unequivocally that the above occurs in Linux in general, or Ubuntu in general or in Ubuntu Edgy in general. I will only say that this is what happens on my Edgy PC (my stance is more out of diplomacy than a lack of confidence in my technical understanding). Anyway, it may be helpful just to see if your Edgy installation behaves as mine does.

The raw data which follows is long and boring and may be confusing to an extent if just casually browsed. However, I believe if you take a slow look, it should make some sense and you should be able to reconcile it with the four summary conclusions I outlined above (hopefully I proofed the raw data transcription well enough).

---------------------------------------------------

**** Local Time Tests**

**UTC Setting:** UTC=No
**Edgy Clock Preference Setting:** UTC Time Not Selected (has no effect on system time, only affects display)
**Time Zone:** America/New_York

**Time Synchronization In Edgy:** None 
- ntp(d) not installed
- ntpdate installed, but does not run (see post #90 for details)

**Time Synchronization In Win XP 1 & 2:** Off / Blocked 
- Built-in sync is disabled / blocked at the firewall
- Time-sync nnchron jobs disabled during tests

**(CT) Correct Time Prior To Conducting Tests: Edgy Display:** 8:55 PM, 2007 03/17

**Clock Reading After Reboot. Done To Establish Clock Times Relative To CT Before Proceeding**
- **BIOS:** Matches CT Except For Elapsed Time ( 8:55 PM, 2007 03/17 )
- **BootIT NG Boot Manager:** Matches CT Except For Elapsed Time ( 8:55 PM, 2007 03/17 )
- **Win XP 1:** Matches CT Except For Elapsed Time ( 8:56 PM, 2007 03/17 )
- **Win XP 2:** Matches CT Except For Elapsed Time ( 8:58 PM, 2007 03/17 )
- **Edgy:** Matches CT Except For Elapsed Time ( 9:00 PM, 2007 03/17 )

--------

*** Local Time Test 1: Introduce 1 Hour Clock Error ( -1 Hour )**

**(T1_CT) Correct Time: Edgy Display:** 9:07 PM, 2007 03/17 
**(T1_CTE) Correct Time + Error: Edgy Display:** 8:07 PM, 2007 03/17

**Clock Reading After Reboot**
- **BIOS:** Matches T1_CTE Except For Elapsed Time ( 20:08 = 8:08 PM, 2007 03/17 )
- **BootIT NG Boot Manager:** Matches T1_CTE Except For Elapsed Time ( 8:08 PM, 2007 03/17 )
- **Win XP 1:** Matches T1_CTE Except For Elapsed Time ( 8:08 PM, 2007 03/17 )
- **Win XP 2:** Matches T1_CTE Except For Elapsed Time ( 8:09 PM, 2007 03/17 )
- **Edgy:** Matches T1_CTE Except For Elapsed Time ( 8:11 PM, 2007 03/17 )

--------

*** Local Time Test 2: Introduce Time Zone Change**

**Time Zone Changed From:** America/New_York To America/Chicago
**Equivalent UTC/GMT Offset for Time Zone:**
- **Standard time zone:** UTC/GMT -6 hours
- **Daylight saving time:**	+1 hour
- **Current time zone offset:** UTC/GMT -5 hours
- **Time zone abbreviation:** CDT - Central Daylight Time

**(T2_CT) Correct Time: Edgy Display:** 9:28 PM, 2007 03/17
**(T2_CTZ) Correct Time + Zone Change: Edgy Display:** 8:28 PM, 2007 03/17

**Clock Reading After Reboot**
- **BIOS:** Matches T2_CTZ Except For Elapsed Time ( 20:29, 2007 03/17 = 8:29 PM, 2007 03/17 )
- **BootIT NG Boot Manager:** Matches T2_CTZ Except For Elapsed Time ( 8:29 PM, 2007 03/17 )
- **Win XP 1:** Matches T2_CTZ Except For Elapsed Time ( 8:29 PM, 2007 03/17 )
- **Win XP 2:** Matches T2_CTZ Except For Elapsed Time ( 8:31 PM, 2007 03/17 )
- **Edgy:** Matches T2_CTZ Except For Elapsed Time ( 8:33 PM, 2007 03/17 )

--------

*** Local Time Test 3: Change BIOS Clock Directly ( + 1 Hour )**

**(T3_CT) Correct Time: Edgy Display:** 2:19 AM, 2007 03/18
**(T3_CTBIOS) Correct Time: BIOS:** 02:19 AM, 2007 03/18
**(T3_CTEBIOS) Correct Time + Error: BIOS:** 03:19 AM, 2007 03/18

**Clock Reading After BIOS Clock Change**
- **BootIT NG Boot Manager:** Matches T3_CTEBIOS Except For Elapsed Time ( 3:20 AM, 2007 03/18 )
- **Win XP 1:** Matches T3_CTEBIOS Except For Elapsed Time ( 3:20 AM, 2007 03/18 )
- **Win XP 2:** Matches T3_CTEBIOS Except For Elapsed Time ( 3:21 AM, 2007 03/18 )
- **Edgy:** Matches T3_CTEBIOS Except For Elapsed Time ( 3:23 AM, 2007 03/18 )


---------------------------------------------------------

**** UTC Tests**

**UTC Setting:** UTC=yes
**Edgy Clock Preference Setting:** see specific test data
**Time Zone:** America/New_York
**UTC/GMT Offset for Time Zone:**
- **Standard time zone:** UTC/GMT -5 hours
- **Daylight saving time:** +1 hour
- **Current time zone offset:** UTC/GMT -4 hours
- **Time zone abbreviation:** EDT - Eastern Daylight Time

**Time Synchronization In Edgy:** None 
- ntp(d) not installed
- ntpdate installed, but does not run (see post #90 for details)

**Time Synchronization In Win XP:** Off / Blocked 
- Built-in sync is disabled / blocked at the firewall
- Time-sync nnchron jobs disabled during tests

**(CT_LT) Correct Time Prior To Conducting Tests: Edgy Display Set To Local Time:** 9:55 PM, 2007 03/17
**(CT_UTC) Correct Time Prior To Conducting Tests: Edgy Display Set To UTC:** 1:55 AM, 2007 03/18

**Clock Readings After First Reboots Since Switching to UTC=yes. Done To Establish Clock Times Relative To CT_LT and CT_UTC Before Proceeding:**
- **BIOS:** Matches CT_UTC Except For Elapsed Time ( 1:55 AM, 2007 03/18 )
- **BootIT NG Boot Manager:** Matches CT_UTC Except For Elapsed Time ( 1:55 AM, 2007 03/18 )
- **Win XP 1:** Matches CT_UTC Except For Elapsed Time ( 1:56 AM, 2007 03/18 )
- **Win XP 2:** Matches CT_UTC Except For Elapsed Time ( 1:57 AM, 2007 03/18 )
- **Edgy Display Set To Local Time:** Matches CT_LT Except For Elapsed Time ( Local: 9:59 PM, 2007 03/17 )
- **Edgy Display Set To UTC Time:** Matches CT_UTC Except For Elapsed Time ( UTC: 1:59 AM, 2007 03/18 )

--------

*** UTC Test 1: Introduce 1 Hour Clock Error ( -1 Hour )**

**(T4_CT_LT) Correct Time: Edgy Display Set To Local Time:** 10:24 PM, 2007 03/17 
**(T4_CT_UTC) Correct Time: Edgy Display Set To UTC Time:** 2:24 AM, 2007 03/18 

**(T4_CTE_LT) Correct Time + Error: Edgy Display Set To Local Time:** 9:24 PM, 2007 03/17
**(T4_CTE_UTC) Correct Time + Error: Edgy Display Set To UTC Time:** 1:24 AM, 2007 03/18

**Clock Reading After Reboot**
- **BIOS:** Matches T4_CTE_UTC Except For Elapsed Time ( 1:24 AM, 2007 03/18 )
- **BootIT NG Boot Manager:** Matches T4_CTE_UTC Except For Elapsed Time ( 1:24 AM, 2007 03/18 )
- **Win XP 1:** Matches T4_CTE_UTC Except For Elapsed Time ( 1:25 AM, 2007 03/18 )
- **Win XP 2:** Matches T4_CTE_UTC Except For Elapsed Time ( 1:27 AM, 2007 03/18 )
- **Edgy Display Set To Local Time:** Matches T4_CTE_LT Except For Elapsed Time ( Local: 9:29 PM, 2007 03/17 )
- **Edgy Display Set To UTC:** Matches T4_CTE_UTC Except For Elapsed Time ( UTC: 1:29 AM, 2007 03/18 )

--------

*** UTC Time Test 2: Introduce Time Zone Change**

**Time Zone Changed From:** America/New_York To America/Chicago
**UTC/GMT Offset for New Time Zone:**
- **Standard time zone:** UTC/GMT -6 hours
- **Daylight saving time:**	+1 hour
- **Current time zone offset:** UTC/GMT -5 hours
- **Time zone abbreviation:** CDT - Central Daylight Time

**(T5_CT_LT) Correct Time: Edgy Display Set To Local Time:** 10:34 PM, 2007 03/17
**(T5_CT_UTC) Correct Time: Edgy Display Set To UTC Time:** 2:34 AM, 2007 03/18

**(T5_CTZ_LT) Correct Time + Zone Change: Edgy Display Set To Local Time:** 9:34 PM, 2007 03/17
**(T5_CTZ_UTC) Correct Time + Zone Change: Edgy Display Set To UTC Time:** 1:34 AM, 2007 03/18

**Clock Reading After Reboot**
- **BIOS:** Matches T5_CT_UTC Except For Elapsed Time ( 2:35 AM, 2007 03/18 )
- **BootIT NG Boot Manager:** Matches T5_CT_UTC Except For Elapsed Time ( 2:35 AM, 2007 03/18 )
- **Win XP 1:** Matches T5_CT_UTC Except For Elapsed Time ( 2:36 AM, 2007 03/18 )
- **Win XP 2:** Matches T5_CT_UTC Except For Elapsed Time ( 2:28 AM, 2007 03/18 )
- **Edgy Display Set To Local Time:** Matches T5_CTZ_LT Except For Elapsed Time ( Local: 9:40 PM, 2007 03/17 )
- **Edgy Display Set To UTC:** Matches T5_CTZ_UTC Except For Elapsed Time ( UTC: 1:40 AM, 2007 03/18 )

--------

*** UTC Time Test 3: Change BIOS Clock Directly ( + 1 Hour )**

**(T6_CT_LT) Correct Time: Edgy Display Set To Local Time:** 2:41 AM, 2007 03/18
**(T6_CT_UTC) Correct Time: Edgy Display Set To UTC:** 6:41 AM, 2007 03/18
**(T6_CTBIOS) Correct Time: BIOS:** 06:42 AM, 2007 03/18
**(T6_CTEBIOS) Correct Time + Error: BIOS:** 07:42 AM, 2007 03/18

**Clock Reading After BIOS Clock Change**
- **BootIT NG Boot Manager:** Matches T6_CTEBIOS Except For Elapsed Time ( 7:42 AM, 2007 03/18 )
- **Win XP 1:** Matches T6_CTEBIOS Except For Elapsed Time ( 7:43 AM, 2007 03/18 )
- **Win XP 2:** Matches T6_CTEBIOS Except For Elapsed Time ( 7:45 AM, 2007 03/18 )
- **Edgy Display Set To Local Time:** Matches T6_CTEBIOS (Local Equivalent) Except For Elapsed Time ( 3:46 AM, 2007 03/18 )
- **Edgy Display Set To UTC:** Matches T6_CTEBIOS Except For Elapsed Time ( 7:46 AM, 2007 03/18 )

-------------

**Note:** To assure all tests were started from a clean slate, the following was done:
- Where applicable, time and time zone were reset to correct time and correct time zone between each test.
- Time was manually synced between each test to ensure clock accuracy using: sudo /usr/sbin/ntpdate -b -s -u ntp.ubuntu.com
- PC was booted into BIOS and into each OS after resetting time and time zone to ensure resets were effective before continuing with tests.
- Additionally, after 'UTC=no' was changed to 'UTC=yes', PC was rebooted before proceeding with 'UTC=yes' testing.

---

### Post by Chazall1 on 2007-03-22
Thank You for the information. You have explained the process in a very professional and logical way, nice work. If anyone asks for info on BIOS and OS Time and how it works, I will pass this along. So far All my times indicate the correct times, and I have not yet got my root last write time in the future. Thanks for you dedication and support!!!

---

### Post by Chazall1 on 2007-03-22
Another thing that I agree with you is that the time does not automaticly update on boot. I ran 
"/usr/sbin/ntpdate -b -s -u ntp.ubuntu.com" and here was the output,

Mar 22 23:32:10 localhost ntpdate[7268]: step time server 82.211.81.145 offset -1.729779 sec

then did the update, "sudo ntpdate -u ntp.ubuntu.com"

and ran "/usr/sbin/ntpdate -b -s -u ntp.ubuntu.com" , and got this output,

Mar 22 23:35:12 localhost ntpdate[7511]: step time server 82.211.81.145 offset 0.036432 sec

If I dont get an auto update of the time, you can see see the value difference between the two offset times, and if left not updated, I would get the root error last write time in the future?

Is there a fix for this issue???

---

### Post by kwilliam on 2007-04-01
My time did not switch like I expected, but
[SIZE="5"]Here's how I got it fixed.  (At least on my machine, and Kubuntu.)[/SIZE]

Go to Control Center -> System Administration -> Date and Time.  My machine had "set date and time automatically" checked.  This is OK.  The dropdown on the right was set to "Public Time Server (pools.ntp.org)"  **Changing this to north-america.pool.ntp.org and hitting Apply fixed the time.**

Interestingly, changing it back to "pools.ntp.org" didn't move the time back an hour; it stayed correct.  This makes me think it needed some kind of forced reconfiguration or something.

I haven't tried booting XP to see what time it's showing.

---

### Post by Ramaddan on 2007-04-01
Hmm...

Not only is my daylight savings update not working, and synchronize time with internet server is not working as well, so my time is never synchronized.

Is there a problem with the whole module? Has a bug already been posted, or is this problem of time not synchronizing at all specific to my machine?

Thanks.

---

### Post by Chazall1 on 2007-04-14
I just upgraded to Feisty and I still have the same problem, my superblock last write time is in the future? I must be missing something simple?? I tried using the internet to sync my time, I have not changed my UTC=no. I have been running "/usr/sbin/ntpdate -b -s -u ntp.ubuntu.com" to see what has been occuring with the time.

Any assistance would be helpful.

Thanks

---

### Post by Ramaddan on 2007-04-21
> **Ramaddan said:**
> Hmm...

Not only is my daylight savings update not working, and synchronize time with internet server is not working as well, so my time is never synchronized.

Is there a problem with the whole module? Has a bug already been posted, or is this problem of time not synchronizing at all specific to my machine?

Thanks.

YEY :-D, finally fixed on Edgy.

Received the update bubble today, so I updated tzdata, and it fixed it,
my daylight savings and time finally synchronizes with internet servers.

Thanks to everyone for their efforts.

---

### Post by itismike on 2008-03-09
I'm embarrassed to say this is still a problem in March 2008.  Seems like a pretty critical error if your OS doesn't know how to handle time. :(  Hopefully this will get the attention it deserves.

---

### Post by Matt0001 on 2008-03-09
March 2008, my desktop, which was left on overnight, adjusted fine. My laptop so far has not. Both are on 7.10 with all updates installed.

---

### Post by peabody on 2008-03-09
Wow, it's the thread that just won't quit :).  I remember this baby.

I'm a bit wiser than I was the first time I was talking in this thread.  I have an idea for what may be causing the problem and why there is such a broad set of conditions that seem impossible to nail down:

[LIST=1]
[*]There are two clocks in Linux (and Unix systems in general).  The hardware clock and the system clock.
[*]Linux's system clock always runs on UTC and time stamps on things like modification times on files are in UTC
[*]Hence the need of a time zone setting so these times can be localized
[*]However, a computer's bios clock can be arbitrarily set to anything.  The time in the BIOS could represent localtime, or it could represent, UTC.  Linux has to be told which it is, so that when it boots, it knows what value to initialize its system clock to
[*]The hardware clock is never updated again until **Linux is properly shutdown, or something like hwclock --systohc is run ** <-- I'm guessing this point explains a lot.
[*]Consequently...Linux will never change the clock on boot up.  It will only change the clock while its running, or during shutdown.
[*]However, as was revealed in this thread before, the bootup scripts ran ntpdate as part of the process.
[*]The thing here is, I know that ntpdate would update the *system* clock.  I don't know if it updates the *hardware* clock, or if it relies on Linux to do that itself during a proper shutdown.
[/LIST]

In otherwords, several scenarios can lead to Linux not updating the hardware clock assuming that ntpdate only updates the system clock.  Just about all of these are assuming the machine's hardware clock runs on localtime:

[LIST]
[*]Having the computer on during the changeover, but not properly shutting down the computer.
[*]Not having Linux on during the change over, and not having your machine on the Internet during bootup for ntpdate to do its thing.
[*]Having Linux off during the change over, booting it with an Internet connection, but then not properly shutting it down.
[*] Having the 'automatically adjust for daylights savings time' turned off in the time zone config (however that's done, I'm pretty sure there's a setting for that.
[*] Finally, the tzdata package went through a change very very recently.  Not having installed this update in time for the changeover may have been another cause.
[/LIST]

There may even be more convoluted scenarios than this.  Especially with dual-booters, unless you've disabled it, windows will try to adjust the hardware clock itself for DST, leading to a potential jump-forward-twice problem.

The only advice I have for people at this point if they want to avoid this in the future is:

[LIST=1]
[*]Update often
[*]If not dual booting run your hardware clock on UTC
[*]If dual booting, let windows do the change over!
[/LIST]``

---

