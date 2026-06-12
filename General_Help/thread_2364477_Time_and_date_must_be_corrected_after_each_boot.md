---
title: "Time and date must be corrected after each boot"
date: 2017-06-23
forum: General Help
---

### Post by AbleTassie on 2017-06-23
Hello everybody,

Yesterday my laptop went off suddenly. I am not sure why it went off (it may be because of overheating, the battery which is old also now no longer seems to hold any charge either). In any case, now the date and time displayed on the taskbar in Lubuntu 16.04.2 LTS is wrong after every boot. For some reason the date is now Feb 11, 2016. The time is wrong as well, (but I think that the time does increase as it should). Firefox will not let me connect to the internet unless the date (and time as well I think) is correct. So I have to manually go into the Time and Date utility under System Tools and change to the correct date and time. Even though supposedly there is a way to automatically sync the date and time using the internet, that option is grayed out, so I can't do that. 

This is really a hastle, of course, because I have to do it after every boot. After the first sudden shut off I got a screen on rebooting that led me to believe I might have to reset to the correct time in the BIOS or something. 

Does anybody know what I can do to correct this problem?

Thanks,

Able

---

### Post by Autodave on 2017-06-23
Do you know how to get into the BIOS? If so, you need to start there first. Every computer has a different way of accessing the BIOS. It might be the ESC key, DEL key, F10, F12, etc. You can google your computer make and model to find out what key is used.  You pretty much start the computer and immediately start hitting that key over and over rather quickly until the BIOS appears or you are given the option to enter the BIOS.

PLEASE be careful and only adjust the date and time and then save.

---

### Post by Autodave on 2017-06-23
You may have to do this everytime if your battery is shot: may be time to look for a new battery.

---

### Post by AbleTassie on 2017-06-23
Thanks Autodave,

I went into the BIOS and corrected the date and time. Now when I boot into Lubuntu, the date is correct, but the time is still off. It is 7 hours behind. I corrected the time with the Time and Date Utility in System Tools, but the time will only stay correct for that session on the laptop. When I reboot again, the date is correct, but the time is incorrect, 7 hours behind.  If I go back into the BIOS though, the time is correct in the BIOS. I tried resetting the BIOS time from the correct time to the correct time and exiting saving the changes. That did not help either. 

Not sure what to do now. At least Firefox allows me to get on the internet with the correct date, even if the time is incorrect.

Thanks,

A.

---

### Post by AbleTassie on 2017-06-23
I came up with a "solution" of sorts to this problem. Somehow Lubuntu is subtracting 7 hours from the true BIOS time. Who knows why? 

But I figured maybe if I change my time zone in the Time and Date utility in System Tools (under Manual Configuration) to 7 hours ahead of where I am, then Lubuntu will display the correct time. As it turns out, that time zone is the Azores in the Atlantic. I did that, and now the correct time displays in Lubuntu when I boot into the system. 

As I said previously, I cannot use the internet synchronization for some reason.

Interestingly, I am Virtualboxing Windows XP and I checked the date and time in Windows XP and the time was also off by 7 hours, so I changed the time zone in WIndows XP to the Azores as well and now the time is correct in Windows XP as well when I start it in Virtualbox.

In addition, I can connect to the internet through Firefox now without any kind of rigamarole needing to be done with the date or time.

Maybe I should file a bug report? 

Thanks,

A.

---

### Post by Bashing-om on 2017-06-23
AbleTassie; Hey !

A thought -
Dual booting with Windows, where Windows controls the hardware clock as local time ( linux is UTC) ?

[INDENT][INDENT]maybe
[/INDENT][/INDENT]

---

### Post by Autodave on 2017-06-23
Or, the computer is thinking that you are in  a different part of the world. I, unfortunately, have no idea where that info is stored or how to change.

---

### Post by Dennis N on 2017-06-23
I think you need to replace the CMOS battery on the motherboard - it keeps the system time correct, especially important when other power source (battery or line power) is unavailable. CMOS has a limited lifetime.

---

### Post by AbleTassie on 2017-06-24
Dennis,

You might be right, but after a  cursory check of the internet it's not clear to me that my laptop, the Lenovo Y510, even has a CMOS battery that can be replaced. Newer PCs apparently no longer have such batteries. In the meantime, it is working well enough. Unless somebody thinks I should file a bug report, I will mark this thread as solved soon. 

A.

---

### Post by efflandt on 2017-06-24
There is no bug (other than possible dead CMOS battery). As mentioned Windows typically sets the hardware clock to localtime and *nix like OS's typically use UTC time. Although normally Ubuntu determines when installed which it is, something might occasionally get confused.

To fix that make sure that "your" timezone and date/time are correctly set in Linux. Then do the following which tells Linux that the CMOS clock is localtime (not utc) and sets the CMOS clock to system time:```
sudo hwclock -w -localtime
``` Then boot Windows, set your correct timezone there and see if the time is correct and stays correct in both operating systems.

---

