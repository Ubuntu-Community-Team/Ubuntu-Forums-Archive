---
title: "Help with dual booting Xubuntu and Windows XP"
date: 2016-05-11
forum: General Help
---

### Post by st3v3nps2 on 2016-05-11
I have a desktop with Windows XP Media Center Edition on it. I installed Xubuntu 14.04.03 on it a while back from a live CD, onto a separate partition. The installation worked and everything works fine with Xubuntu. The only problem is that when I boot up the computer, the grub loader does not appear; it just boots straight into Xubuntu. I still want to be able to boot into XP. I know XP is still there because when I view my partitions with GParted, the XP partition is still there, untouched. I ran the Linux Boot Repair tool, but it didn't solve the problem.

I have the boot log at this link: [http://paste.ubuntu.com/14366754](http://paste.ubuntu.com/14366754)  so you knowledgable folk can look at it and see if there's any problems there. (the date on the boot log is old because my desktop has been like this for a while, I just haven't gotten around to posting about the problem until now lol). Anyone have anything else I can try to get things working properly? Any help at all is really appreciated.

---

### Post by oldfred on 2016-05-11
It shows this & you have entries in grub menu.
Found Windows XP Media Center Edition on /dev/sda1
Found Windows NT/2000/XP on /dev/sda2

Actually sda2 looks more like a recovery partition, so do not try to boot it.

Since you have multiple systems, grub menu should show up.
If not try holding shift key from BIOS until menu appears.

---

### Post by st3v3nps2 on 2016-05-12
Well, this might kind of derail the thread but actually, what I've figured out is that the GRUB Loader is working perfectly fine... it's just that I can't see it. My monitor is an HPvs17e and when I boot up my desktop, the monitor displays the HP splash screen fine, but when it gets to the point where it should display the GRUB loader, my monitor says "Input Signal Out of Range". Until now, I thought this was just the monitor adjusting before booting up Xubuntu, but if I press the down arrow key and hit enter, I can use the other options of the GRUB loader, including booting Windows XP. So I can use GRUB with a little bit of guesswork (I've already figured out that four presses on the down arrow key will get me to the option to boot Windows XP) but is there anything I can do to get my monitor to actually display GRUB? It would be nice to be able to see it lol.

---

### Post by oldfred on 2016-05-12
I have an HP 1903 monitor from 2006 and never had issues.

Grub used to try to use its own settings picked up from BIOS, but I believe it now tries to use the video mode from the Ubuntu install.

Does Ubuntu work once booted? Or still black screen? You just press enter or wait 10 sec & it will boot into Ubuntu if no other errors.

I assume it worked with live installer, or else you could not have installed?
What video card/chip do you have?

One user posted this, no idea what version as it was just a comment in my notes:
 After update, It had reset to the BIOS defaults, setting the video to ONBOARD and switching off the dynamic video memory allocation (manually allocating 32Mb instead of leaving it as AUTO). 

If you can boot post this:
      
 #To see video:
sudo lshw -c display
sudo lshw | grep -A 11 display
lspci | grep VGA
#Resolution:
xwininfo -root
xrandr -q

---

### Post by yancek on 2016-05-12
I had an "input not supported" message on booting Grub at one time.  Not sure if this will resolve it but my solution was to mount the partition and navigate to the /etc/default/grub file as root in a text editor and comment out the line below by removing the hash mark (#) and saving the file.

> #GRUB_GFXMODE=640x480

---

### Post by mastablasta on 2016-05-13
yancek's advice should work.

more info here: [http://askubuntu.com/questions/54067/how-do-i-safely-change-grub2-screen-resolution](http://askubuntu.com/questions/54067/how-do-i-safely-change-grub2-screen-resolution)

another option owuld be to set :
GRUB_GFXMODE=auto

make sure you run 

```
sudo update-grub
```

after changing the grub config file.

---

### Post by st3v3nps2 on 2016-05-13
Thanks for the replies all! I tried what yancek posted and it worked perfectly. I'm now able to see grub when I boot. Thanks again for the help everyone!

Edit: How do I mark the thread as solved? Can't seem to figure out how to do it.

---

### Post by oldfred on 2016-05-13
Quick answer is last line of my signature.

 Let us know what works and to mark your thread as [SOLVED] for new forum vb4:
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by st3v3nps2 on 2016-05-13
Alright, got it. Thread is now marked as solved. Thanks!

---

