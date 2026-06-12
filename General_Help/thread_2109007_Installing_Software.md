---
title: "Installing Software"
date: 2013-01-26
forum: General Help
---

### Post by CAH5 on 2013-01-26
I am entirely new to Linux and have installed Ubuntu 12.04.1 LTS on a new hard disk.
I have tried to install a copy of VueScan. I downloaded vuex3292.tgz into the Downloads directory. From the Downloads directory, I ran tar -xzf vuex3292.tgz and it created a directory VueScan in the Downloads directory. I then ran ~/Vuescan/vuescan, which opened the program. I was able to enter my registration details and scan.
However, clicking the vuescan icon did nothing. I thought that this might be because it was installed in the wrong location. I moved the directory to the Home directory and tried to run it. It failed to run. I then moved it back and it still would not run. I then tried to delete the application with sudo apt-get remove --purge vuescan. The response was that it could not be found.
Is anyone able to help.
1 How do I remove my bad installation?
2 How should I install it again?
3 Where should it be installed and how do achieve this?
4 How do I set it to run from the icon?
5 How can I attach it to the Launch Bar?

This is the only application that I have tried to install.

---

### Post by Abhinav Kumar on 2013-01-26
> **CAH5 said:**
>  From the Downloads directory, I ran tar -xzf vuex3292.tgz and it created a directory VueScan in the Downloads directory. I then ran ~/Vuescan/vuescan, which opened the program. I was able to enter my registration details and scan.
Till this point you have just extracted from the tar file. You have not installed the program. An install would require a root permission.
```
~/Vuescan/vuescan
``` is just referring to vuescan application in Vuescan directory which is inside your home directory ( ~ means home directory)

> However, clicking the vuescan icon did nothing. I thought that this might be because it was installed in the wrong location. I moved the directory to the Home directory and tried to run it. It failed to run. I then moved it back and it still would not run. I then tried to delete the application with sudo apt-get remove --purge vuescan. The response was that it could not be found.
It showed so because the program has not been yet installed.

> Is anyone able to help.
1 How do I remove my bad installation?
Just go to the extracted directory. There should be some uninstall.sh file.
Run that in case you want to uninstall it.

> 2 How should I install it again?
Probably, there should be some install.sh file in the Vuescan directory.
Say you have moved to your home directory. Open a terminal and type
```
cd ~/Vuescan
sudo chmod +x install.sh
./install.sh 
```

> 3 Where should it be installed and how do achieve this?
Home directory is OK
> 4 How do I set it to run from the icon?
I think an icon should be shown on desktop for this.
> 
5 How can I attach it to the Launch Bar?
It can be easily added later to your launch bar

Regards,
Abhinav

---

### Post by omeomi on 2013-01-26
Did you make the file executable? If not, right click the file (vuescan) and choose Properties -> Permissions. On this tab you find an option to make the file executable.

In order to get it into the Launcher you first need to create a desktop entry for it. These are located in /usr/share/applications. Just look at the ones that are already there and then create a similar one for your program.

---

### Post by ajgreeny on 2013-01-26
I have just downloaded the application to try it, having read about it before, and having extracted the VueScan folder to my home, the vuescan file was already executable and the program ran after double clicking it.

There is no real reason to install it any further than you have, but do check that the file is executable, just in case it is not. If it will still not run, try opening it in terminal to see if any errors appear with command ```
/home/$USER/VueScan/vuescan
```

---

### Post by CAH5 on 2013-01-26
Thank you all for trying to help. Unfortunately, your suggestions have not enabled me to progress, for the following reasons.
1  Abhinav says it is not installed. However, it did run the first time.
2  No uninstall.sh file exists in the /VueScan directory. There are three files: vuescan, vuescan.8ba and vuescan.ds. Both are said to be shared libraries.
3  omeomi recommends that I right click the vuescan file and make it executable. It is already flagged as executable.
4  ajgreeny suggests running /home/$USER/VueScan/vuescan. The response is: No such file or directory.

Presumably, I installed it incorrectly and did further damage by moving the VueScan directory to /home and back.

Clearly files are present. The program has been run once, from the command line. How can I delete what is already present and how do I install correctly?

---

### Post by ajgreeny on 2013-01-26
[LIST=1]
[*]The program is not, and does not need to be installed.  The executable can be easily run from your home as long as you use the correct pathway for it, which is your current problem.
[*]If you had the VueScan folder in your home, the command I gave you would run the executable file, but looking closer, I see that the folder is  in Downloads so you need to use the command```
 /home/$USER/Downloads/VueScan/vuescan
``` or just ```
Downloads/VueScan/vuescan
```
[*]If you really want to get rid of what you already have you can simply delete the VueScan folder in your home (or wherever it is) and the hidden ~/.vuesan folder also in your home, but in view of the above, just keep trying
[/LIST]
Good luck with this. Just out of interest, why do you want to use this program instead of either simple-scan or xsane?  The latter of those is terrific with scanners which are recognised by the system; perhaps yours is not seen by xsane, but is by vuescan.

