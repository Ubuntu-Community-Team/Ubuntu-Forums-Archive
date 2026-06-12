---
title: "Newbie with install problems"
date: 2008-05-27
forum: General Help
---

### Post by ktashes on 2008-05-27
Alright, I've got a problem, and am completely new to linux. If this problem has been solved elsewhere, I'm sorry. I looked and couldn't find this anywhere, but I may just not have been searching right.

Alright, my problem: I just burned the Ubuntu iso to a disc and restarted my system to install linux. Everything started up to the splash screen absolutely fine. I can see the options for starting from the disc in live mode or installing it. Anyway, I clicked on install (and later on live mode with the same result) and it goes to the 'progress bar' screen (don't know what else to call it) and completes whatever it does there. Then, after it finishes the progress bar, my screen just goes black and my monitor gives me a resolution out of range error. I can hit ctrl+alt+f1 and get to the command line stuff, and I keep getting 2 driver errors there, one for my wireless card, and the other for b43legace/ucode4. I think it is for the wireless card too, though I'm not 100% about this.

Anyway, any help would be very greatly appriciated.
Thank you in advanced and sorry for being a complete newbie :S

-Ktashes

---

### Post by TWO on 2008-05-27
> **ktashes said:**
>  Alright, my problem: I just burned the Ubuntu iso to a disc and restarted my system to install linux. Everything started up to the splash screen absolutely fine. I can see the options for starting from the disc in live mode or installing it. Anyway, I clicked on install (and later on live mode with the same result) and it goes to the 'progress bar' screen (don't know what else to call it) and completes whatever it does there. Then, after it finishes the progress bar, my screen just goes black and my monitor gives me a resolution out of range error. I can hit ctrl+alt+f1 and get to the command line stuff, and I keep getting 2 driver errors there, one for my wireless card, and the other for b43legace/ucode4. I think it is for the wireless card too, though I'm not 100% about this.
-Ktashes

Just to make it a bit clearer, are you saying that you load the Live CD and then select 'install' from the desktop but an error message shows up or are you saying that after you have selected an option for loading the disc, the error message shows up?

If you could say what the specifications of your computer/ laptop are, that will be useful for anyone who can help you.

> Thank you in advanced and sorry for being a complete newbie :S

No need to apologise about being a newbie! Everyone has to start somewhere! :KS Although I don't suppose it matters much, maybe in future, whilst you're still unsure of things, ask questions in the "Absolute Beginner Talk!" People there hang around to help people just getting started!

Oh, and welcome to Ubuntu!:grin:

---

### Post by justleen on 2008-05-27
on the boot menu of the live CD there are several options at the bottom, accesible through the F keys.
You can use those to define a screenresolution and refresh. Change that to something you know your monitor supports.

---

### Post by ktashes on 2008-05-27
> **TWO said:**
> Just to make it a bit clearer, are you saying that you load the Live CD and then select 'install' from the desktop but an error message shows up or are you saying that after you have selected an option for loading the disc, the error message shows up?

If you could say what the specifications of your computer/ laptop are, that will be useful for anyone who can help you.

No need to apologise about being a newbie! Everyone has to start somewhere! :KS Although I don't suppose it matters much, maybe in future, whilst you're still unsure of things, ask questions in the "Absolute Beginner Talk!" People there hang around to help people just getting started!

Oh, and welcome to Ubuntu!:grin:

Thank you for the help,

My Specs are: I'm running a 5 year old hp pavilion with default specs minus an added Radeon 9200 video card. The computer has 512 ram, an AMD 3200+ processor, and 200gb hard drive. I have windows installed on it already, and am trying to install from the live cd (ie I start my computer with the live disc in and hit install at startup, though I've also tried going to the live demo mode and installing that way with the results I described above).

And what I mean is that I can't even get to the desktop. I get to the initial splash menu with options like install, check disc for errors, and boot from first drive. When I select install or boot into live mode, it goes out of my monitors resolution range.

And Sorry, I didn't know where to post it, so I just chose here. I'll remember that next time :).

> **justleen said:**
> on the boot menu of the live CD there are several options at the bottom, accesible through the F keys.
You can use those to define a screenresolution and refresh. Change that to something you know your monitor supports.

I tried to find it but wasn't sure it was in those options. I'll check again though and post my results. :)

EDIT: I just checked and I couldn't find the option to change my resolution anywhere. I'm on the 8.04 live disc (the newest one). If anyone can tell me which option its under that would be great! :)

EDIT2: Alright, I got it fixed. For some reason linux wasn't autodetecting anything about my monitor so I set everything up in xorg.conf file manually using [this guide]("https://help.ubuntu.com/community/FixVideoResolutionHowto").

Thank you, 
-Ktashes

---

