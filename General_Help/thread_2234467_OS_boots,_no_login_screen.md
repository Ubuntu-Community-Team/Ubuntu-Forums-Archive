---
title: "OS boots, no login screen"
date: 2014-07-14
forum: General Help
---

### Post by lisa_gibson on 2014-07-14
I had a theme that wonked up and added my taskbar and the dock together (makign either one impossible to click on) so I removed it and it removed my taskbar menu  completely. Along with other problems, i searched online and installed "Boot repair" which boot up and fixed it (its all good now :D ) problem is, every time I turn on my computer, it boots up (before the log in page does) . So my question is either, how to stop it from loading on boot or how to delete it completely from my system? I've only been on this OS for about a month so I'm figuring things out little by little.

edit: sorry I didn't post what the problem was in the title, some plug in on firefox caused the broswer to crash D;

---

### Post by P_THE_AWESOME on 2014-07-14
> **lisa_gibson said:**
> problem is, every time I turn on my computer, it boots up (before the log in page does) . So my question is either, how to stop it from loading on boot or how to delete it completely from my system? I've only been on this OS for about a month so I'm figuring things out little by little.
What is "it?" My guess (because you did a Boot Repair) it is GRUB asking you options like Ubuntu, Other options for Ubuntu, or Memtest86+. Boot Repair is intended to fix system that can't even get to the login screen. So, I'm surprised that Boot Repair fixed your problem.

In order to get rid of that screen, you need to run Boot Repair again. This time, click the little arrow for "Advanced Options." Make sure that the "Main Options" tab is selected. **_UNCHECK_ "Reinstall GRUB" and "Unhide boot menu.**"

I haven't done this in a while, _so if unchecking "Reinstall Grub" disables unchecking "Unhide boot menu," then don't worry and leave "Reinstall GRUB" checked._
[IMG]http://s11.postimg.org/pt2zv29sj/Boot_Repair_Advanced_Options_Main_Options_E.png[/IMG]
[SIZE=1]*Image from: [Boot-Repair (Ubuntu Wiki)]("https://help.ubuntu.com/community/Boot-Repair"). Edit by: [DaAwesomeP (P_THE_AWESOME)]("http://ubuntuforums.org/member.php?u=1861069").*[/SIZE]

---

### Post by lisa_gibson on 2014-07-15
hey thank you so much :D I did it and reboot and no reboot repair thing :D thank you

---

### Post by claracc on 2014-07-15
As you got fix your problem, please, mark the thread as solved with thread tools in the right upper part of the web page.

Thanks.

---

### Post by Bucky Ball on 2014-07-15
> **claracc said:**
> As you got fix your problem, please, mark the thread as solved with thread tools in the right upper part of the web page.

Thanks.

^^^
This.

And I have changed the title of your thread to help others. You can edit the title yourself anytime within half an hour of posting the thread (Edit first post and 'Go Advanced'). Anytime after that, ask staff to change it for you. You were lucky this time, but generic titles generally reduce your chances of getting support.

Good luck. ;)

---

### Post by P_THE_AWESOME on 2014-07-15
> **lisa_gibson said:**
> hey thank you so much :D I did it and reboot and no reboot repair thing :D thank you

Glad to help you. Please mark your thread as solved as the others have suggested.

---

