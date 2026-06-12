---
title: "Screen resolution all messed up"
date: 2013-09-15
forum: General Help
---

### Post by TimEnid on 2013-09-15
I turned on my pc this morning and it wasnt not running the proper display. The screen seems stretched out. I would post a screen shot of it, but i can not even see all my screen. Even as i type this now, the whole browser is not showing up. I wish i could give more details, but i'm not even sure whats going on here. Any suggestions?

---

### Post by CeejRab on 2013-09-15
My gracious you have a screaming PC. Sorry just noticed it in your signature, lol.

Have you tried a different monitor? Have you tried the monitor settings for resolution? Its possible that the monitor is set at like 640x480 and the computer wants to put out 1280x760. Just an idea!

Also have you tried a reboot? Ubuntu sometimes fixes graphical issues on boot... Try a live CD if you can and see if it does the same thing. If it does, its likely your monitor's settings. If not it may be a setting in your ubuntu install on the computer.

---

### Post by TimEnid on 2013-09-15
thanks, i actually have to update that sig.

yes, i tried rebooting and the monitor settings. I will try a live cd and see what happens. But, the thing is, when i boot my pc, i dont even see the bios screen. It just jumps straight to my login screen. I also noticed that when i shut down, a quick screen flashes showing some type of error or something. i cant make it out because it happens so quick.

---

### Post by TimEnid on 2013-09-15
i switched my hdmi cable to a digital cable, and that fixed the resolution, but the browser is still not showing completely. i can not access my sidebar.

---

### Post by CeejRab on 2013-09-15
Aha... So your launcher is hidden and you cant see all of firefox. 

This may help, press the windows key to open dashboard. Type "displays" and press enter. 

From here you can change the screen resolution and set the monitor/display type etc. Let me know if that makes a difference.

To temporarily see your unity launcher (sidebar), open dashboard with the windows key and type "appearance". Click "behavior" and choose which side of the screen you want the launcher on: top, bottom, left, right. This way you can put it on a side that you can access so youll be able to use the launcher until you fix the resolution issue.

If the resolution is the way you want it, then perhaps a hard reboot will fix the window issue. If not, you may have a problem with your window manager....  (hopefully not!)

As for the error message, not sure what to make of it... Have you tried hard rebooting the computer? (hold the power button so it just shuts off abruptly)

---

### Post by TimEnid on 2013-09-15
i can not see my top system bar. the one that shows the time, shutdown, etc. and when i press the windows key, nothing shows up. the slideout doesnt show.

---

### Post by CeejRab on 2013-09-15
oh my, how are you functioning!? hmm...

Try to open a terminal window with ctrl alt T

type the command "sudo apt-get update"

Then "sudo apt-get upgrade"

This will update your repositories and check for updates to the software.

Do you have a different monitor you can try plugging into? If you have a live CD it would be good to try and see how the resolution is on that.

---

### Post by CeejRab on 2013-09-15
You do have the normal unity desktop right? you havent switched to lxde or something? no theme changes that mightve caused issues?

---

### Post by TimEnid on 2013-09-15
> **Christian_Rabideau said:**
> oh my, how are you functioning!? hmm...

Try to open a terminal window with ctrl alt T

type the command "sudo apt-get update"

Then "sudo apt-get upgrade"

This will update your repositories and check for updates to the software.

Do you have a different monitor you can try plugging into? If you have a live CD it would be good to try and see how the resolution is on that.
Tried with a live cd and there was no issue.
I used the two commands above and it did not fix it. 
> **Christian_Rabideau said:**
> You do have the normal unity desktop right? you havent switched to lxde or something? no theme changes that mightve caused issues?
Yes, normal unity.

here is a screenshot of the issue. This is a shot of my entire pc screen. Those black spaces are the issue.
[IMG]http://i43.tinypic.com/2upsu8l.png[/IMG]

---

### Post by TimEnid on 2013-09-15
and when im at my login screen, everything looks fine. i can see the top panel just fine.

---

### Post by CeejRab on 2013-09-15
ok, thanks for checking those things for me. i'll be right back i have an idea....

---

### Post by CeejRab on 2013-09-15
Ok heres some progress hopefully, open a terminal window and type this command:

"gnome-control-center"

This will open your system preferences. Open the displays section if you can and try to choose a different resolution. Let me know how that goes.

---

### Post by TimEnid on 2013-09-15
> **Christian_Rabideau said:**
> Ok heres some progress hopefully, open a terminal window and type this command:

"gnome-control-center"

This will open your system preferences. Open the displays section if you can and try to choose a different resolution. Let me know how that goes.
tried that, didnt fix the issue. Im thinking there is an issue with my drivers for my graphics card, perhaps.

funny thing is, when i click in the black space, i can actually click something. its not showing, but there is something there.

---

### Post by CeejRab on 2013-09-15
thats wierd... in the gnome control center did you click additional drivers and see if your graphics card shows in there as one that needs updating?

If no one else comes along to offer some advice, id say try to backup your files and reinstall ubuntu... First right over what you have so as to preserve your files, and if that doesnt fix it then a full HD wipe with gparted from the live CD and a fresh install of Ubuntu.

