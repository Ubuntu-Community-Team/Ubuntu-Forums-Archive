---
title: "WINE questions on running applications"
date: 2007-03-26
forum: General Help
---

### Post by charish2k1 on 2007-03-26
Alright, here's the slew of questions: 

1) I was tinkering around with wine and in order to run calc.exe, I had to drag it into the WINE system32 folder and use ```
wine calc.exe
``` So, I was wondering this: for programs that I have installed on my Windows partition, (for example, Corel Paint Shop Pro 10), could I just take the folder and drag into the WINE program files folder and just run it straight from there? Or is it slightly more complicated than that?

2) While I was running calc.exe or even notepad.exe through wine from its system32 folder, I got this message: ```
libGL warning: 3D driver claims to not support visual 0x4b
``` Any fix for this? If it helps, my video card info lies within the image below: 

[IMG]http://img.photobucket.com/albums/v60/charish2k1/VideoCard.png[/IMG]

3) Is there any sort of like, GUI for wine rather than just having to run it from the Konsole? I like to have it around just for kicks and save the Konsole as sort of a backup (for example, sometimes Ubuntu won't respond to "Restart Computer" when I select it from the K-Menu, but "reboot" in the Konsole does the trink).

In advance, thanks for all the help and thanks to those that've been helping me in the random threads that I make since I'm a Linux nub >.>;

---

### Post by whitewizardcoder on 2007-03-26
First off, wine needs to be able to run your program.  You can check the status of the application you are trying to run by going to [appdb.winehq.org]("http://appdb.winehq.org") and searching for the app.  For the most part, if your program is fully supported, it should be able to run straight from your windows partition (without needing to copy anything).

You will need to have your partition mounted and then go into the wine configuration gui by running "winecfg" from the Konsole.  Click on the "Drives" tab and then click "Autodetect".  This should add a slew of virtual drives for wine to use.  Verify that it added your Windows partition as a drive.  If it didn't, click "Add" and then specify the path to where your Windows partition is mounted (should be something like "/media/hda#").

I'm not too familiar with how KDE runs things, but you should be able to navigate to the executable file, right click, and click "Open with...".  Specify to open the file with "wine".

Keep in mind, however, that some programs add a lot of dll files to the system32 folder on your Windows partition.  If you are unable to run the program with the above method, you can try the following: go back into the wine configuration gui and into the "Drives" tab.  Click on the "C" drive in the list and modify the path so that it points to your mounted Windows partition.  You can try running the program again, but if it still won't run, a fresh install of the app into the ".wine/drive_c" folder is probably the best option.

---

### Post by zvacet on 2007-03-27
you can put exe in .wine>C>program files and to start it 
```
winefile
```
C>program files>your exe<double click

---

