---
title: "trouble running a shell script"
date: 2008-05-09
forum: General Help
---

### Post by Kymus on 2008-05-09
I am in the process of following the guide posted on the forums to run Neverwinter Nights in Ubuntu. Part of this requires that I run a shell script (which I downloaded), but something is funky here and I can't get it to run. I went into the file's properties and clicked on "Permissions" and made sure to check "allow executing file as program". However, I think the problem may lay with the fact that it's trying to open the script with the wrong program. On the open-with tab, the options I've got listed are:

[LIST]
[*]dosbox
[*]Kate
[*]KWrite
[*]Purr
[*]Text Editor
[*]Wine Windows Emulator
[/LIST]

and that's it! Isn't this supposed to run in the terminal?

---

### Post by ibuclaw on 2008-05-09
Open up a terminal and cd to the directory where the script is.

ie: If the script is on your desktop
Type in:
```
cd ~/Desktop
```
Then to make sure that your script is there (in the terminal):
```
ls -1
```
A list of files and directories will be printed, if you can see you script, we can proceed!

To run the script, type in:
```
sh **script.sh**
```
Where "script.sh" is really the name of the file you wish to run.

Regards
Iain

---

### Post by Zorael on 2008-05-09
Hmm?

I've a small script I created myself in my home folder, and double-clicking it in Dolphin makes it execute properly. Going into the file's properties and disabling the executable flag makes it open up in Kate upon double-click. There is no "open with" selection to use with executable scripts.

You could, of course, try executing it in a terminal and see what happens.
```
$ cd locationofscript
$ ./scriptitself
```

---

### Post by songshu on 2008-05-09
if it is nagging that its not an executable just do

cd ~/Desktop
chmod +x ./scriptitself

---

### Post by ibuclaw on 2008-05-09
I could go one step further and say "**make sure that the script is on a filesystem that allows executing of files**". But I doubt the problem will be that deep.

Though, I had a similiar problem when I first setup a shared directory.
The fstab line read "**defaults,users**".
And by de facto standards, the command "**users**" envokes the "**noexec**" rule.

Adding "**exec**" fixed that problem. ("**defaults,users,exec**").

Regards
Iain

---

### Post by Kymus on 2008-05-09
thank you for the input, everyone. Is there a way that I can make it so this will automatically open up in the terminal when I double-click it?

---

### Post by rmdegennaro on 2010-02-16
Finally got a linux laptop and I'm running into the same issue.  Finally figured out that you need to create a .desktop file to the script file.  Seems silly to me, but I do remember something about users running scripts from unknown sources blindly.  Changes the way I have to organize stuff I do routinely.  Oh well....

Oh, and for others who aren't sure what I mean by creating a .desktop file:
[LIST=1]
[*]Open Dolphin
[*]Goto location to you want to keep file to launch
[*]Right click open space & select "Create New" -> "Link to Application"
[*]Goto application tab & find shell script.
[*]Click on advanced options & check "Run in terminal"
[/LIST]
You can't rename it when first creating it (another silly thing).  Another thing to remember is that you have to escape spaces on the command line (not done automatically, add "\" before space).  Oh, and the file name is not what you see if you add it to a folder that is viewed from a panel, its the name from the General Tab.

---