---

### Post by grahammechanical on 2013-01-26
I am a little confused. But then I usually am. You say that when you extracted veuex3292.tgz it created a Veuscan directory in the Downloads directory. You then moved the VeuScan directory to the Home directory and then moved it back again. Yes? Where to? The Downloads directory? So, the path would be ~/Downloads/veuscan/veuscan. Also remember, Linux is case sensitive.

Regards.

---

### Post by CAH5 on 2013-01-27
At last, I think I know why I am not getting anywhere. I found the following article:

[http://gastarbeiten.wordpress.com/2011/06/20/vuescan-doesnt-run-on-ubuntu-11-04-or-does-it/](http://gastarbeiten.wordpress.com/2011/06/20/vuescan-doesnt-run-on-ubuntu-11-04-or-does-it/) 

It claims that there is a bug in Compiz, which is causing my problem. This does not effect Ubuntu 10.10 but stops the VueScan window showing in version 11.04. I am running 12.04.1 LTS.

Following their suggestions, I have installed the CompizConfig Settings manager and disabled Windows Decorations. I have done this starting Ubuntu in normal and in Ubuntu 2D, which I assume to be the same as "Ubuntu Classic - no effects." In neither case does the VueScan window show but if I try to run it in Ubuntu 2D with Windows Decorations deselected, I get the VueScan start up Flash screen but nothing else. However, the icon turns red. Does this mean that it is running, even if I cannot see it.

What I cannot understand is how I managed to run VueScan properly, the first time it was installed. I did this in terminal with ~/VueScan/vuescan. I was able to insert the licence details and perform a scan. Unfortunately, I could never run it again.

Is there a way of getting Compiz fixed, if that is the problem.

ajgreeny asked why I wanted to use VueScan. I bought a licence for it after HP abandoned support for my scanner less than two years after I bought it. VueScan solved my problem. It scans to jpg, pdf, including multi page and has excellent OCR.

---

### Post by Cheesehead on 2013-01-27
> **CAH5 said:**
> What I cannot understand is how I managed to run VueScan properly, the first time it was installed. I did this in terminal with ~/VueScan/vuescan. I was able to insert the licence details and perform a scan. Unfortunately, I could never run it again.

You're running off on a tangent. The bug hypothesis is unlikely. If the (supposed, old) Compiz bug were relevant, VueScan would not have worked initially. 

ajgreeny is on the right track. You should answer the rest of his questions.

Did you move anything else?
Did you change any permissions?
Did you use sudo or gksudo when moving it?
When you put it back, did you use the original name (including proper case?)
What exactly is the current full path of your VueScan directory? Of the vuescan executable?
Do you still have the original download package or tarball?

---

### Post by CAH5 on 2013-01-28
Cheesehead says that I haven't answered ajgreeny's questions. I have tried to answer everyone's questions but here is the additional information requested.
1  All that I moved was the VueScan directory and its contents from /Downloads to /home. I then moved it back. I achieved this by right clicking on it and selecting "move folder."
2  I did not change any permissions. The file vuescan was already flagged as excecutable.
3  I did not use sudo or gksudo to move it.
4  I did not change any name or case.

I have now deleted the original installation including /.vuescan. I downloaded the .tgz file again, moved it to /home and extracted it there. It was after this that I tried Ubuntu 2D and deselecting Windows Decorations, as explained in my previous reply.

I note that ajgreeny is running Ubuntu 10, where VueScan installs and runs correctly. This would be in accord with the German experience, that I detailed before.

Has anyone experience of VueScan working in Ubuntu 12.04.1 LTS?

---

### Post by Frugal37 on 2013-02-13
I downloaded VueScan file vuex6492.tgz and VueScan would not execute.

Ed Hamrick, [email]vuescan@gmail.com[/email], has responded to my inquiries about VueScan on Ubuntu 12.04 as follows:
[INDENT]There are incompatibilities in shared libraries on Ubuntu 12.04

"You need to ask the people who produced Ubuntu 12.04 when they are going to fix this problem"
[/INDENT]We users need some help here.

---

### Post by Frugal37 on 2013-02-13
Ed Hamrick, [email]vuescan@gmail.com[/email], reports that there are incompatibilities in shared libraries on Ubuntu v. 12.04:

"You need to ask the people who produced Ubuntu 12.04 when they are going to fix this problem"

How do we communicate with those in the Ubuntu community who can address this issue?

---

### Post by CAH5 on 2013-02-13
I had already contacted Ed Hamrick. At that stage he had not tried a recent release of Ubuntu. It sounds as though he has now done so. I don't know how to get the issue escalated to the programmers of Ubuntu 12.04.

---

