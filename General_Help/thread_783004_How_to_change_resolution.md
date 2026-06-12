---
title: "How to change resolution?"
date: 2008-05-05
forum: General Help
---

### Post by trowadeath on 2008-05-05
Hello, I recently installed Xubuntu on my school computer, and the resolution is stuck at 800x600 (I think) which is too low. In the configuration menu for display the only option it gives me for other resolutions is 640x480 but I would like to go up to 1024x768. I've done some looking on Google and no beans.

Guess that I should add that I am running Xubuntu with Virtualbox on XP.

---

### Post by Bruce M. on 2008-05-07
> **trowadeath said:**
> Hello, I recently installed Xubuntu on my school computer, and the resolution is stuck at 800x600 (I think) which is too low. In the configuration menu for display the only option it gives me for other resolutions is 640x480 but I would like to go up to 1024x768. I've done some looking on Google and no beans.

Guess that I should add that I am running Xubuntu with Virtualbox on XP.

Have you tried: Applications > Settings > Screens and Graphics ?

---

### Post by xavi1337 on 2008-05-08
unfortunately that option is not availible in the Menu on the Hardy release. I am very new to xubuntu and haven't found out where to find that program et, but it is certainly not in the drop down

---

### Post by FuturePilot on 2008-05-08
Did you install the Guest Addons? You won't be able to change the resolution until you do that.

---

### Post by xavi1337 on 2008-05-08
Guest add ons installed, but in the control panel i still only see default and 640x480 resoltuion options. There has got to be a different utility that i need to use but i can't find it.

This is something that Ubuntu needs to address. If they are going to have software installed by default then they need a way for a casual user to acess it. This is espectilly important for a system admin issue.

---

### Post by FuturePilot on 2008-05-08
Well it acts a little different when you're running it in a VM.
You're probably going to have to edit your xorg.conf
Post the output of
```
cat /etc/X11/xorg.conf
```

---

### Post by knownrider on 2008-05-10
> **Bruce M. said:**
> Have you tried: Applications > Settings > Screens and Graphics ?

This is actually correct!  With a twist...

You may need to tell the system what display you have.  This way the video card knows what resolutions and refresh rates are supported.  This is especially true for older monitors.

However, to get to the **Screens & Graphics** settings, do:

1). System > Preferences > Main Menu
2). In the **Other** submenu that you can activate is the **Screens & Graphics** option.  Activate this option, and apply.
3). Go to: Applications > Other > Screens & Graphics
4). Select your monitor from the menu, set your resolution and refresh rate, apply and reboot.

I have had this problem with several Ubuntu releases, and this is what fixes it for me.  Including with my latest install of 8.04.

I hope this solves your problem.  Perhaps in later releases these options will be more intuitive to find.  I may look into submitting a fix after finals.

---

