---
title: "Help with installation and other things"
date: 2008-04-05
forum: General Help
---

### Post by Redls1bird on 2008-04-05
Alright,  Ive been using ubuntu for less than 12 hours, so please, be gentle.

First off, im trying to learn how to install programs and such, and running into problems.  I downloaded google earth, and currently its on my desktop in .bin format.  I have tried everything i can find on the web for resources on how to install it, but i just cant get it to work.  Ive tried "sudo" in the terminal, > sh googleearthlinux.bin in the terminal, and tried to understand the synaptics manager to no avail.  Can someone point me to a good guide to tackle this?

Also, does ubuntu have a "task manager" to control non-responsive programs?  THe word processor froze on me causeing me to have to reboot.

The final thing is with Firefox.  I am familiar with using it and love it.  I have one problem though.  On my machines running windows, using the backspace key while typing will simuiate pressing the back button on the browser.  I am very used to this feature.  On firefox in ubuntu however, it just scrolls up the page.  Is there a way to change this?

Thanks in advance for your patience and helping out a noob.

---

### Post by mikewhatever on 2008-04-05
Google Earth
[http://ubuntuforums.org/showthread.php?t=195382](http://ubuntuforums.org/showthread.php?t=195382)
[https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)
Just move the bin file to your home folder or change to the Desktop (cd ~/Desktop), whichever is easier. Don't go to Synaptic, cause downloaded installers aren't there.

Task Maneger
System>Admin>System Monitor.

Firefox backspace
[http://ubuntu.wordpress.com/2006/12/21/fix-firefox-backspace-to-take-you-to-the-previous-page/](http://ubuntu.wordpress.com/2006/12/21/fix-firefox-backspace-to-take-you-to-the-previous-page/)
[http://lifehacker.com/software/firefox-tip/set-backspaces-firefox-behavior-269945.php](http://lifehacker.com/software/firefox-tip/set-backspaces-firefox-behavior-269945.php)

---

### Post by Redls1bird on 2008-04-05
Holy fast response Mike.  Thanks alot.  ill give those a shot and report back if i still have problems.

---

### Post by Redls1bird on 2008-04-05
Well,  everything worked great.  Google earth crashes, but im not worried about that,  i really was just using it to learn how to install things.  so,  can anyone tell me what i did by following mikes commands?  im not sure why what i did worked.

" chmod +x GoogleEarthLinux.bin"  what is this?

---

### Post by mikewhatever on 2008-04-06
chmod +x made GoogleEarthLinux.bin executable.

---

### Post by BaffledMollusc on 2008-04-06
> **Redls1bird said:**
> Well,  everything worked great.  Google earth crashes, but im not worried about that,  i really was just using it to learn how to install things.  so,  can anyone tell me what i did by following mikes commands?  im not sure why what i did worked.

" chmod +x GoogleEarthLinux.bin"  what is this?

As mikewhatever said, it made the file executable. A file that is not marked as executable can't be run, which is a good security measure. The executableness of files is tied up with the file permissions system in linux (i.e. who is allowed to what to a file).

It might be worth gettting some background into this. See, for example,
[http://www.perlfect.com/articles/chmod.shtml](http://www.perlfect.com/articles/chmod.shtml)

Of course, using the command line is a slightly geeky and arcane way of playing with file permissions. A more user-friendly way is to right click on the filename in the file browser (i.e. choose Places->Home Folder, and navigate to the file) and choose "permissions". You can make all the changes there using a GUI.

---

