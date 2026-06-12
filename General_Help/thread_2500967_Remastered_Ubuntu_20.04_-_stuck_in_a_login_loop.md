---
title: "Remastered Ubuntu 20.04 - stuck in a login loop"
date: 2024-09-17
forum: General Help
---

### Post by shorthaul on 2024-09-17
[COLOR=#000000][FONT=Arial]I had an Ubuntu 20.04 desktop that I remastered a number of years ago into a LiveUSB using Systemback . I have used the LiveUSB for years now on different computers and it has worked perfectly. I just built a new computer (AMD Ryzen 7700X) and when I try and boot the LiveUSB on that computer it gets stuck in a login loop.[/FONT][/COLOR][COLOR=#000000][FONT=Arial]

[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]At first when I tried booting it would bring up the boot screen where I select &#8220;boot live system&#8221; and after selecting that the screen would go black and stay that way.. I thought it might be because the original Ubuntu install that I remastered had a discrete AMD GPU (RX570) and this new computer was using the iGPU , so I put the RX570 from the old computer into the new computer and that seemed to fix that issue as it booted to the login screen. [/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]However, when I login the screen goes briefly black and then brings me right back to the login screen. Just to confirm the LiveUSB is still working correctly, I tried it on several other computers and have no issue logging in and using all of the programs I have setup on the LiveUSB. [/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]From the login screen I opened a terminal (CTRL + ALT +F3) and was able to login with no problem there but I can&#8217;t get to the desktop.[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Searching google for a solution to a login loop in Ubuntu brings up suggestions to check ownership of .Xauthority, to check permissions on the /tmp directory, and checking free hard drive space. [/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]I would assume (?) that none of those are my issue as the LiveUSB has been working fine for years on a number of different systems (Intel/AMD), it just isn&#8217;t letting me log in on the new computer, so I assume there is something about the computer build that is causing the issue but I don&#8217;t know what it could be. Just to test, I put an SSD in the new computer and installed Ubuntu 24.04 and it works perfectly.[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]I did look at the auth.log after trying to login, then opening a terminal and logging in there and running: sudo less /var/log/auth.log and this was the output (EDIT: sorry, it looks like the image is being downsized which makes it pretty unreadable):

[/FONT][/COLOR][IMG]https://ubuntuforums.org/attachment.php?attachmentid=294253&stc=1[/IMG]
[COLOR=#000000][FONT=Arial] 
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Does anyone have any idea why the LiveUSB would work on all other computers but not on the new computer? [/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]

---

### Post by shorthaul on 2024-09-18
So, I went back to my old computer and turned on auto login and then made a new LiveUSB of that system. I tested the LiveUSB on that computer and it booted right up to the desktop. I then tried the LiveUSB on a laptop and it booted right to the desktop.Then I took the LiveUSB to the new computer and it booted to the login screen with the same login loop issue?! 

What the heck is going on? How is it possible that a LiveUSB set to auto login does exactly that on every computer except for this new one? I'm pulling my hair out over this so if anyone has any suggestions I would love to hear them.

---

### Post by shorthaul on 2024-09-18
I figured it out, it turns out that I needed to explicitly disable the iGPU, it wasn't enough to have the dedicated GPU selected as the preferred GPU.

---

