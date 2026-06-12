---
title: "Ubuntu 14.04 can't run any installed app even from app center"
date: 2015-03-23
forum: General Help
---

### Post by kendinh8 on 2015-03-23
today is my first day using ubuntu.  i installed clean 14.04 download from ubuntu website. but somehow it only run the pre-installed app.  whatever i install won't launch.  I tried both from launcher and from terminal.  
so far i installed chrome,  and many app from app center.  none of them work.   it shows a icon on the bar, and then nothing happen.  running 64bit 14.04
plz help.  thanks

---

### Post by Keith_Helms on 2015-03-23
What happens when you click on the icon for something you installed?  Do you see little white triangles on either side of the icon afterwards?

---

### Post by kendinh8 on 2015-03-24
the icon just appear on the bar.  there is nothing else.

---

### Post by CaptainMark on 2015-03-24
Strange. You'll need to start a program through the command line to get an idea if there's any errors going on in the background. Tell us which applications you installed and well tell you what to do.

EDIT: I've just seen your newest comment about the icons appearing, it sounds like the applications are opening correctly, it must be some problem with them being hidden by in Unity somehow but I don't use Unity so can't help with that.

---

### Post by kendinh8 on 2015-03-24
ATTENTION: default value of option force_s3tc_enable overridden by environment.
libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast
[11069:11102:0324/024433:ERROR:channel.cc(305)] RawChannel read error (connection broken)


above are the error when i tried to run chrome from the terminal . For other apps, it just show an icon on the bar with no error message in the terminal.

---

### Post by Keith_Helms on 2015-03-24
Did you install the 64-bit version of Ubuntu?  What video card does your system have?  Did you change anything related to video drivers after the install?

---

### Post by kendinh8 on 2015-03-24
yes,  I'm running the 64 bit ubuntu 14.04 lts.  using ati raedon hd7770. i didn't change anything from the system.

---

### Post by efflandt on 2015-03-24
Did you actually "install" Ubuntu (on hard drive, ssd, etc.), or are you running the live system on a live/install iso booted from USB (or DVD)?

---

### Post by kendinh8 on 2015-03-24
i did installed it on my hard drive ,  running dual boot alongside Windows 7,

---

### Post by das280zx on 2015-03-24
Can you still boot a live usb and does that seem to work and load applications?  If so, I would try reinstalling Ubuntu since it doesn't really take all that long and you haven't had your system up long enough to miss anthing that won't be installed on the fresh install.

---

### Post by kendinh8 on 2015-03-25
i just upgraded to 14.10. it still doesn't work.  lool like the app still open as it shows the icon on the bar,  but nothing else.  for example,  when i open chrome,  it ask me if i wanna set it as default?  but then it won't go ro the browser.

---

### Post by das280zx on 2015-03-26
Did you upgrade from 14.04 using the update manager?  I recommend wiping your current setup and re-installing.   You could still have some bad setup files in there that were maintained if all you did was an upgrade.

---

