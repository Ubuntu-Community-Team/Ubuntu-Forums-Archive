---
title: "HOW TO: Intel 965 + Compiz + Video"
date: 2008-02-25
forum: General Help
---

### Post by L815 on 2008-02-25
Ok I spent a decent amount of time just figuring out how to get compiz to work on my Intel GM965. Then I spent some more time looking for the fix for the video, which I did with unpleasant results (blocky video). Then I found how to get it all to work together just right.

I'll make this guide to maybe help those who are still struggling to get Compiz to work on Intel 965 while not sacrificing the video quality.

**[COLOR="Red"]This is a compilation of all the help I found around the boards, so the credit goes to them, I'm simply compiling it all in one post.[/COLOR]**

This is how I got it to work on my Laptop:
Specs: 
Vaio Fz240E
Intel GM965 Graphics
Sigmatel Audio
2GB Ram
250 GB HDD (Fujitsu I believe)
Intel Core Duo



[B]
First off, check to see if you can enable Compiz[/B]
 
System > Preferences > Appearance > Visual Effects and enable Extra

If it works, then you don't need to read any further :)



**Download Compiz Advanced Desktop Effects Settings**

Open Terminal and type or copy the following:
```
sudo apt-get install compizconfig-settings-manager
```

**Next, Skipping the check for blacklisted Intel 965:**
```
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager

```


**Next, try and enable the effects again in the Appearance settings**
If it works, then Compiz is now running and you can go to :
System > Preferences > Compiz Desktop Effects Settings and configure to your hearts desire


If need be press ALT + F2 and type:
```
compiz --replace
```

**For Emerald Theme manager open Terminal and type:**
```
sudo apt-get install emerald
```

Go to System > Preferences > Emerald Theme Manager to edit your themes


**To Get Videos to work with Compiz + Intel 965 without resulting to X11:**

We will be using XGL

Open terminal and type:
```
sudo apt-get install xserver-xgl

```

Reboot, and everything should be working OK



PS: If something is out of order, or something is advised against (with reasoning), let me know and I'll change it.

---

### Post by StiveG on 2008-03-07
Wow, many thanks, it works!!!

I tried almost everything before and no way to have the 3d desktop!! I have it now! Yes!!

---

### Post by danscali on 2008-03-10
Hi, I ran into a problem when i tried : sudo apt-get install compizconfig-settings-manager

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compizconfig-settings-manager

Could you show me how to fix this?
Thanks.

---

### Post by L815 on 2008-03-10
Do you have your Software sources checked?

System > Administration >Software Sources

Make sure these are checked:
Main
Universe
Restricted
Multiverse

---

### Post by danscali on 2008-03-10
I tried to run the software source but it did not give me any window to chech/uncheck things. When I selected software source, it asked me for the password then nothing show up. Do you know what's wrong? This is my first time using Linux.
Thanks.

---

### Post by L815 on 2008-03-10
I'm not sure why nothing showed up. I haven't encountered that problem. 
What version of Ubuntu are you using? 

Also, did you make sure that you put in the right password?

---

### Post by Nebetsu on 2008-03-11
I have the same problem. I can't find Emerald anywhere in the package manager and typing that in doesn't work. Everything is checked off.

---

### Post by sibidiba on 2008-03-12
Did not work for me. Running Hardy, everything is fine by default, except Compiz+Xv.

Installing xserver-xgl brings no change on the issue.

---

### Post by danscali on 2008-03-15
LT815:
 What does your graphic card driver show? Mine shows: Generic VESA- compliant video card. I followed the instruction but still can not set the Visual Effect to work. I have exact same model as yours. Thanks.

---

### Post by danscali on 2008-03-15
nevermind that, i got it to work now. 
Thank alot!!!

---

### Post by darth_indy on 2008-03-17
Thanks a lot! I have the Dell 1420n, and while it's worked perfectly, I've missed the extra eye candy. I've learned the hard way why the 965 is blacklisted though, and I've learned not to use certain features.

Another thing though; have you had problems working with multiple workspaces? I can only get one workspace, and switching to another crashes the machine. It's a feature I miss but can work without; if there is a solution, however, I'd really appreciate it.

---

### Post by L815 on 2008-03-17
About the works spaces, I don't know exactly where, but if you have the advanced settings manager, one of the options there will allow you to change how many you have. It's probably one of the ones related to work spaces. It will say something like 1 horizontal and 1 vertical. Just change it to the proper amount.

Or it's it's in the emerald theme manager.

---

### Post by darth_indy on 2008-03-17
I actually did try that, and it didn't work. It was originally set to 4 horizontal, 1 vertical (the number I had before activating Compiz) and it still crashed. I had to set it to 1x1 so I wouldn't be temped to switch workspaces and hence crash.

Then again, now that I look to try again, I can't find the setting. Maybe I changed it in the old workspace manager that goes on the toolbar (which I also disabled).

---

### Post by L815 on 2008-03-17
Hmm that's strange. I haven't played with work spaces much, maybe someone will come along who knows more  than I do.

---

