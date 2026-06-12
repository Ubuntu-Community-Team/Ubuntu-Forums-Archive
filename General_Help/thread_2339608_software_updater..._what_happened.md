---
title: "software updater... what happened?"
date: 2016-10-10
forum: General Help
---

### Post by acefromspace on 2016-10-10
Software updater told me I needed security updates for my hardware, so I installed them and now my computer is running slower (I have not had many problems with updates before) My browser (mozilla firefox) is having issues, dim screen (to save power) is happening more often. My laptop is a bit outdated, but has been OK so far (I'm using ubuntu 14.04) Specs are: processor pentium 1.6 x 2, memory 1 gig. Would an upgrade to 2 gig memory help? I will be going to 16.04 soon, so do I need the 2 gig or should I stay with 14.04? I had a strange feeling about this update... didn't show me how many software will be updated and also how many megabytes the download would be. After updating I chose to do shutdown instead of restart (should be the same?) Anyone had issues with mozilla firefox being slower? What happened?

---

### Post by howefield on 2016-10-11
> **acefromspace said:**
> Software updater told me I needed security updates for my hardware, so I installed them and now my computer is running slower (I have not had many problems with updates before) My browser (mozilla firefox) is having issues, dim screen (to save power) is happening more often.

Have a look at the bottom of the /var/log/apt/history.log file for an idea of the packages that might have caused your issue, kernel package perhaps and also look in /var/log/apt/term.log for errors.

[code]My laptop is a bit outdated, but has been OK so far (I'm using ubuntu 14.04) Specs are: processor pentium 1.6 x 2, memory 1 gig. Would an upgrade to 2 gig memory help?[/quote]

You have tagged this thread as Ubuntu, so assuming that you are running the Unity desktop, those are on the bottom end of the recommended specifications. More memory will almost certainly help, do you know if the your machine uses "*swap*" - I'd expect it does. Run the top command in a terminal to see details.

>  I will be going to 16.04 soon, so do I need the 2 gig or should I stay with 14.04? I had a strange feeling about this update... didn't show me how many software will be updated and also how many megabytes the download would be. After updating I chose to do shutdown instead of restart (should be the same?) Anyone had issues with mozilla firefox being slower? What happened?

I'm not sure if [Low graphics mode]("https://insights.ubuntu.com/2016/09/19/low-graphics-mode-in-unity-7/") works in 14.04 but it might be worth a look if you move to 16.04.

---

### Post by acefromspace on 2016-10-11
I will go for the 2 gig memory. The graphics is: Intel® 965GM x86/MMX/SSE2 (laptop is toshiba satellite a205) I am using regular ubuntu 14.04 with unity desktop. Thanks for the tips... especially about the visual effects (don't care for that stuff anyway)

---

