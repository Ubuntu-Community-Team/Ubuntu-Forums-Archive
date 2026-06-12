---
title: "Lost Windows users"
date: 2007-01-02
forum: General Help
---

### Post by thomasa93 on 2007-01-02
For about 6 months now, i have been dual-booting Windows XP and Ubuntu. Just recently, I booted into Windows and the list of users was gone! I tried logging in as the administrator and it produced an error telling me that it couldn't log me in. Does anyone know how to get my users list back?

P.S. I checked and all the documents for each user are still there

---

### Post by arsenic23 on 2007-01-02
Have you tried hitting ctrl-alt-delete twice and logging in manually?

---

### Post by reza81 on 2007-01-02
I thing some how you messedup your windows registery replays it with your backup registery. ther is also a file where the users are noted ... where its located? i dont know. BUT if the file is gone your reg could be rewriten by your m$ OS.

I switched to Ubuntu 3 weeks ago. its a perfect replacement that doesnt have this kind of bullshizzle. I only miss macromedia studio mx!

---

### Post by thomasa93 on 2007-01-02
> **arsenic23 said:**
> Have you tried hitting ctrl-alt-delete twice and logging in manually?

Yes,  I tried that and still got the same error.:(

---

### Post by thomasa93 on 2007-01-02
Does anyone no where the file that "reza81" is talking about is located?

---

### Post by riven0 on 2007-01-02
> **thomasa93 said:**
> Does anyone no where the file that "reza81" is talking about is located?

You mean windows registry? If I remember correctly, go to Run and type regedt32

Should come up...

Edit: If that doesn't work, try regedit

---

### Post by ~LoKe on 2007-01-02
It's **regedit**.

---

### Post by skwishybug on 2007-01-03
Are you able to boot in 'Safe Mode'?

If you tap F8 during the start up (right after it does its POST check of memory and stuff) you should get a menu with a list of startup options--it can be a little tricky to catch it, you might need to try a couple of times.

When the menu comes up, select safe mode and it should take you to a log in screen with an option being "Administrator". Most people don't have a password on this one (since they don't know it technically exists).

Once inside windows, set up a new account with administrator privliges, reboot, and log back in with that account to try and fix the other ones (check with the M$ and Windows forums to find out more on the fix).

-sk

---

### Post by jordanmthomas on 2007-01-03
I am thomasa93's brother and I figured I'd maybe give a little more information on the troubles he's having.
Like he said, Windows boots fine but there are no users on the login / welcome screen.
I immediately tried ctrl - alt - delete twice and logging in as one of the normal users --> failure.
So, while there I tried logging in as the hidden Administrator which I know sometimes doesn't work anyway.  Not surprised when it failed, I booted into safe mode.  Once it booted, there was still no users in the list so I can't even log in as the hidden admin.

After that, I tried booting into safe mode + command prompt.  Apparently you need to log in first there as well, so it was a no go.

I have looked in the Windows partition and I can't seem to find anything wrong with it so I will be able to back everything up if it comes down to it 

Now, here's my question:  does anyone know where the user accounts are stored.  I have an Orphcrack CD that loads a SAM file to check for Windows users and passwords.  If anyone knows where this is located usually maybe I can use some disk recovery tools to get it back.  Is it in the registry?  Is it a separate file somewhere? 

If it is indeed a problem in the registry, do you know where the registry is stored in Windows and do you know if regedit will work under Wine so I can actually edit it?

I am just getting tired of having to reinstall XP on that computer and restore my parents' old e-mails and **all** their shortcuts and settings once every two months, so I would like to fix it without a reinstallation if it's at all possible.

Even if you can only answer a few of the questions here, maybe I can stitch it all together and come up with some sort of solution.  I seem to have lost my l33t Wind0w$ skillz0rz over the past few years.  :icon_frown:

---

