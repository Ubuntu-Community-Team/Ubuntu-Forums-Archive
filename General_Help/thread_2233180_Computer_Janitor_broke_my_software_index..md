---
title: "Computer Janitor broke my software index."
date: 2014-07-07
forum: General Help
---

### Post by jackechanprime on 2014-07-07
Hey all,

Before I get started I just want to say thank you to anyone willing to help me with this. Anyway, I recently used the Computer Janitor program (which is believe was part of the default install, I'd just never touched it before). It seemed to work great until the end of it's cleanup cycle at which point error messages galore popped up. Apparently something went wrong when it tried clean a program/driver related to my Brother Multi-function printer (model: MFC-j615w if that's relevent, one of those scanner, fax, copy, printer, etc. deals). Now i've got error messages informing me that the software index is broken, and I can't install or remove programs. It tells me to run "sudo apt-get install -f" to fix the problem, but this command also fails. Error reporting also fails since brother drivers are, apparently, 3rd party software and not a part of the normal realm of ubuntu software.

I'm running Ubuntu 12.04 LTS with no serious mods, and 99% out of the box software. So, to be blunt... How do i dig myself back out of this pit I'm in? Luckily the thing still RUNS, but I have a nasty feeling it this might only be a matter of time before that changes. I will provide any information needed on request. Please help!

Again, Please and thank you!

---

### Post by Bucky Ball on 2014-07-07
Reboot and hit shift to get to the grub menu list. Choose the recovery kernel (should be second on the list and marked 'recovery'). After some business, you will end up at an options screen. Hit 'Repair Broken Packages'. After that, choose the option to drop to a root shell and try the 'sudo apt-get update' command there. Report any and all errors. 

If you have Synaptics Package Manager installed you can use that and run 'Repair Broken Packages' from the drop down menu (not sure which at the mo, but you'll find it). Synaptics will also tell you if you have broken packages in the info bar at the bottom.

---

### Post by jackechanprime on 2014-07-07
Results from synaptic:

edit &#8594; “fix broken packages”
Returns:
“Successfully fixed dependency problems”
Then,
Run update:
hit “apply changes” button
Returns:
“E: brscan: subprocess installed post-removal script returned error exit status 1”

After Running recovery kernal and update, and returning to standard OS boot up, Running Synaptic generates these errors:
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/BHL': No such file or directory 
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/BHL2': No such file or directory 
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/BHL2FB': No such file or directory 
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/BHLFB': No such file or directory 
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/BHMFB': No such file or directory 
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/BHminiFB': No such file or directory 
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/YL4': No such file or directory 
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/YL4FB': No such file or directory 
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/ZL2': No such file or directory 
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/ZL2FB': No such file or directory 
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/ZLe': No such file or directory 
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/ZLeFB': No such file or directory 
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData': No such file or directory 
rmdir: failed to remove `/usr/local/Brother/sane': No such file or directory 
dpkg: error processing brscan (--remove): 
 subprocess installed post-removal script returned error exit status 1 
No apport report written because MaxReports is reached already 
                                                              Errors were encountered while processing: 
 brscan 
E: Sub-process /usr/bin/dpkg returned an error code (1) 

I did some snooping and indeed, this location doesn't exist. Apparently my computer is trying to uninstall something that no longer exists anyway. How do you fix THAT?

---

### Post by ibjsb4 on 2014-07-07
Check this out

[http://ubuntuforums.org/showthread.php?t=1351793&p=8552668&viewfull=1#post8552668](http://ubuntuforums.org/showthread.php?t=1351793&p=8552668&viewfull=1#post8552668)

more here

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=brscan&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=brscan&sa=Search&cof=FORID:9)

---

### Post by jackechanprime on 2014-07-07
Ok, honestly, I kicked myself over this one. I had thought to do the exact same thing, but then I said to myself "naaaaw... it couldn't be that simple..."

If it wants a directory to delete, give it a directory to delete and all is suddenly well! It worked!
*facedesk*
Thanks guys.

---

### Post by ibjsb4 on 2014-07-07
Funny

I think that we all have been there and done that at one time.  I'm still doing it :)

I haven't use computer janitor since it wrecked my 8.o4 install.  I find bleachbit to be safe.

---

