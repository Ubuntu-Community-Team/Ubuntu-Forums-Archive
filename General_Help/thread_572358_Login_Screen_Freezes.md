---
title: "Login Screen Freezes"
date: 2007-10-10
forum: General Help
---

### Post by XendlessXwishingX on 2007-10-10
Hi there, new member here. As much as I hate my first post to be one asking for help, I haven't seen a good enough solution for it not to be.

I messed around with some settings yesterday, and now I can't log in. The login screen fails to display. The screen just sits there with a spinning cursor on a black screen.

Getting to a command prompt, I can log in, and try to start the GDM and X window system, but both err out since they've already been started.

Every post with a similar problem has the user re-installing Ubuntu. I'd like *not* to do that. I also don't have access to a Live CD or the original install disk, nor can I download one (currently in Iraq where the internet speed in the common areas are the equivalent of 56K.)

Any help = :)

---

### Post by dabl on 2007-10-10
> **XendlessXwishingX said:**
> 

I messed around with some settings yesterday, and now I can't log in. 

Can you describe what you were playing with, generally?  It might help narrow down what needs to be changed back.

> 

The screen just sits there with a spinning cursor on a black screen. 

You've got a blinking "_" in the upper left corner of a black screen?  That's a classic broken x server indicator.

> 

Getting to a command prompt, I can log in, and try to start the GDM and X window system, but both err out since they've already been started. 

Which makes this last part of your report quite a mystery!

Not knowing any more, you probably can't make it any worse by reconfiguring the x server.  The console command (at your login prompt) is ```
sudo dpkg-reconfigure xserver-xorg
```

You didn't say what graphics chip you have.  There are two possibly ways to get this to work:

(a) on the first screen you say "YES" and it automatically detects and configures your X server display, or else (if that doesn't work)

(b) on the first screen you say "NO" and then on the second screen you mark "VESA" as your display type.

Then you can accept the defaults until you get to the "Monitor" section of the script.  There, you want to "x" only the resolution that you'd like to default to, and make sure when you get to "refresh" and "sync" that you set a range that is within the performance capabilities of your LCD or monitor.

"VESA" is pretty universal -- it should work, although it won't necessarily get the maximum performance out of your graphics chip.

Hope this gets you going!  :)

---

### Post by XendlessXwishingX on 2007-10-11
> Can you describe what you were playing with, generally?  It might help narrow down what needs to be changed back. 
I was trying to customize a few different things at the time, though I think it might have been whatever I did in the Login Window. 

I messed around with it more last night, and while not great, I've gotten it working a little better. Ubuntu now will boot into a terminal login:
```
Ubuntu 7.04 Laptop tty1

Login:user
Password:xxxx
user@Laptop:~$

```

Typing "startx" at the prompt, starts the GUI as if I had logged in normally. This should be fine, but...going to change anything that needs a root password to access, I get the following dialog box: (for System>Admin>Login Window)
```
Failed to run /usr/sbin/gdmsetup as user-root
Unable to copy the user's Xauthorization file
```

If I go into the Terminal, type in:
```
 user@Laptop:~$ sudo /etc/init.d/gdm start
Starting GNOME Desktop Manager                                        {OK}
user@Laptop:~$
```
I get a DOS-esque blue screen error saying: There appears to be an X server already running on disp :0. Should another be tried?

> (a) on the first screen you say "YES" and it automatically detects and configures your X server display, or else (if that doesn't work)

(b) on the first screen you say "NO" and then on the second screen you mark "VESA" as your display type.

If I select "YES", I get a black screen with the spinning cursor.
> You've got a blinking "_" in the upper left corner of a black screen?  That's a classic broken x server indicator.
Not the blinking "_", but the spinning "busy" mouse cursor in the center of the screen. My mouse can move it. Pressing "CTRL+ALT+F7" brings back the GUI to how it was previously.

If I select "NO", the screen returns to normal for a couple of seconds until the X server error screen returns. This will continue for 6 tries, return to normal for 2 minutes, and start over. To quit this, I have to go into the Terminal, type in:
```
user@Laptop:~$ sudo /etc/init.d/gdm stop
Stopping GNOME Desktop Manager                                        {OK}
user@Laptop:~$
```

Also, back in what appears to be a normal desktop, going shutdown the computer, there is no shutdown or restart option. Only Log Out, Lock Screen, Switch User, Suspend, and Hibernate. The CPU monitor still detects both cores, but the second core is at an inverse of the first: CPU #1: 4% CPU #2: 96%. As one rises, the other falls. This did not use to happen.

> You didn't say what graphics chip you have. 
Acer Aspire 5610 Notebook with Intel Core Duo 1.83GHZ processor and integrated Intel GMA945. 2GB RAM.

---