### Post by AbleTassie on 2017-06-24
[SIZE=2]I found instructions for replacing the CMOS battery in the Y510 at [https://forums.lenovo.com/t5/forums/v3_1/forumtopicpage/board-id/ll04_en/thread-id/94191/page/2](https://forums.lenovo.com/t5/forums/v3_1/forumtopicpage/board-id/ll04_en/thread-id/94191/page/2) , see below 

[/SIZE][SIZE=2]   [/SIZE][h=2][SIZE=2]Re: CMOS battery on Y510 needs replacement
[/SIZE][/h][SIZE=2][/SIZE]
[SIZE=2][/SIZE][SIZE=2]&#8206;07-02-2014 05:45 AM  [/SIZE]
[SIZE=2] [/SIZE][SIZE=2] 	[/SIZE][SIZE=2]Turn the system over. Remove the Hard Drive first.  with the 	main battery oritented at the top, the HDD is located below the 	cover door on the bottom left.  Remove one captured screw at 	the bottom right of the door.  Remove the HDD by sliding it to 	the left and lifting it out.  Under the drive there is a square 	plastic sheet that is stuck to the solid plastic base.  Unpeel 	the plastic sheet.   You now see the blue CMOS battery, its 	cable and plug.  Unplug and replace.  
[/SIZE]
[SIZE=2] [/SIZE]
[SIZE=2] [/SIZE][h=2][SIZE=2]Re: CMOS battery on Y510 needs replacement[/SIZE][/h][SIZE=2] [/SIZE][SIZE=2] 	[/SIZE][SIZE=2]&#8206;11-24-2014 08:23 AM  
[/SIZE]

[SIZE=2] [/SIZE][SIZE=2] 	[/SIZE][SIZE=2]PERFECT and CristalClear explanation ! 	This allowed me to extract CMOS ! Will this clear password ?? We'll 	see....  	
[/SIZE]
[SIZE=2] [/SIZE]
[SIZE=2]  [/SIZE][h=2][SIZE=2]Re: CMOS battery on Y510 needs replacement[/SIZE][/h][SIZE=2][/SIZE]
[SIZE=2][/SIZE][SIZE=2]&#8206;11-24-2014 08:25 AM - edited &#8206;11-24-2014 08:27 AM  [/SIZE]
[SIZE=2] [/SIZE][SIZE=2] 	[/SIZE][SIZE=2]Thank you for this explanation. Y510 are oldies now and not so easy to find information...And it was way more simple that seen on youtube...[/SIZE]

[SIZE=2] 	[/SIZE][SIZE=2] Regards[/SIZE]

[SIZE=2] 	[/SIZE][SIZE=2] Note : the plastic under the hardrive is strong. Use a 	screwdriver (or any flat tool) to[/SIZE]

[SIZE=2] [/SIZE]
[SIZE=2] [/SIZE][h=2][SIZE=2]Re: CMOS battery on Y510 needs replacement[/SIZE][/h][SIZE=2][/SIZE]
[SIZE=2][/SIZE][SIZE=2]&#8206;11-24-2014 09:24 AM  [/SIZE]
[SIZE=2] [/SIZE][SIZE=2]Hello

unfortunately despite the cmos battery is not in anymore, a password is till requested.

Is thare any kind of Generic BIOS password or any default bios password ?

PLEASE HELP

Regards

ps : feel free to email me in any case

   **Community Super Moderator**

Good day.

  There are no 'generic' or 'default' BIOS passwords.

 Also, the [Community Guidelines]("https://forums.lenovo.com/t5/Welcome-FAQs/Lenovo-Community-Participation-Rules/m-p/1") do not allow discussion of circumvention of security measures, which includes passwords. Please see the [Y510 User Guide]("http://download.lenovo.com/UserFiles/UserGuide/en/User%27s%20guides%20and%20manuals/Y510/Y510%20User%27s%20Guide.pdf"), starting on page 22, for the allowable discussion on the subject. If you are unable to remember the correct password, you may wish to contact Service (info below) to discuss any available options.

  Since the original question in this thread, *machine disassembly* & *removing / installing the CMOS battery*, has been answered, I'm locking this thread before more password discussion ensues.

  Regards.

 
 
[/SIZE]
[SIZE=2][/SIZE]

---

### Post by AbleTassie on 2017-06-24
> **efflandt said:**
> There is no bug (other than possible dead CMOS battery). As mentioned Windows typically sets the hardware clock to localtime and *nix like OS's typically use UTC time. Although normally Ubuntu determines when installed which it is, something might occasionally get confused.

To fix that make sure that "your" timezone and date/time are correctly set in Linux. Then do the following which tells Linux that the CMOS clock is localtime (not utc) and sets the CMOS clock to system time:```
sudo hwclock -w -localtime
``` Then boot Windows, set your correct timezone there and see if the time is correct and stays correct in both operating systems.

efflandt,

I am virtualboxing windows, not dual booting. I really don't want to dual boot. Would what you are suggesting work with a Virtualboxed Windows XP?

Thanks,

A.

---

### Post by efflandt on 2017-06-26
> **AbleTassie said:**
> efflandt,

I am virtualboxing windows, not dual booting. I really don't want to dual boot. Would what you are suggesting work with a Virtualboxed Windows XP?

Thanks,

A.

I guess I missed the virtualbox part, but using that hwclock command on the Linux host (and setting proper timezones in both OS's) should work whether the Windows guest directly or virtually accesses the CMOS clock/calendar.

And it just dawned on my why I ran into that problem. I used a laptop to install Ubuntu to an SSD where it was the only OS, so Linux assumed CMOS was utc. I moved the SSD to my desktop which also has Win7 on its hard drive, which assumes CMOS is localtime. So the 2 OS's were out of sync until I did the "hwclock -w -localtime" to tell Ubuntu to use localtime for CMOS.

---

### Post by AbleTassie on 2017-06-27
For the time being my date and time are OK using my "solution." So I will mark as SOLVED. I may, however, have to return to the CMOS battery issue later.

Thanks efflandt, Dave, Bashing Om and Dennis. 

A.

---

