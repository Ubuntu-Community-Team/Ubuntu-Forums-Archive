---
title: "Forgot Password"
date: 2015-05-11
forum: General Help
---

### Post by david51 on 2015-05-11
Hi,

I just loaded Ubuntu onto my desktop (via USB). Before it boots into the desktop screen, it asks me for my user ID and password. The day before I loaded Ubuntu onto my laptop and created a user ID and password. Today, when I put in the user ID and password (to my desktop), I got an invalid password error. I am still logged in on my laptop (which is what I'm using to post this thread). Is there somewhere on the desktop screen I could find out what my password is? And if not, Is there a way to retrieve my password?

Thank you,

David

---

### Post by Bashing-om on 2015-05-11
david51; Hello;

A number of things can cause that condition, are you fairly sure it is a forotten password issue ?
If so, will not hurt to change the password and see what results:
Here are easy instructions to reset your password in Ubuntu:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

[INDENT]small steps
[INDENT][INDENT][INDENT]one at a time
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by david51 on 2015-05-11
Hi Bash,

Thank you for the quick response. I tried the psychocats password reset method and it did not work (the Recovery screen that came up has 2 options: 1) System Restore, 2) Factory Reset). I do see the Recovery option in the background but it's greyed-out by the 2 options I mentioned.

Now when I start the computer to boot Ubuntu, it only goes as far the first screen (the screen with "Ubuntu" and the 5 flashing dots underneath it, then the screen just goes blank and it does not respond to any command!

Somehow when I first loaded Ubuntu, I made it (inadvertently) dual boot (Windows XP/Ubuntu). I am thinking maybe my PC does not have enough memory for dual boot. But I don't know how to make Ubuntu to overwrite Windows XP instead.

David

---

### Post by Bashing-om on 2015-05-12
david51; Morning;

As advised, there could be a number of things at play here. From your last it appears to be a graphics driver issue. What release is this ? As 15.04 is a horse of a different color now to 14.04 .
> 
 I am thinking maybe my PC does not have enough memory for dual boot. But I don't know how to make Ubuntu to overwrite Windows XP instead.

Naaww; Dual booting will have no effect on memory usage as only one operating system at a given time is loaded into the available memory.

Following your thought process, let's examine the graphics issue.
Boot up the operating system to the grub boot menu, at this menu with ubuntu selected, press the 'e' key for edit mode -> boot parameters screen;
Arrow down to the line similar ( 14.04 ) to " linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=217ed9a7-e11a-4e32-8c05-992e8c8932b6 ro  quiet splash $vt_handoff " arrow across to "quiet splash" and add the term "nomodeset" - with out the quotes;
press key combo ctl+x to continue the boot process booting to the GUI, degraded graphics are OK at this point,

In the GUI -> Software Center -> software sources (menu)-> last tab is " Additional drivers" . install the recommended graphics driver.

Advise now of the status.

[INDENT][INDENT][INDENT]maybe yes 
[/INDENT][/INDENT][/INDENT]

---

