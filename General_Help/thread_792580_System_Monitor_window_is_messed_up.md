---
title: "System Monitor window is messed up"
date: 2008-05-13
forum: General Help
---

### Post by pistos on 2008-05-13
My System Monitor window got messed up (see attached screen shot) after I had to force quit GIMP when it got hung reading a huge file.

Before force quitting GIMP, I tried to pull up the System Monitor (while GIMP was still running) so I could check out what was happening. When I did that, the attached screen shot appearance is what it looked like. Since the GIMP crash, my system monitor window looks like this all of the time. I have shut down the machine and restarted it with no change to the windows appearance.

Does someone know how I can fix my System Monitor window? Did a resource get damaged that I can replace or something? Thank you.

---

### Post by zenwalker on 2008-05-13
So that rainbow color display is on only for that app right? No where else? I think some thing for corrupted in that package, just reinstall it again. Try...

---

### Post by pistos on 2008-05-13
Yes, just that window is messed up. Everything else on my system is golden as far as I know.


I just did what you suggested (I think). Using Synaptic Package Manager I reinstalled the gnome-system-monitor package, but it did not fix my problem.  :(

---

### Post by pistos on 2008-05-13
Does anyone else have any idea how to fix this?

---

### Post by Rocket on 2008-05-15
My system monitor (sys mon) is the same and I cannot use it to kill any processes. Also once I start sys mon I cannot stop it with out logging out and back in again. Everything else appears ok. I did a Hardy upgrade from Dapper a week or two ago. I tried a reinstall of sys mon, still no good.
Help
Regards
Rod

---

### Post by pistos on 2008-05-15
I am able to still "use" my system monitor, by poking around, having to guess where the actual control areas are now in the dialog window, since the image no longer matches the underlying "hot spots" of the GUI.

I am able to close the window by right-clicking in the window title bar and selecting "close" from the menu. Are you able to do that?

---

### Post by Rocket on 2008-05-16
You are quite right, I can use (and close) the sys mon by estimating the position each control is, roughly 20 mm to the right of the image of the control with my monitor. What type of video card are you using. I am using an ati/radion 9550, I have had problems using it with the ati drivers. I am using the "vesa" driver now. 
Regards
Rod

---

### Post by pistos on 2008-05-16
I too am using the VESA driver now because I had lots of other more serious problems with the ATI driver. I have an Acer Travelmate 8003 laptop with an ATI 9700 Mobility video card with 128 dedicated video ram on it.

---

### Post by wohenben on 2008-06-07
Did anyone find a solution to this? I have the same problem.

---

### Post by pistos on 2008-06-07
Not that I am aware of. I was hoping that one of the many system updates that have come out over the past couple of weeks might magically correct the problem, but my System Monitor window is still messed up.  :(

---

### Post by washburnello on 2008-07-18
I am having this problem as well. I have been running Ubuntu on my dell c600 laptop since edgy, upgrading as they came. I did a clean install when I went to Hardy. everything went fine except this distorted system monitor window. As mentioned before, the controls are in the right place and fully functional but the graphics are offset by the graphic distortion. I thought this  was exclusive to system monitor but the other day I tried installing Eagle circuit maker from add/remove.. The initial window that opens when i first ran eagle was garbled in the exact same way. ALSO. The font on my consoles (ctrl-f1-f6) is whacked out. looks kinda like it's only displaying the top two or three pixels of each character and their big and rectangular.
I don't know how to post a screenshot of my console or I would. Anyone got a command for that? Anyway, some help would be greatly appreciated.

---

### Post by pistos on 2008-07-18
FYI: My system monitor window is still messed up too. I keep hoping one of these system updates will finally fix the problem, but that has not happened yet.  :(

---

### Post by Rocket on 2008-07-18
Another bit of info.
I had a mishap, while attempting to partition a 16 gig flash drive with gparted late at night with my brain half asleep, I repartitioned the main drive of my hardy box. So I did a completed install of Hardy from fresh.
I no longer have the faulty system monitor display, so it is something to do with the upgrading to Hardy rather than a fresh install.
Regards
Rod

---

### Post by washburnello on 2008-07-18
Interesting. When I went to Hardy I did a fresh install. I'm still using this install and have the graphics issue. I might reinstall if I knew it had a good chance of fixing it.

---

### Post by pistos on 2008-07-18
Rocket, thanks for your input. But, unless I misread/misunderstood washburnello's post, he said that he had done a fresh install of Hardy and it happened to him. Curiouser and Curiouser.

---

### Post by washburnello on 2008-08-15
I just installed gnome-do today cause i thought it looked neat only to find that it's messed up like the system monitor. Pic is attached. i tried to get a pic of gnome-do but it won't let my print screen with it up.
Hope this helps someone cause this is really starting to get annoying.

Thanks in advance.

---

### Post by NathanKP on 2008-11-03
Did anyone here ever find a solution to their problem.  I am experiencing the same issue, also with an ATI Radeon graphics card. :confused:

---

### Post by sirebral on 2008-11-03
What is your video refresh rate.

If you have to 'judge' where the mouse is clicking it might be your refresh rate.

---

### Post by pistos on 2008-11-03
My System Monitor window is fixed since updating to 8.10. There was never any other solution for me. I am grateful that the update to 8.10 has installed a refreshed window and all is well.  :)

---

### Post by pistos on 2008-11-03
> **sirebral said:**
> What is your video refresh rate.

If you have to 'judge' where the mouse is clicking it might be your refresh rate.

My problem was not related to video refresh rate. I have a notebook computer with LCD screen. Somehow, the window layout code got borked. As I just said above, when I updated to 8.10 it was fixed. I was pretty sure that would be the case. I probably could have reinstalled that one component of code that spec'ed the layout of the System Monitor window, but I don't know enough to know where that component is in the system. So, I was basically stuck with having to live with it until an update was released. None of my other Ubuntu 8.04 systems ever exhibited this problem. Hope that helps.

---

### Post by NathanKP on 2008-11-03
I'm upgrading to 8.10 right now.  Its only too bad that the issue was never fully addressed in 8.04.

---

