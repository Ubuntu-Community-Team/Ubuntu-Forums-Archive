---
title: "Issues / Questions I need help with"
date: 2017-09-09
forum: General Help
---

### Post by tobiasjohansson2 on 2017-09-09
Hello,

So I'm fairly new to the Ubuntu side of Linux (or well to Linux in general). I have a few issues, and some questions I would love to get help with to learn more, and be able to get completely away from Windows soon! :)

I've tried 4 different Ubuntu version (Lubunut, Orignal Ubunutu, Ubunutu budgie, Ubuntu Gnome). I'm currently running Lubuntu on my MacBook Pro (working great), and Ubuntu Gnome on my PC (until it died, so I need to get a new one). 

Issue:

In all of these I have an issue that it looks like in Software that I have 2 of some things installed. (I've attached two examples in the dropbox links). Is there anyway I can fix this? 
Uninstalling one seems to break it in some cases (probably because one is not really installed, and when I accidently picked the installed one it removes both). 

Image 01: [https://www.dropbox.com/s/b73j4sybk43l8bd/Selection_001.png?dl=0](https://www.dropbox.com/s/b73j4sybk43l8bd/Selection_001.png?dl=0)
Image 02: [https://www.dropbox.com/s/9x5e4y4hay94sx2/Selection_002.png?dl=0](https://www.dropbox.com/s/9x5e4y4hay94sx2/Selection_002.png?dl=0)

Questions:

1. How do I add start-up software in Lubunutu? 
I tried adding it in the Default Applications for LXSession, but either I added it wrong, or I need to add it somewhere else.
2. Is there anyway to get three finger swipes on the MacBook Pro touchpad working in Lubunutu? 
I installed Skippy XD (Mission Control software) and would like (if possible) to add the ability that when I swipe up with three fingers it runs Skippy XD. 

Thanks!
Tobias Johansson

---

### Post by RobGoss on 2017-09-09
Hello and welcome, it's best to add one question per **thread** in order to get the best help for each question, I'll try to answer your first question for you 

> 1. How do I add start-up software in Lubunutu? 
I tried adding it in the Default Applications for LXSession, but either I added it wrong, or I need to add it somewhere else.  

In Ubuntu you can add applications at startup by accessing  **startup application** please see the screen shots I've added below. Add the command for the application you want to add at startup

---

### Post by HermanAB on 2017-09-09
Uninstalling stuff is like unscrambling an egg.  The result is seldom satisfactory.  Best not done at all.  Just remove the unwanted things from the menu and be done with it.

---

### Post by Dennis N on 2017-09-09
> 1. How do I add start-up software in Lubunutu?
I tried adding it in the Default Applications for LXSession, but either I added it wrong, or I need to add it somewhere else.

You've got the right place. Maybe you added it wrong. The whole procedure is:

Menu > Preferences > Default Applications for LX Session > (Press) '**Autostart**' on left
On right, next to **Add** button, enter the command that will start the program. Press '**Add**'.
Reboot, and the program should automatically start on log in.

If the executable is not in a standard place (as shown by $PATH) you need to include the path to the executable.

---

