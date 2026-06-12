---
title: "Screen Resolution Help"
date: 2007-09-06
forum: General Help
---

### Post by h11g on 2007-09-06
Hi dear Ubuntu users, i recently decided to swtich over to Ubuntu from windows. I am using a dell 700m laptop which has a widescreen. I have trouble changing the screen resolution from 1028X784 to 1280X1024. anyone can help me out here?

---

### Post by thegreenblob on 2007-09-06
Have you tried going in to System>Preferences>Screen Resolution?

---

### Post by h11g on 2007-09-06
> **thegreenblob said:**
> Have you tried going in to System>Preferences>Screen Resolution?

Yes i did, but it only show max resolution of 1024X768. but my screen is capable of 1280X1024

---

### Post by peromalosutra on 2007-09-06
You need to change xorg.conf file.
First, jump to terminal and type sudo gedit /etc/X11/xorg.conf. Enter your password and press enter. This will open text editor. Scanf over the file until you find the lines containing list of resolutions (it will be pretty easy to spot them). At the begining of each line containing resolution list add "1280x1024" (or other resolution that you know your monitor is capable of).. Save the file and restart GDM with ctrl+alt+backspace.
Then go to system->preferences->screen resolution as @thegreenblob explained and the 1280x1024 resolution shuld be in list. Select it and enjoy. :)

---

### Post by h11g on 2007-09-06
> **peromalosutra said:**
> You need to change xorg.conf file.
First, jump to terminal and type sudo gedit /etc/X11/xorg.conf. Enter your password and press enter. This will open text editor. Scanf over the file until you find the lines containing list of resolutions (it will be pretty easy to spot them). At the begining of each line containing resolution list add "1280x1024" (or other resolution that you know your monitor is capable of).. Save the file and restart GDM with ctrl+alt+backspace.
Then go to system->preferences->screen resolution as @thegreenblob explained and the 1280x1024 resolution shuld be in list. Select it and enjoy. :)

do i replace the resolution in the "" ? because i did and once restarted some error message pop up and at the screen resolution, i couldnt see the resolution i added

---

### Post by h11g on 2007-09-06
Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024"
	EndSubSection

the above is the sample of resolution that i changed

---

### Post by peromalosutra on 2007-09-06
No, you dont need to replace anything, simply add prefered resolution(s) in front of the ones that alredy exists.. For example, this is one section of my xorg.conf file:

    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "640x480"

What kind off error message do you recive?

note:
 It would be a good thing to back up your original xorg.conf file before proceeding with it's modification (so you can restore to earlier state if something goes wrong).. SImply type in terminal sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup.

---

### Post by h11g on 2007-09-06
> **peromalosutra said:**
> No, you dont need to replace anything, simply add prefered resolution(s) in front of the ones that alredy exists.. For example, this is one section of my xorg.conf file:

    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "640x480"

What kind off error message do you recive?

note:
 It would be a good thing to back up your original xorg.conf file before proceeding with it's modification (so you can restore to earlier state if something goes wrong).. SImply type in terminal sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup.

oh crap, i didnt back up that file, but since mine only show one resolution, but at the menu i can choose between 3 resolution.

---

### Post by h11g on 2007-09-07
anyone can help me out here?

---

### Post by buzznot1012 on 2007-09-07
Thank you peromalosutra!  This worked like a charm for me.  I'm very new to Ubuntu, having been a grudging Windows user for years.  So far, I think Ubuntu is awesome.

Thanks again!

---

### Post by rajan on 2007-09-09
h11g, can you post your entire xorg.conf file? it'll be long, but we'll be able to scroll through it as long as you hit the pound sign in the upper right side of the posting window and put the file contents between the "code"s. 

i have had a lot of problems with the screen resolution not taking the changes that you enact on the system. just to make sure you're not making any mistakes, you should remember that most changes to your /etc directory (that's where your xorg.conf file is) require some sort of restart. this one requires a restart of X, which is the graphical frontend to your linux system. in order to restart after making changes, you should hit <control><alt><backspace>. NOTE: that's not control alt delete! make sure you hit the backspace instead of delete and also make sure you don't have anything important open on the desktop because your system is going down in a hurry. 

if this isn't the problem, then it'll be more difficult to diagnose, but I have heard of people having success with the X graphical system by taking away all the options in their xorg.conf file except for the one they're looking for. Definitely back up your xorg.conf before you do this (and it couldn't hurt to do the same with any data on the HD just in case). 

if neither of these fixes work, then hopefully someone more knowledgable than me can go over your xorg.conf file and figure out what's wrong. just keep in mind that this particular problem is one of the more difficult ones that i've found on linux so don't get discouraged easily.



EDIT: this thread seems to have a lot of information:
[http://ubuntuforums.org/showthread.php?t=529834](http://ubuntuforums.org/showthread.php?t=529834)

---

### Post by Detox06 on 2007-09-11
I have a dual boot Vista Ultimate/Ubuntu 7.04 computer. Compaq Desktop. AMD 3500+, 1GB RAM, 250GB, 2x200GB SATA drives not in raid, Soundblaster Audigy, EVGA Nvidia 7100GS 256MB. 

The issue I am having just started yesterday. Sunday night, I played City of Heroes on my Vista install. I shut the computer down and went to bed. Woke up monday morning, booted into Ubuntu to do some surfing before work. Computer was stuck in 640x480 @ 50hz. 

I looked at Xorg, all the resolution is in correctly for my resolutions. Tried updating nVidia driver via Envy. Xorg was corrupted by the update. Restored the backup, rebooted, still stuck in 640x480. I gave up, booted into Vista again and it worked right, so I don't think its a hardware issue. 

Before work I turned the computer off and left for my 8 hours. When I got home, Ubuntu worked fine. Correct resolution and everything. Booted to Vista, played CoH again, booted off after a couple hours and back into Ubuntu. worked fine. 

Woke up to surf before work today, Ubuntu was again stuck in 640x480 @ 50hz. Tried rebooting a couple times, didn't fix the problem. 

Any suggestions?

**<Edit> I also have not recently installed anything onto my Ubuntu partition. the only thing I have installed on my Vista partition recently was CoH. Don't think that shoulda messed up Ubuntu though.**

---

