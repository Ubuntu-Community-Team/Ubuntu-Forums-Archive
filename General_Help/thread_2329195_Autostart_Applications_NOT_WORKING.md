---
title: "Autostart Applications NOT WORKING"
date: 2016-06-28
forum: General Help
---

### Post by ronnie4 on 2016-06-28
Hello,
I have just installed lubuntu 16.04 64 bit. I have been trying to configure autostart for hours now and nothing is working. I ran a real vnc server on my old install (ubuntu 14.04) and it worked fine. I have tried using the GUI and adding the .desktop file by dragging and dropping AND the actual path and nothing happens when restarting or logging on. I have also manually added it to /home/bikini/.config/lxsession/Lubuntu/autostart and it still will not work. I also tried launching the sticky note application from there to test if it is just real vnc not working but NO applications are starting up automatically. I really need to get this sorted out as quickly as possible, any help would be greatly appreciated.

Thanks,
Ron

---

### Post by ronnie4 on 2016-06-28
fyi I am getting the directory from the .desktop file I want to auto start from /usr/share/applications

---

### Post by ronnie4 on 2016-06-28
I am also having problems with vnc, as when the computer goes to the lock screen (automatically after inactivity), when I connect with vnc it is just a black screen. Initially after installing I couldn't even get into the system because I manually had to download the correct intel drivers for my old onboard integrated graphics. I am starting to contemplate to switch back to ubuntu 14.04 as there are too many problems so far. Can I go to ubuntu 16.04 or will i have the same video issues as well? Everything worked like a charm in the old one, only upgraded because I needed to switch from 32 bit to 64 bit from a memory upgrade.

---

### Post by Dennis N on 2016-06-29
I always go to Preferences > Default Applications for LXSession.
Click on Autostart tab on left.
Enter the command to run your script or start your application under "Manual autostarted applications" in the box and click on Add. That should do it.

On your follow up, sorry, I don't know vnc.

---

### Post by ronnie4 on 2016-06-29
Hi Dennis,
Thanks for your response but as a said above it ignores anything in there and it does not auto start. I put the exact path to the .Desktop file under applications in there. Also I really think its support of the older intel hard ware is what is causing the glitch with the screen going black. The latest stable version real vnc supports is ubuntu 15.10. I think I may wipe my server again and go back to regular ubuntu. I like the light weight graphics package in lubuntu and figured it would be much easier on older hardware (core 2 duo, 4gb ram), but it is very buggy and I often get internal errors and errors with the pcmanfm file system. I wish they would make a version of regular Ubuntu that was exactly the same just simplified graphics. I'm sure it can be optimized for performance in settings somewhere.

---

### Post by Dennis N on 2016-06-29
Autostarted applications are shown in this file:

**~/.config/lxsession/Lubuntu/autostart**

The "Default Applications for LXSession" merely writes entries to the same file. These of course are per user and don't start until the user logs in. I have one entry and it does work in 16.04.

There is also **/etc/xdg/autostart** for general system autostart. In there are .desktop files.

---

### Post by ronnie4 on 2016-06-29
I will give the "**/etc/xdg/autostart" **a try as the autostart in the config didn't work either. Do I just drag and drop the .desktop file into the autostart config in **/etc/xdg/autostart **&#8203;?

---

### Post by Dennis N on 2016-06-29
> **ronnie4 said:**
> I will give the "**/etc/xdg/autostart" **a try as the autostart in the config didn't work either. Do I just drag and drop the .desktop file into the autostart config in **/etc/xdg/autostart **&#8203;?

It will require root privileges. My preference for that is just use the cp command in the terminal. But any way it works for you.

---

### Post by ronnie4 on 2016-06-29
Thanks for the help. One more question, when I would drag the file in the command/directory itself would include "File://" at the beginning. Should I type this in **/etc/xdg/autostart**or just put the exact path to the desktop file
ex:
[COLOR=#000000]/usr/share/applications/realvnc.desktop

or

File:/[/COLOR][COLOR=#000000]/usr/share/applications/realvnc.desktop[/COLOR]

---

### Post by Dennis N on 2016-06-29
Just so I am clear what is being done: You are going to copy a .desktop file from **[FONT=Courier New]/usr/share/applications/[/FONT]** TO **[FONT=Courier New]/exc/xdg/autostart[/FONT]**

You don't include anything in front of the actual file name, such as File://

Easiest way for this is open your terminal, and if the desktop file is **abc.desktop**

```
sudo cp /usr/share/applications/abc.desktop /etc/xdg/autostart/
```

Keep in mind this location is used for system files, and things that run in the background like a screensaver daemon , power manager, or update notifier, for example. So may or may not work.

---

### Post by ronnie4 on 2016-06-29
Wow it finally worked thanks Dennis! I'll have to further investigate this black screen bug at the logon, but at least it starts up now.

Thanks again,
-Ron

---

### Post by Dennis N on 2016-06-29
Good. I had my fingers crossed.

---

### Post by markackerman8@gmail.com on 2017-06-25
A different solution/Problem 

In Ubuntu-Gnome searching got me to Startup Applications, which has always worked in the past, but not now hmmmm??.

Since a recent re-install it is not working ...
Fix

Go to the Tweak-Tool (Gnome-Tweak-Tool)
and go to tab Startup Applications, and it works and is much SLICKER! too! ):P

---

