---
title: "Laptop Sleep/Suspend  Issue - Ubuntu 12.04 LTS"
date: 2012-12-15
forum: General Help
---

### Post by mur0j on 2012-12-15
Make: HP-Pavillion
Model: dv7-3169m
OS: Ubuntu 12.04.1 LTS
Video Card: Radeon 4650m

Like many laptop users, I was experiencing an issue where my laptop would not resume from sleep. I tried the fix reported [COLOR=Blue][here]("http://ubuntuforums.org/showthread.php?t=1978290")[/COLOR] to no avail. After many google searches and dead ends I finally came upon a solution that seems to be working.  I am hoping that I can shed some light on the problem for others, or at least point you in the right direction.

Please note that I am  NOT a Linux expert.  Please use caution when attempting any of the methods outlined below because you can potentially  damage your system.

OK,  with that said onto the good stuff.  After searching through the info pages I found that  a utility called pm-suspend  is responsible for executing the code necessary to suspend your computer (read it yourself:** open a terminal and type "info pm-suspend**"). The pm-suspend utility can take several options - referred to as quirks -- that can be used to force reset your video card and (hopefully) cause your display to turn on.  Here is a short snippet from the info page: >  On some hardware putting the video card in the suspend state and recovering from it needs some special quirk handling. With the --quirk-* options of the pm-suspend and pm-suspend-hybrid commands you can select which quirks should be used After quite a few failed attempts that resulted in reboots I found that the quirk that works on my system is **--quirk-s3-mode**. To force the use of quirks, you must specify an additional option to the pm-suspend command :  --quirk-test**. ** For example, the following command successfully sleeps/resumes my laptop.

```
sudo pm-suspend --quirk-test --quirk-s3-mode
``` [B]
DISCLAIMER: Please execute these commands at your own risk

[/B]If you find a quirk that works on your system then your halfway there. Ideally, you want to make sure that the quirk is used when you push the sleep button or when you tell the computer to sleep through the GUI rather than having to call sleep through the terminal every time. Unfortunately, I have not found a good solution for this yet. I find that when I try to add quirks they are disabled because my system is using a "kernel modesetting video driver." (You can check /var/sys/pm-suspend.log to find out what auxillary programs (hooks) are executed when pm-suspend is called.) The code that checks for this driver resides in  /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler. I manually edited the file and made sure that my quirk was not removed. Kind of a hack but I am not sure how else to do it right now. Any suggestions?

---

### Post by Toz on 2012-12-16
Hello, welcome to the forums, and thanks for sharing.

The problem with directly editing the /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler file is that if there was ever an update to the pm-utils package, your change would get overwritten.

You __should__ be able to create a file in /etc/pm/sleep.d (won't get overwritten) called (for example) **config** with the following content:
```
ADD_PARAMETERS="--quirk-s3-mode"
```
...or maybe:
```
ADD_PARAMETERS="--quirk-test --quirk-s3-mode"
```
...that should have the same effect. Sorry, but I can't actually test this.

Also, the video quirks database is located at /usr/lib/pm-utils/video-quirks. If you look at **20-video-quirk-pm-hp.quirkdb**, you'll notice that there is no entry for the DV7, which is probably why its not happening automatically. You could open a bug report against pm-utils to suggest that they update the database to include information for the DV7.

---

### Post by mur0j on 2012-12-16
Hey Toz, thank you for your feedback.

I tried creating a config file as you said but the quirks are not executed for some reason. 

I will open a bug report as you suggested.

---

### Post by Toz on 2012-12-16
Can you post back the contents of the file you created along with:
```
ls -l /etc/pm/sleep.d
```

As well as the contents of /var/log/pm-suspend.log after you try suspending with that file.

I'm curious, it should have worked.

---

### Post by pouchette on 2013-02-05
[EDIT]

FOUND THE SOLUTION !!! 

Hi mur0j, 
I see you didn't come bask to check this post, I had the same pb with a dev7 also.
So With your 2 (you and Toz) propositions, I finally find a way to make this config permanent :

Same Problem :

For me, the issue is on HP Pavilion Dv7 (and other many laptops I noticed), there are 2 annoying issues ; no wake up (resume) from sleep mode, and no shut down properly.
Have to hard reboot...

Ati/Amd graphic card for me (not tested on Nvidia but could work may be)

After reading several posts to fix it, and tried many many proposals that didn't work for me, I finally found a solution (till new updates or kernel will fix it a better way, we hope).

This problem comes from a lake a video quirk database for some pc

Here is what to do for make it work :

- Method with graphical super user mode :

> sudo nautilus (it will open your home folder with sudo permission)

1) browse to go and open the directory : system file /usr/lib/pm-utils/sleep.d

> then remove/delete the file "98video-quirk-db-handler"


2) Now, browse and open the directory : /etc/pm/config.d

> We have to edit a file in this directory

> open and edit a text file on your desktop that you name ADD_PARAMETERS

> type this line into the text file :

ADD_PARAMETERS="--quirk-s3-mode --quirk-vga-mode-3 --quirk-s3-bios --quirk-radeon-off " (including the quotes)

[NB : if you want to try this with Nvidia Card don't add -quirk-radeon-off]

> Save it on your desktop and close it

> then Drop the text file from desktop into the folder /etc/pm/config.d

(verify permissions of the file on "properties-permission menu" it has to be on root "read and write" for all 3 options)

Close the folder

reboot (or close session)

Done ! 

(Of course you can do all this procedure in a terminal console with root permissions)


It really works perfectly ! wake up from sleep mode and shut down properly !!


NB: not sure- but if upgrade of fglrx (ati driver) or getting a new pm-utility package from the update manager you might have to do this again, except if the updates did fix the issue :-)

That's it.

---

