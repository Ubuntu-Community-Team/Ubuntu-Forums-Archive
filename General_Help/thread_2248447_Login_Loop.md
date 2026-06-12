---
title: "Login Loop"
date: 2014-10-14
forum: General Help
---

### Post by jeff-aus on 2014-10-14
I need help. I cannot login to ubuntu.  Each time I enter my password, it presents with the login screen.
I have been several days without being able to login.  Up late trying to find a solution.

I have searched the forum and made a number of entries using the terminal.  Probably made too many changes, but nothing has worked.

I have moved and removed .Xauthority

I have chown .Xauthority

I have reinstalled xorg, and desktop manager.  I have installed a new desktop manager.

I have tried going back to an older version of Ubuntu, but still could not login.

I used an L-ubuntu CD to access my hard drive, but I could not do a single thing with any file as I did not have permission and I could not change permission.
At least by using the live CD I could see that basically everything inside appears to be as you would expect.

I am using Ubuntu Studio 14.04 LTS.  I also have unity, xfce and now 2 variations of GDM.  But selecting any of these makes no difference.  Still cannot get past login.

I can switch to terminal and there is no problem with login or password.  So if I can login through tty, why cannot I login through GUI?

I would really appreciate suggestions.

---

### Post by pissedoffdude on 2014-10-15
Hi,

Which display manager are you using? Since you said you have GDM, does that mean you installed gnome? Post the log of the display manager you're currently using.

Also, you can check if it's related to your local settings by doing a:
```
mv ~/.config ~/.config.old
mv ~/.local ~/.local.old
```

Also, what's the output of running a startx in a virtual console?

---

### Post by deadflowr on 2014-10-15
Do you have an option for a guest session at the login screen?
If so, does it also loop?

Have you tried to create a new user, and then tried logging in through that?

I ask these, so we can determine if it's a user setting problem, or a system-wide problem.

---

### Post by jeff-aus on 2014-10-15
I can login as guest.  This made me think the problem was in my home folder, which was i tried to fix by removing .Xauthority
I have not tried creating a new user.

Thanks

---

### Post by jeff-aus on 2014-10-15
Yes, I installed Gnome in one of my attempts to fix.  It made no difference.

I will look at local settings.

---

### Post by Bucky Ball on 2014-10-15
Remove .xauthority and .iceauthority, reboot and see if that gets you there.

---

### Post by jeff-aus on 2014-10-15
Hi
I removed .Xauthority and .ICEauthority.  Unfortunately, I still have login loop.
Following suggestion from deadflowr (see above), I added a new user.  But I could not login with the newuser.  Just goes back to login screen. I guess that is good news in a way.  I am expecting that means the problem is outside of my home folder.
Not sure where to go.

---

### Post by jeff-aus on 2014-10-16
Just wondering if anyone had any thoughts on whether a distribution upgrade from 14.04 to 14.10 would help solve login loop?

---

### Post by davit2 on 2014-10-16
Hi, try it.
 $ cd
 $ sudo apt-get install --reinstall xserver-xorg ubuntu-desktop
 $ sudo rm .Xauthority
 $ sudo reboot

---

### Post by Bucky Ball on 2014-10-16
> **jeff-aus said:**
> Just wondering if anyone had any thoughts on whether a distribution upgrade from 14.04 to 14.10 would help solve login loop?

I wouldn't go there. Install 14.10 on another partition if you want to find out. 14.10 is not released yet and has nine months support rather than five years when it is. Have you searched outside the forum? You mention you've searched the forum, but we are by no means the only resource. Try digging through [HERE]("https://duckduckgo.com/?q=login+loop+ubuntu"). It doesn't matter much the release. The fix is quite probably the same.

Common-ish problem. Happened to me a couple of times myself, but as I've mentioned, removing .xauthority and .iceauthority then rebooting fixed it. How are you removing them? You should try booting to the recovery option at the boot menu, when you get to the options, drop to a shell as root, then remove them. After that:

```
sudo reboot -h now
```

... and see what happens. Try this before reinstalling the desktop and xserver as instructed in the previous post! That might be a last resort ...

*

@davit2: what's the cd for? 

> **davit2 said:**
> Hi, try it.
 $ cd
 $ sudo apt-get install --reinstall xserver-xorg ubuntu-desktop
 $ sudo rm .Xauthority
 $ sudo reboot

You would need to run this with xserver stopped I'd think.

---

### Post by Alireza_Zamani on 2014-10-16
hi
can you share log messages from /var/log/ for that time to here ?

---

### Post by davit2 on 2014-10-16
cd - just to be sure, that you are in your home directory.
when your login screen is open, press Alt+Ctrl+F1(switch to command line mode) and go on with commands.

---

### Post by Alireza_Zamani on 2014-10-16
please share syslog from /var/log/

---

### Post by Alireza_Zamani on 2014-10-16
cd /var/log
cat syslog | less

---

### Post by jeff-aus on 2014-10-19
Thank you to all who helped.
I am now using my computer. Happy days.
So, for anyone who has been challenged by a similar problem, I want to share how I found a solution.
Whilst searching a link Bucky Ball suggested, I found some Kubuntu documentation that said a log in loop could be caused by a full file system.  I entered in recovery mode and deleted some unnecessary files. That was enough.
I could login again.
I found the actual cause of the disk space problem was a file that resulted from a failed video transfer.  This file was over 20GB from an original video of less than 1GB.  I was not even aware the file existed.  Now it is safely deleted, and i am back to having plenty of available disk space.
So, if you have a login problem and you have tried the fixes mentioned above like privileges and graphics driver, you might find that it is disk space.
i hope this helps somebody.

---

### Post by Bucky Ball on 2014-10-19
Happy days, indeed, and thanks for sharing. Good luck. ;)

---

