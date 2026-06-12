---
title: "running console applications from nautilus"
date: 2013-01-08
forum: General Help
---

### Post by ampetrosillo on 2013-01-08
Hi everyone,

I'm coding some very simple console applications for university work, but trying to run them from nautilus results in no output.

As opening a terminal each time is cumbersome and annoying, is there an easy way to automatically have the application running in a terminal?

---

### Post by rnerwein on 2013-01-08
> **ampetrosillo said:**
> Hi everyone,

I'm coding some very simple console applications for university work, but trying to run them from nautilus results in no output.

As opening a terminal each time is cumbersome and annoying, is there an easy way to automatically have the application running in a terminal?
hi
you can create in your ~/Desktop a file like this:

[Desktop Entry]
Version=1.0
Name=test
Comment=test
Exec=/bin/bash    # for /bin/bash use the path to your application
Icon=/home/richi/flippig/minixlogo02.png
Terminal=true
Type=Application
Categories=Utility;Application;
Name[de_DE]=test_ap

1. filename must end with .desktop
2. belongs to you
3. Terminal=true !!!!
4. but when your aplication exit the terminal will be closed
if you want you can copy the icon you used to the desktop
if you double klick on the icon the app will start in a terminal
ciao

---

### Post by JRV on 2013-01-08
Use alacarte to create a launcher.  
Change "Type" to "Application in terminal.
The alacarte program is called "Main Menu"
It is located in Applications=>System Tools=>Preferences.

---

### Post by sudodus on 2013-01-08
Yes there are several way to do such things.

0. You can easily open terminal windows by the hotkey combination (press all 3 keys at the same time)

***ctrl + alt + t***

1. It is possible to install a plug-in in Nautilus, to right-click and open a terminal window in the current directory.

2. You can make a .desktop file, that is clickable and will run your application in a terminal window.

3. You can have one or many terminal windows open and run the applications with & at the end of the command line. This means that they run in the back-ground (detached from the terminal window).

... (others may suggest more ways to work)

---

### Post by bhaveshnande on 2013-01-08
When you execute an executable file from nautilus, it asks if you want to run it in terminal.
[IMG]http://i.imgur.com/4rBkK.png[/IMG]
To make it executable, right click on your file > permissions > tick "Allow executing file as a program" and then double click on it.
What do you mean by you don't see the output?
Your program runs in terminal and terminal closes down automatically and that's why you don't see any output?
If that's the case, add a line at the end of your program which asks for user input, so the terminal waits for user input and you will be able to see your program output.

---

### Post by ampetrosillo on 2013-01-08
Thanks, but I'm using Ubuntu 12.10, and I don't have the familiar Applications -> System Tools menus (but I have to use the Unity lens, and searching for "Main Menu" doesn't yield any results).

Alacarte doesn't seem to be installed, I might as well install it, but if you can explain to me how to custom write a launcher (I haven't really understood, based only on [rnerwein]("http://ubuntuforums.org/member.php?u=972890")'s post, sorry), using simply a text editor, I might just do that.

I tried making a <whatever>.desktop file, but it doesn't seem to work.

Anyway, I'm doing console applications in C (ie. executable files), not shell scripts, so I don't get any dialog boxes such as the one referred to by [bhaveshnande]("http://ubuntuforums.org/member.php?u=1176681").

---

### Post by sudodus on 2013-01-08
Yes, custom write a launcher using simply a text editor :-)

---

### Post by JRV on 2013-01-08
> **ampetrosillo said:**
> Thanks, but I'm using Ubuntu 12.10, and I don't have the familiar Applications -> System Tools menus (but I have to use the Unity lens, and searching for "Main Menu" doesn't yield any results).

Alacarte doesn't seem to be installed, I might as well install it, but if you can explain to me how to custom write a launcher (I haven't really understood, based only on [rnerwein]("http://ubuntuforums.org/member.php?u=972890")'s post, sorry), using simply a text editor, I might just do that.

I tried making a <whatever>.desktop file, but it doesn't seem to work.

Anyway, I'm doing console applications in C (ie. executable files), not shell scripts, so I don't get any dialog boxes such as the one referred to by [bhaveshnande]("http://ubuntuforums.org/member.php?u=1176681").

I gave you instructions based on Ubuntu 10.10 bacause that is what it says in your user profile.
For 12.10 you will need to install alacarte, use the command:
```

sudo apt-get install alacarte

```
You can then search for either "alacarte" or "Main Menu" with the Unity lens to find it.

To learn how to write a .desktop file look at the existing .desktop files. 
They are in /usr/share/applications.  
The .desktop files you create with alacarte are in /home/USERNAME/.local/share/applications

---