I hope it doesnt come to that, but i cant think of any practical alternatives right now. Im sorry if i havent been much help :(

I'm subscribed to this thread and i will keep and eye on it and certainly post any further thoughts. I hope you can get it fixed soon!

---

### Post by TimEnid on 2013-09-15
> **Christian_Rabideau said:**
> thats wierd... in the gnome control center did you click additional drivers and see if your graphics card shows in there as one that needs updating?

If no one else comes along to offer some advice, id say try to backup your files and reinstall ubuntu... First right over what you have so as to preserve your files, and if that doesnt fix it then a full HD wipe with gparted from the live CD and a fresh install of Ubuntu.

I hope it doesnt come to that, but i cant think of any practical alternatives right now. Im sorry if i havent been much help :(

I'm subscribed to this thread and i will keep and eye on it and certainly post any further thoughts. I hope you can get it fixed soon!

my card shows up, and nothing else. the one thats selected is "using x.org x server.

I really dont want to reinstall. I will see if someone else has a suggestion. Thanks for your help.

---

### Post by CeejRab on 2013-09-15
*light bulb* have you used terminal to update xorg?

---

### Post by TimEnid on 2013-09-15
> **Christian_Rabideau said:**
> *light bulb* have you used terminal to update xorg?
no i havent.

---

### Post by TimEnid on 2013-09-15
> **TimEnid said:**
> no i havent.

the close, minimize and resize buttons arent even working.

i also get this error message when i try to check nvidia
> You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.
is this something i need?

---

### Post by CeejRab on 2013-09-15
ok, im really reaching here....

See this link if you can, and maybe try the command. It might help your situation. I think it may be a kernel issue so this command may do the trick.

[http://askubuntu.com/questions/144330/how-do-i-fix-this-half-screen-problem](http://askubuntu.com/questions/144330/how-do-i-fix-this-half-screen-problem)

---

### Post by TimEnid on 2013-09-15
> **Christian_Rabideau said:**
> ok, im really reaching here....

See this link if you can, and maybe try the command. It might help your situation. I think it may be a kernel issue so this command may do the trick.

[http://askubuntu.com/questions/144330/how-do-i-fix-this-half-screen-problem](http://askubuntu.com/questions/144330/how-do-i-fix-this-half-screen-problem)
i tried [COLOR=#333333][FONT=UbuntuRegular]sudo service lightdm restart and it reboot, but the problem is still there. Also, i have a message in the right corner of my screen that says "AMD Unsupported Hardware"[/FONT][/COLOR]

---

### Post by CeejRab on 2013-09-15
*Facepalm*..... Im still working on it, stay tuned for more ideas lol

---

### Post by TimEnid on 2013-09-15
Will this help?
```
ompiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
unity-panel-service: no process found
compiz (core) - Error: Another window manager is already running on screen: 0
compiz (core) - Info: Stopping plugin: core
compiz (core) - Info: Unloading plugin: core

```

---

### Post by CeejRab on 2013-09-15
this may be of some assistance....

[http://dwmallisk.blogspot.com/2010/01/how-to-adjust-ubuntu-screen-size.html](http://dwmallisk.blogspot.com/2010/01/how-to-adjust-ubuntu-screen-size.html)

---

### Post by CeejRab on 2013-09-15
a little bit, can you check this out? Try the commands mentioned at this page if youd like, im not sure if they will help you or not but it helped this person so its worth looking into at least right? :)

[http://www.linuxforums.org/forum/ubuntu-linux/139248-solved-bottom-half-my-screen-black.html](http://www.linuxforums.org/forum/ubuntu-linux/139248-solved-bottom-half-my-screen-black.html)

---

### Post by TimEnid on 2013-09-15
> **Christian_Rabideau said:**
> a little bit, can you check this out? Try the commands mentioned at this page if youd like, im not sure if they will help you or not but it helped this person so its worth looking into at least right? :)

[http://www.linuxforums.org/forum/ubuntu-linux/139248-solved-bottom-half-my-screen-black.html](http://www.linuxforums.org/forum/ubuntu-linux/139248-solved-bottom-half-my-screen-black.html)

```
tim@tim:~$ grep -i driver /etc/X11/xorg.conf
   Driver      "intel"

```

---

### Post by CeejRab on 2013-09-15
also this will reset unity (which i should have thought of in the first place, gnome is a fallback, unity is standard)

[http://www.liberiangeek.net/2012/10/reset-unity-in-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/10/reset-unity-in-ubuntu-12-04-precise-pangolin/)

---

### Post by CeejRab on 2013-09-15
> **TimEnid said:**
> ```
tim@tim:~$ grep -i driver /etc/X11/xorg.conf
   Driver      "intel"

```

you could replace intel with the name of your graphics card as was shown in the link where you got this command from- That may help.

---

### Post by TimEnid on 2013-09-15
> **Christian_Rabideau said:**
> also this will reset unity (which i should have thought of in the first place, gnome is a fallback, unity is standard)

[http://www.liberiangeek.net/2012/10/reset-unity-in-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/10/reset-unity-in-ubuntu-12-04-precise-pangolin/)
we have a winner. this fixed it. Thanks for the help.

---

### Post by CeejRab on 2013-09-15
Awesome! Youre welcome, glad it helped :)

God Bless

---

