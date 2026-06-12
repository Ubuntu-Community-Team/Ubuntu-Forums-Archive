---
title: "Beryl"
date: 2007-02-02
forum: General Help
---

### Post by battleroyalex on 2007-02-02
I see a lot of beryl posts but I'm still confused.

I am going to install ubuntu for the 2nd time. I actually got Counter strike source to run on ubuntu a long time back.. But I forgot EVERYTHING..


Can someone give me a step by step run through on what I have to do to install beryl on a laptop with a 7800GTX GO card. I'm not sure if they have the drivers?


Should I get unbuntu 6.10 or an older version?

---

### Post by MoLE on 2007-02-11
> **battleroyalex said:**
> I see a lot of beryl posts but I'm still confused.

Can someone give me a step by step run through on what I have to do to install beryl on a laptop with a 7800GTX GO card. I'm not sure if they have the drivers?


Should I get unbuntu 6.10 or an older version?

To answer the second question first, I would definitely recommend using the most recent stable version of Ubuntu - which would be 6.10 - the Edgy Eft.

Depending on your video hardware, I would recommend following one of the guides on the [Beryl wiki.]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu")

I used the "install Beryl on Ubuntu Edgy AIGLX" - which would be the preferred method for you with your video hardware (which is presumably nVIDIA based).

If you have any problems, then I would suggest posting in the Desktop area, and you may have more luck with responses.

---

### Post by reabralop on 2007-02-11
I went to that site to install it and I'm not following it too well. I'm either missing something or I'm tired of dealing with soo many hoops just to do something.

---

### Post by MoLE on 2007-02-12
What sort of problems are you having?  I'm happy to help walk you through it, but I think your expectations about the process are a little too high.  Beryl is *beta* software.  If you want to try out the Beryl experience hassle-free, there are live-cds which exist where all the hard work is done for you.

[http://www.ubuntuforums.org/showthread.php?t=349732](http://www.ubuntuforums.org/showthread.php?t=349732)

That said - I'm more than happy to help you through the process, if you can share the problems you are having.

---

### Post by reabralop on 2007-02-12
I guess the first question is how do I use it? I have it installed, I think. In my system tools drop down I have the Beryl manager and Beryl settings manager.  I get a settings window with the settings manager, makes sense, but when I select the beryl manager my computer just goes back to the log in screen. 
Truth is I don't know if it is truly installed. I don't know what all it can do but I know I want to be able to do the window transparency and maybe the cube thing. 

I want eye candy. I'm ready for a change in my viewing experience. I dual boot this machine and have a Mac. After a while all three really do LOOK the same.

That may be TMI but that's my goal.

---

### Post by madcow72 on 2007-02-12
Hey!  Wanted to make a quick suggestion.  The latest beryl has defaults for "Wobbly Windows" on, (and maybe some other effects) which may be causing X to crash, which is why you always end up at the login screen when you choose beryl-manager.  This was absolutely the case with my computer.  

Try this:  Before starting up beryl-manager, try opening up the beryl-settings-manager and disabling wobbly windows for a start.  "Visual Effects" -> Unclick "Wobbly Windows".  Then start beryl-manager.

This is all assuming, of course, that you've got your video card driver running properly and you're running a single desktop window with resolution below 2048...

Oh yeah, you may want to try disabling any other graphics intensive effects as well.

---

### Post by MoLE on 2007-02-12
Can you post your /etc/X11/xorg.conf file here as an attachment?  Open a terminal screen and type glxgears -printfps.  Do you see 3 rotating gears in a small window, or do you just get an error message?

---

