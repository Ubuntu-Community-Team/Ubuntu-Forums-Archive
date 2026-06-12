---
title: "log in screen font too big"
date: 2007-11-29
forum: General Help
---

### Post by rbprogrammer on 2007-11-29
when i go to type in my name and password on the login screen on ubuntu, the font is so big.  especially the dots when i type in my password.  so big, that my password is longer than the textbox has room for, so when i type it in it "scrolls" as i type, but i cant tell.

i have searched the forums for a bit and found that people have the same problem, but they have big font for the rest of the desktop environment (ie window titles, etc..).  my problem just lies in the log in screen.  all the other font sizes are fine but the login screen.

whats going on? and how do i fix this?? :confused:

---

### Post by TidusBlade on 2007-11-29
I would try looking around System> Admin> Login Window if I were you, seen a few custimization tabs there ;)

---

### Post by rbprogrammer on 2007-11-29
nope, i already tried that.  it did not have anything that would change the font size of the log in textbox.  but it seems as if, if ubuntu had the feature of changing the font size of that textbox, thats where it would be.  i think i might be out of luck..

*sigh :( ..

---

### Post by traf on 2008-04-14
I'm having the same problem. I had to set the Windows title font to 1 to get regular font size. I don't know how to change the login screen font size. I think it's multiplying the set font size by 10. So font size 1 is actually 10 and font size 10 is actually 100. That's my theory anyway. This only affects the login screen and the window titles. I have no idea why it is doing this. I have included a couple of screenshots.

---

### Post by bleaksquid on 2008-04-19
Same issue here, only it doesn't effect the tops of my windows, just the logic screen.

---

### Post by bert.thibault on 2008-04-20
I had the same problem. I found a fix that was posted on these forums and it works great.
[http://ubuntuforums.org/showthread.php?t=683035](http://ubuntuforums.org/showthread.php?t=683035)
Just have to edit gdm.conf file and add the -dpi 96 to 
[server-Standard]
name=Standard server
-command=/usr/bin/X -br -audit 0 -dpi 96
restart the system and login normally.
Many thanks to JorisGoudriaan for this fix.
I had been running 7.04 upgraded to 7.10 because if I installed 7.10 directly the exact
same problem occurred. I was disappointed when 8.04 did it also. I decided I would search
the forums to find an answer.
I am very grateful to JorisGoudriaan for taking the time to help others.

---

### Post by mooseydoom on 2008-04-25
Thanks for the fix.  I had the same problem installing Gutsy and Hardy on my Toshiba satellite m35x laptop.

---

### Post by dcstar on 2008-04-25
> **bert.thibault said:**
> 
......
I had been running 7.04 upgraded to 7.10 because if I installed 7.10 directly the exact
same problem occurred. I was disappointed when 8.04 did it also. I decided ......

Post the contents of your /etc/X11/xorg.conf file, it sounds like something didn't get autodetected correctly.

---

### Post by reaganf2 on 2008-05-22
Solved my large login font problem too... thanx...

---

