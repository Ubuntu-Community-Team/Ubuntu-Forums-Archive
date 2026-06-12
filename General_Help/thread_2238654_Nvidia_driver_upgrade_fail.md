---
title: "Nvidia driver upgrade fail"
date: 2014-08-09
forum: General Help
---

### Post by motorcity909 on 2014-08-09
Hi all

Yesterday, via the normal software updater, I installed the Nvidia driver 331.38.  All was fine and the computer ran all day with no problems until I shut it down before retiring for the evening.

This morning, I booted up my computer and it came up at a horrible resolution, something liked 1024x768, whereas I'm normally on 1920x1080.

I've reverted to the previous driver 304.117 and after a reboot all is fine again.

Shall I just leave it on the old driver or is there some magic to allow 331.38 to work?

Thanks as always
Dave

(PS - no need to suggest using Nouveau drivers - tried that before and resolution was poor and GPU temperatures rocketed to 70+ even on idle)

---

### Post by kc1di on 2014-08-09
Hi Dave (Nice name :) 

The 331 driver is for newer cards and the 304. xx driver is for most legacy cards.  So I'm assuming that the card in your machine is not so new.

your GT430 is listed under supported by the 304 driver according to Nvidia see [this page]("http://www.nvidia.com/Download/driverResults.aspx/77034/en-us")
look under support products and the 400 series. Though they list that card with the 331 driver it seems to only support it in windows , don't know why. 
So I'd stick with the 304 driver for now anyway.  Unless there is some compelling reason you need a newer driver.  Then I'd down load the latest one that supports the card from nvidia directly and do a manual install. 
Good Luck,
Dave :)

---

### Post by motorcity909 on 2014-08-09
Hi fellow Dave (splendid name!)

Many thanks for the reply.  I must confess that graphics cards and drivers is not exactly my field of expertise, just tend to install what the OS recommends.

There is no compelling reason for me to have newer drivers - in fact, there is no compelling reason for me to have a graphics card if I'm honest - I'm not a gamer so the onboard graphics would probably suffice.  For my next computer I'm seriously thinking of not having a graphics card and having a *really* good soundcard instead, as the PC is now the "music hub" of the house.

But I digress..... just one more question on the Nvidia driver, if I may.  The additional drivers list two versions of 304.117 - one is called 'nvidia-304' and the other is 'nvidia-304-updates'.  See attached.  I'm using the first one - is there any advantage in the second 'updates' one?

Thanks again
Dave

[ATTACH=CONFIG]255344[/ATTACH]

---

### Post by kc1di on 2014-08-09
I'm not sure what the difference is but[ this post]("http://askubuntu.com/questions/363835/nvidia-304-updates-vs-nvidia-304-and-similar") may be of help to you .

I've only used the stable 304 driver and never had problems with it.

---

### Post by motorcity909 on 2014-08-09
Thanks again, think I'll stick with the stable one.  If it ain't broke, etc etc.

Cheers
Dave

---

