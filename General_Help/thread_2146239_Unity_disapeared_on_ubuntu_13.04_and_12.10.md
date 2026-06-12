---
title: "Unity disapeared on ubuntu 13.04 and 12.10"
date: 2013-05-17
forum: General Help
---

### Post by MaxPayneFH on 2013-05-17
Hello,

The left icon bar and the top bar with the shutdown buttons and stuff just disappeared out of nowhere when I booted into 13.04 x64 today,
I tried restarting xserver but the screen just went blank for ages and didn't come back.
Also tried reinstalling nvidia drivers and unity but none worked out.
Startup applications and windows still show up thou, and I can still open up terminals.

So in the end I just used a clonezilla made image of 12.10 I had made before upgrading to 13.04 and the same bug shows its face.

The /home directory is in a different partition so I'm guessing it's something there that is causing this bug since 12.10 was working perfectlly when I made that clonezilla image a month or so ago.

Is there anyone out there that might be able to know what is the probable cause of this issue and how to fix it ?

Any help would be greatly appreciated.

---

### Post by ranger1021994 on 2013-05-18
I dont know whether this will help or not but have you tried resetting compiz and unity ?

Press ctrl+alt+f1
Login and type unity --reset

---

### Post by MaxPayneFH on 2013-05-18
I had tried unity --reset but I got a error message saying that --reset is now deprecated or something like that.

I did solve this issue thou, found the solution by accident on the list of questions in askubuntu

ran ccsm in terminal and enabled opengl and unity plugin after that the side and top screen bars came back.

Thanks for the help anyway, glad to know that at least someone tried to help.

---

### Post by bogan on 2013-05-18
Hi!, **MaxPayneFH**,

Have you tried logging in to fallback or on a Guest account, or a new second Administration account ? A lot depends if those work correctly or not.

Many users with this problem found the first code below to cure their display; others , me included,  had 'Can not open Display' or ' GLX not loaded' error messages and that, as well as many other ways to reset Compiz & Unity, failed. What worked for me was the second code below.

For other  suggested 'solutions' see my Thread in Ubuntu+1.
[http://ubuntuforums.org/showthread.php?t=2136435](http://ubuntuforums.org/showthread.php?t=2136435) Post #36

```
 sudo apt-get install dconf-tools
dconf reset -f /org/compiz/
unity --reset-icons

```
First Posted by Bogan ( Post #39):> My problem with 13.04 has been cured by using a terminal in Fallback  mode to enter the reset unity command included in Unity-Tweak-Tool:     

     ```
sudo apt-get install unity-tweak-tool 
echo $DESKTOP_SESSION 
fallback-compiz 
 gksudo unity-tweak-tool --reset-unity 
Warning: You are about to reset unity to its default configuration.
   It is normal for your desktop to flicker during the process.   
Type yes to continue, anything else to exit.    Do You wish to continue? _
```On rebooting all the log-in options were correct and with intact Launchers and Panels.

 
Running the same command when logged into the faulty Ubuntu/Unity Blank  Desktop gave a 'Can not open display' message and did nothing.

It is probable - though I have not tried it - that the other compix/unity reset commands would also work if run in the same way.Hope one way or the other works for you.

Edit: I see you found a solution before I Posted. Good for you.
Chao!,** bogan**.

---