### Post by GrumpyBob on 2007-01-03
Usually when I have windows problems (not on my behalf now that I'm an Ubuntu person!) I've found [http://www.annoyances.org/](http://www.annoyances.org/) to be pretty helpful, perhaps there is advice to be had there...

Robert

---

### Post by Rhubarb on 2007-01-03
Do it the lame windows techie way:
- Back up data
- Reinstall windowz
- Put backed up data back

I know you probably won't learn too much doing it this way, but quite often it is the fastest way of fixing up most fubared windowz installs.

---

### Post by mahiyar on 2007-01-03
If you have systome restore points set can u use that?

---

### Post by thomasa93 on 2007-01-03
> **mahiyar said:**
> If you have systome restore points set can u use that?

I don't think that will work because I cannot login. Does anyone know if  you can use System Restore before logging in?

---

### Post by ffi on 2007-01-03
> **jordanmthomas said:**
> I am thomasa93's brother and I figured I'd maybe give a little more information on the troubles he's having.
Like he said, Windows boots fine but there are no users on the login / welcome screen.
I immediately tried ctrl - alt - delete twice and logging in as one of the normal users --> failure.
So, while there I tried logging in as the hidden Administrator which I know sometimes doesn't work anyway.  Not surprised when it failed, I booted into safe mode.  Once it booted, there was still no users in the list so I can't even log in as the hidden admin.

After that, I tried booting into safe mode + command prompt.  Apparently you need to log in first there as well, so it was a no go.

I have looked in the Windows partition and I can't seem to find anything wrong with it so I will be able to back everything up if it comes down to it 

Now, here's my question:  does anyone know where the user accounts are stored.  I have an Orphcrack CD that loads a SAM file to check for Windows users and passwords.  If anyone knows where this is located usually maybe I can use some disk recovery tools to get it back.  Is it in the registry?  Is it a separate file somewhere? 

If it is indeed a problem in the registry, do you know where the registry is stored in Windows and do you know if regedit will work under Wine so I can actually edit it?

I am just getting tired of having to reinstall XP on that computer and restore my parents' old e-mails and **all** their shortcuts and settings once every two months, so I would like to fix it without a reinstallation if it's at all possible.

Even if you can only answer a few of the questions here, maybe I can stitch it all together and come up with some sort of solution.  I seem to have lost my l33t Wind0w$ skillz0rz over the past few years.  :icon_frown:
C:/Documents and Settings is useally where all info is stored including parts of the registry (NTUSER.DAT)
look in the user directories and there you will also see a backup of NTUSER.DAT

---

### Post by thomasa93 on 2007-01-03
It's strange because NTUSER.DAT is still present in each account.
I guess we'll just do the good 'ol reinstall.

---

### Post by ffi on 2007-01-03
you could always try to repair first using the windows install disk or at least check if you can log into the partition with the repair disk, if this is the case most likely you cab repair things...

now I remember there being something with msgina.dll and logging in too.....

---

### Post by dannyboy79 on 2007-01-03
this is from another forum, is it possible that you installed anything like this from sony?

Jan 31st 2005, 12:20 pm | #10 

--------------------------------------------------------------------------------
Thanks for those suggestions, however the problem prevents proceeding past step #2. I figured out what 'caused' the problem and will explain in a minute. But to save all of my data from that computer which wouldn't let me log on I had to use a second computer and attach my hard-drive in "slave" mode. After transferring everything that I wanted to keep, I then had to perform a complete reinstall of my operating system!

Who caused this mess, you ask? SONY!!!!

WARNING...DO NOT USE SONY'S "SONIC STAGE" version 2 !!

Why do I know that they are the cause? Because immediately before my machine was ruined by Sony, I installed this software. My computer is WinXP home with SP2. Apparently this Service Pack is incompatable with Sony's horrible software.

You now ask, how do you know that something else didn't cause this problem?

Great question...like an idiot, after reinstalling my new OS and obtaining SP2 from the Microsoft website, I reinstalled Sonic Stage. BOOM...it happened immediately after that.

Perhaps Sony's new version 2.3, or something, no longer does this...I am not willing to try until I can get some explicit answers from those morons!

Good luck everyone...I hope my pain can save you all several hours of your lives that can be better spent. (Now how do I deal w/ my anger?)

---

### Post by thomasa93 on 2007-01-03
> **dannyboy79 said:**
> this is from another forum, is it possible that you installed anything like this from sony?

Jan 31st 2005, 12:20 pm | #10 

--------------------------------------------------------------------------------
Thanks for those suggestions, however the problem prevents proceeding past step #2. I figured out what 'caused' the problem and will explain in a minute. But to save all of my data from that computer which wouldn't let me log on I had to use a second computer and attach my hard-drive in "slave" mode. After transferring everything that I wanted to keep, I then had to perform a complete reinstall of my operating system!

Who caused this mess, you ask? SONY!!!!

WARNING...DO NOT USE SONY'S "SONIC STAGE" version 2 !!

Why do I know that they are the cause? Because immediately before my machine was ruined by Sony, I installed this software. My computer is WinXP home with SP2. Apparently this Service Pack is incompatable with Sony's horrible software.

You now ask, how do you know that something else didn't cause this problem?

Great question...like an idiot, after reinstalling my new OS and obtaining SP2 from the Microsoft website, I reinstalled Sonic Stage. BOOM...it happened immediately after that.

Perhaps Sony's new version 2.3, or something, no longer does this...I am not willing to try until I can get some explicit answers from those morons!

Good luck everyone...I hope my pain can save you all several hours of your lives that can be better spent. (Now how do I deal w/ my anger?)

No, I have not installed this software.  Thanks for the suggestion!

---

### Post by jordanmthomas on 2007-01-03
Well, we went ahead and reinstalled.  Since I backed everything up, I was able to restore all the settings using each user's NTUSER.DAT and everything appears to be peachy.  Thanks for all your suggestions and your help

---

