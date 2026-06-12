---
title: "Login screen reloading self repeatedly (infinitly) after update"
date: 2008-03-20
forum: General Help
---

### Post by jimsmithkka on 2008-03-20
I just used the auto update earlier today, and needed to restart my laptop (dell Inspiron 600m)

after i restarted, the system boots up but when it gets to the login screen (in GUI with mouse) it brings up the Ubuntu banner and the login box then the screen goes back to the back ground color and it loads the box and banner again, and repeats like this untll i hold down power to shut the machine off, i can get into recovery mode command line, but when i do init 6 or startx it goes to that same login screen with the same issue.

One of the updates that was installed (gotten from another ubuntu box i have) was libkrb53, the kerberos update, haven't tried rebooting that system yet for fear of having the same issue

i cannot get into console screens on this laptop with the alt-ctr-F# keys (known prob) due to the laptops screen not loading the console prompts, issue with screen res switching, but is unrelated to this issue.

Any help would be...well helpful

I need to know where to look for error logs, i haven't mucked around much in ubuntu, but have done a bunch in fedora and centos.

---

### Post by deepclutch on 2008-03-20
it is a driver issue.login to a virtual console run "sudo killall -9 gdm"
now make sure ur video driver modules are modprobed.then restart gdm(/etc/init.d/gdm restart)

---

### Post by jimsmithkka on 2008-03-21
my virtual consoles are not working, and the system has no ssh server running either, 
also the video is not restarting, just the login (mouse stays on screen even with reloads)

---

### Post by deepclutch on 2008-03-21
so..just press "e" edit grub ubuntu kernel line,remo "quiet splash" press enter.
press "d" and remove the last line "quiet"
press "b" to boot.OKay?

---

### Post by jimsmithkka on 2008-03-21
no change, still is "flashing" at login screen

the screen does not go black between flashes, it just reloads the ubuntu title and the login box UI's, this only started happening after the last update yesterday, if i could be told how to recover the list of updates from the last update i might be able to uninstall them

---

### Post by jimsmithkka on 2008-03-21
if i could find the log file for the update manager i could remove the packages that were installed, or if there is a rollback function that would help as well.

Does anyone know about either of these possibilities?

---

### Post by Dakillakan on 2008-03-22
I am also having this problem.

---

### Post by jimsmithkka on 2008-03-23
BUMP

Reinstalling xorg, ubuntu-desktop, and gnome all have no effect, and somehow i know have edubuntu on the loading screen, stried also installing kde desktop, but that doesn't get to the login screen either, and when booting after removing gdm, i get no login at all (not even console login) and my setup has no virtual ttys, only the GUI in normal bootup (attached external monitor to test)

---

### Post by jimsmithkka on 2008-03-23
Ok, i resolved my problem, but it is not a solution to this problem

i backed up my hdd and reinstalled ubuntu from scratch and replaced my home folder and got all the GUI fun stuff back up.  

I hope that a Real solution is found for this issue, because i like ubuntu and the idea behind it, however a need for system checking should be implemented in the update form, or better information on what may cause this kind of conflict in a system in the update package descriptions.  

Also a recovery option in the CD installer would be a major improvement as well, i saw that it has been suggested and i hope that it is implemented in the next edition.

---

### Post by asteroid on 2008-05-25
I am having the same problem :( 
I am very new in linux and I don't know how I can fix that

Pls is there something I can try??
ty

---

### Post by jimsmithkka on 2008-05-25
the only way i found to solve this problem was to backup my home folders and  any config files i altered and reinstall ubuntu completely, reformatting the  ubuntu partitions.  Not really a asolution but if you are pressed for time it will work for the most part as far as i can tell. 

There should be guides else where in the forums on backingup and restoring.

---

### Post by asteroid on 2008-05-25
ty for reply 
I don't have the time to do that :(
I have to finish an essay for the university and I have a complex system installed :(
and I am very new at linux
I have upload a video [http://video.google.com/videoplay?docid=-3435908842394213101&hl=en]("http://video.google.com/videoplay?docid=-3435908842394213101&hl=en")
showing the exact problem

Pls pls pls help me fix it

---

### Post by deepclutch on 2008-05-26
well,I saw.but with xorg being complex with bullet-proof X it is really confusing.
what I will recommend is,to uninstall the xorg driver for your gfx card.let X reconfigure itself to the best option.
Now,if it fixed the problem,reinstall Xorg driver. :)

---

### Post by asteroid on 2008-06-03
I tried this but didn’t work unfortunately 
Thank you for your answer thought:)

---

