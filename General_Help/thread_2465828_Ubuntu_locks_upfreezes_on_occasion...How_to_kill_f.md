---
title: "Ubuntu locks up/freezes on occasion...How to kill frozen app in Ubuntu?"
date: 2021-08-12
forum: General Help
---

### Post by adambond on 2021-08-12
From time to time, my computer will lock up/freeze up. Everything on the screen remains there, but its all frozen. Mouse included.  Im sure it is related to Firefox. 

I stay absolutely up to date on all my updates. 

My question, once locked up, how can i "kill" an application (in this case, Firefox).   Ive tried many different hotkey commands and nothing responds. Its truly locked up. I have to 
force shut down every time.  Its becoming more and more frequent, and getting annoying. 

Thanks in advance. 
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=288952&stc=1[/IMG]

---

### Post by tea for one on 2021-08-12
When this freeze happens, can you open a terminal with:-  **Alt F2** and try xkill
(xkill is a utility used for force-quitting GUI apps. It is handy when an application isn't responding or is causing your system to work abnormally)

Forced shutdown is generally not a good idea because it can encourage file system damage.

You can power off/reboot more gracefully with [COLOR="#0000FF"]REISUB[/COLOR], although it is not fully enabled in current Ubuntu versions.

Here is a method to enable the process by editing a system configuration file:-
```
sudo nano /etc/sysctl.d/10-magic-sysrq.conf
```
Then change the number in line 26 from 176 to 244 i.e. **kernel.sysrq = 244**

I found the solution at this site [https://digitalfortress.tech/debug/what-should-you-do-when-ubuntu-freezes/](https://digitalfortress.tech/debug/what-should-you-do-when-ubuntu-freezes/) and the information was in section 3.

By the way, the last letter in the process **B** reboots your system, sometimes you may want to power off completely by substituting the **B** for an **O**

---

### Post by adambond on 2021-08-12
Thank you. No ive tried Alt F2 and i get no response.  I will try the REISUB

---

### Post by adambond on 2021-08-12
Ive changed the value to 244, but not sure how to "enable".
 Or do i just close the screen.  I tested it by Alt+SysReq+F, and it only took a screenshot. So clearly 
i havent got it enabled.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=288953&stc=1[/IMG]

---

### Post by tea for one on 2021-08-12
Did you save the modified file?

Ctrl O to save
Ctrl X to exit

---

### Post by adambond on 2021-08-12
I didnt know that ^ meant "control".    Thank you. 

I tried "control O", 
Then it asks me to write a file name.  

Im gonna need a walk through. I have no idea.... :([IMG]https://ubuntuforums.org/attachment.php?attachmentid=288954&stc=1[/IMG]

---

### Post by tea for one on 2021-08-12
Hit your Enter key so that you save the file to the same place.

Then Ctrl X to exit

---

### Post by adambond on 2021-08-12
Ok. We are getting there. Thank you. im clearly a noob.  :)  

I got it saved as 244.  Exited out of the terminal. Tried alt-printscn-F   and B and all it still does is take a screen shot.  Seemed to have no effect. I reconfirmed, it is saved as 244.

---

### Post by tea for one on 2021-08-12
Try this:-

Boot into your system
Press and hold Alt
Press PrintScreen and release

Press R (leave a 2 second gap between each key press)
Press E
Press I 
Press S
Press U
Press B (or O to power off)

---

