---
title: "Reinstall"
date: 2008-04-08
forum: General Help
---

### Post by renesis317 on 2008-04-08
Im new to linux, and thanks to this community, i got ubuntu working on my dell desktop flawlessly. Now its time to convert the dell laptop...


i effed something up during the envy ati driver install, the generic kernal wont boot...i just get some gibberish on the screen. I decided to reinstall, but the livecd asks me  for a username and password. Other people have had this problem, but a solution was never found. Can i reinstall ubuntu from recovery mode?

---

### Post by Slushdoot on 2008-04-08
If you're going to completely reinstall don't triger recovery mode.  Recovery mode dumps you into a minimal terminal session that would be useful if you wanted to change a few config files or something like that.

It's not too different from booting the failsafe kernel in Grub if you want to think of it that way.

I assume you're using 7.10.  With my Dell laptop 7.10 gave me all sorts of troubles trying to get the ATI proprietary driver working with the mobile X1300 graphics..  I tried the Hardy beta and it picked it up out-of-the-box with the restricted drivers mamager and got everything working in minutes.  If you can swing the download I think you should try that.

---

### Post by renesis317 on 2008-04-08
Im downloading the beta right now. How should i go about installing it?

---

### Post by renesis317 on 2008-04-08
I got hardy going...where is the restricted driver manager?

I tried to install envyng...it said...dependency is not satifiable: Python-Central

---

### Post by Crafty Kisses on 2008-04-08
> **renesis317 said:**
> I got hardy going...where is the restricted driver manager?

I'd assume in the same place, **System<Administration<Restricted Drivers Manager.**

---

### Post by renesis317 on 2008-04-08
the update manager just fired up....lets see what happens after the 455 updates....

---

### Post by Slushdoot on 2008-04-08
The Restricted Drivers Manager is now called Hardware Drivers.  It's still under System -> Administration.

---

### Post by renesis317 on 2008-04-09
theres is nothing in the hardware drivers window to choose from.

Should i use Envy?

---

### Post by Slushdoot on 2008-04-09
What does it return when you type
lspci
in a terminal window?

Have you enabled all the repositories in Software Sources?

---

