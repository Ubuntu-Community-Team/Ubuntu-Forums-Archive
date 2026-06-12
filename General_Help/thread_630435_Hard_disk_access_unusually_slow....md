---
title: "Hard disk access unusually slow..."
date: 2007-12-03
forum: General Help
---

### Post by psycho5 on 2007-12-03
Hi, everytime i boot up, after putting in my user name and password, it shows the little gnome image and starts to load gnome-volume-manager. This takes an unexpectedly long time to load.

After loading, anything I try to access in my .ext3 partition of my hard disk takes a long time to load. Atleast 5-7 seconds of idle time to open any folder/media/file. 
Any installed application has the same effect on loading, takes a few seconds of idle time (around 5-7) before starting up. I say idle because the hard disk doesn't spin and there isn't much ram activity. Once I open a folder after waiting, any sub-folders in the parent folder open normally, but still, opening a file in the sub-folder or parent folder will take unexpectedly long time. 

I tried viewing the system log in the terminal but nothing unusual happens when I open a folder or a program, no unexpected activity. 

The hard disk is an IDE 7200RPM Maxtor 200GB 

This slowing down happened suddenly after around 2 months I using Ubuntu. 
I've tried rebooting and logging out and logging as a different user, thinking something in my HOME folder would be causing this problem, but still the same. 

Anything that i try to access  in my windows xp partition in the SAME hard disk opens up in a flash.

My Specs:

AMD x2 +3600 
Asus M2A-VN motherboard
Nvidia 8600GTS 256MB 128-bit
1gb DDR2 667 RAM
IDE 7200RPM Maxtor 200GB


Someone tried to help in Xchat but still no luck. Can anyone please be of some assistance? Highly Appreciated.

---

### Post by eggdeng on 2007-12-03
Use the command ```
top
``` to check your CPU and memory usage as you access a file on the partition in question. It might tell you if some process is hogging resources.
If you haven't already, you can add a system monitor applet to the panel (right-click-> Add to Panel ->System & Hardware).

---

### Post by HermanAB on 2007-12-03
Some more things to investigate: 
This can be a problem with PAM, or a link pointing to a network share.

---

### Post by psycho5 on 2007-12-03
HermanAB

Please elaborate..what do you mean by PAM?

I checked the system monitor, no processes acting unusually. Everything seems normal when I open a a folder, except that my cpu usage for both processors goes from 2% to 20% then the folder suddenly opens.

---

### Post by HermanAB on 2007-12-03
PAM is the Pluggable Authentication Modules.  Whenever you access a file, even just for 'ls' the machine has to check your credentials and see whether you have permission to access the file.  If there is an authentication problem, then the timeouts on each and every file permission check can cause inordinately long delays.

PAM works well when it works and is pretty much impossible to fix when it doesn't...

Check your /var/log/messages file carefully - there should be some clues in it.

---

### Post by psycho5 on 2007-12-06
Okay I don't know about PAM that much, but here's something interesting:

I created a launcher on my desktop for my HOME folder and if I launch it from there, it opens very quickly, as it should.

---

