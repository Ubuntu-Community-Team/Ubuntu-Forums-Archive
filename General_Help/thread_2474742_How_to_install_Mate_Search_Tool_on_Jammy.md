---
title: "How to install Mate Search Tool on Jammy"
date: 2022-05-06
forum: General Help
---

### Post by Tom_Carr on 2022-05-06
I can't find Mate Search Tool in the software store, and when I go in the terminal and enter

sudo apt install mate-search-tool

It says unable to locate package

I know there  are lots of search tools available, but none that I know of are nearly as good as Mate.

---

### Post by dragonfly41 on 2022-05-06
I don't see it in Synaptic.
Have you tried Albert with Algolia Search in python extensions?

---

### Post by tea for one on 2022-05-06
Here is some info:-

[http://manpages.ubuntu.com/manpages/jammy/man1/mate-search-tool.1.html](http://manpages.ubuntu.com/manpages/jammy/man1/mate-search-tool.1.html)

[https://launchpad.net/ubuntu/jammy/+package/mate-utils-common](https://launchpad.net/ubuntu/jammy/+package/mate-utils-common)

---

### Post by Tom_Carr on 2022-05-07
I was using Mate search tool but apparently it is no longer available

I would like a search tool that lets me search:
All files in a given folder
That are greater or less than a given size
That were last changed before of after a given date
That contain a given string

For example, all files in folder XYZ that were changed after 6/15/2021 that are less than 10K in size and contain the string "Jerry"

This was easy to do with Mate search tool, but I have not found any other ap in the ap store that does it.

---

### Post by QIII on 2022-05-07
Threads merged.

---

### Post by QIII on 2022-05-07
You should be able to find mate-search-tool in [mate-utils]("https://packages.ubuntu.com/jammy/x11/mate-utils").

The Software Store is not as finely grained as using apt in the terminal, but you should be able to use

```
sudo apt install mate-utils
```

to install it.

You should also be able to install it using synaptic, which lists the following tools:

This package contains all the tools bundled as MATE utilities:
 - mate-disk-usage-analyzer, a disk usage analyser
 - mate-dictionary, a program which can look up the definition of words
   over the internet (including a panel applet to do the same)
 - mate-search-tool, with which one can find files by name or content
 - mate-system-log, a log viewing application
 - mate-screenshot, a tool to take desktop screenshots and save them into
   a file.

By the way: Note that you are looking for mate-utils, not mate-search-tool, in the package systems, which may be why you couldn't find it.

---

### Post by Tom_Carr on 2022-05-11
I installed mate-utils (see below).  It seems to have installed ok, but I still can't run mate search tool.

> tom@tom-OptiPlex-3040:~$ sudo apt install mate-utils
[sudo] password for tom: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gir1.2-gnomebluetooth-1.0 ltrace
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  libmate-panel-applet-4-1 libmatedict6
The following NEW packages will be installed:
  libmate-panel-applet-4-1 libmatedict6 mate-utils
0 upgraded, 3 newly installed, 0 to remove and 16 not upgraded.
Need to get 321 kB of archives.
After this operation, 1,174 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/universe amd64 libmate-panel-applet-4-1 amd64 1.26.2-1 [31.8 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/universe amd64 libmatedict6 amd64 1.26.0-0ubuntu1 [52.2 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/universe amd64 mate-utils amd64 1.26.0-0ubuntu1 [237 kB]
Fetched 321 kB in 0s (1,005 kB/s)   
Selecting previously unselected package libmate-panel-applet-4-1:amd64.
(Reading database ... 202534 files and directories currently installed.)
Preparing to unpack .../libmate-panel-applet-4-1_1.26.2-1_amd64.deb ...
Unpacking libmate-panel-applet-4-1:amd64 (1.26.2-1) ...
Selecting previously unselected package libmatedict6.
Preparing to unpack .../libmatedict6_1.26.0-0ubuntu1_amd64.deb ...
Unpacking libmatedict6 (1.26.0-0ubuntu1) ...
Selecting previously unselected package mate-utils.
Preparing to unpack .../mate-utils_1.26.0-0ubuntu1_amd64.deb ...
Unpacking mate-utils (1.26.0-0ubuntu1) ...
Setting up libmatedict6 (1.26.0-0ubuntu1) ...
Setting up libmate-panel-applet-4-1:amd64 (1.26.2-1) ...
Setting up mate-utils (1.26.0-0ubuntu1) ...
Processing triggers for desktop-file-utils (0.26-1ubuntu3) ...
Processing triggers for gnome-menus (3.36.0-1ubuntu3) ...
Processing triggers for libc-bin (2.35-0ubuntu3) ...
Processing triggers for mailcap (3.70+nmu1ubuntu1) ...
tom@tom-OptiPlex-3040:~$ 


---

### Post by &amp;KyT$0P# on 2022-05-11
> **Tom_Carr said:**
> It seems to have installed ok, but I still can't run mate search tool.

What does happen when you try to run it?
Do you see any related error messages if you run it from Terminal -
```
mate-search-tool
```

---

### Post by #&amp;thj^% on 2022-05-11
MATE Search Tool uses the find, grep, and locate UNIX commands. 
use:
```
whereis mate-search-tool
```
And:
```
ls -l /usr/bin/mate-search-tool
```
>  mate-search-tool [options]

       or select Search for Files...  from a Main Menu or from the Places menu in a Menu Bar
mate search man: [https://manpages.ubuntu.com/manpages/jammy/man1/mate-search-tool.1.html](https://manpages.ubuntu.com/manpages/jammy/man1/mate-search-tool.1.html)

---

### Post by Tom_Carr on 2022-05-12
It works when I run it from the terminal.  That basically solves my problem and is a "good enough" solution.  I would like to at least understand why I can't run it from the GUI.

---

### Post by #&amp;thj^% on 2022-05-12
I stopped using Mate on Ubuntu, but asked to see:
```
ls -l /usr/bin/mate-search-tool
```

---

### Post by &amp;KyT$0P# on 2022-05-12
> **Tom_Carr said:**
> It works when I run it from the terminal.  That basically solves my problem and is a "good enough" solution.  I would like to at least understand why I can't run it from the GUI.

The launchers in mate-utils package deliberately hide from non-MATE desktop environments.  If you would like to run mate-search-tool from GUI, you can copy [FONT=Courier New]/usr/share/applications/mate-search-tool.desktop[/FONT] into the directory [FONT=Courier New]~/.local/share/applications/[/FONT] (create this directory if it doesn't exist), then in your copy remove this line -
```
OnlyShowIn=MATE;
```

---

### Post by Tom_Carr on 2022-05-12
In response to 1fallen:

> tom@tom-OptiPlex-3040:~$ whereis mate-search-tool
mate-search-tool: /usr/bin/mate-search-tool /usr/share/man/man1/mate-search-tool.1.gz
tom@tom-OptiPlex-3040:~$ ls -l /usr/bin/mate-search-tool
-rwxr-xr-x 1 root root 160000 Aug 21  2021 /usr/bin/mate-search-tool




---

### Post by #&amp;thj^% on 2022-05-12
It's owned by root:
```
-rwxr-xr-x 1 root root 160000 Aug 21 2021 /usr/bin/mate-search-tool
```
halogen2 has a viable option in post #12

---

### Post by Tom_Carr on 2022-05-12
> [COLOR=#000000][INDENT]halogen2 has a viable option in post #12[/INDENT]
[/COLOR]


That is educational, but I will stick with a simpler solution.  I just created  a keyboard short cut, ctl-alt-s to run it.

Thanks everyone for your help doing this.  I will now close the thread.

---

### Post by Dennis N on 2022-05-12
>  I would like to at least understand why I can't run it from the GUI. 
Are you using Ubuntu MATE? (can't tell, since your marking it SOLVED removed the tag). 
If not then the reason it will not show in the applications list is because it is restricted to MATE by this line in it's .desktop file:
```
OnlyShowIn=MATE;
```
Comment out this line and it will show up.

---

### Post by #&amp;thj^% on 2022-05-12
> **Dennis N said:**
> Are you using Ubuntu MATE? (can't tell, since your marking it SOLVED removed the tag). 
If not then the reason it will not show in the applications list is because it is restricted to MATE by this line in it's .desktop file:
```
OnlyShowIn=MATE;
```
Comment out this line and it will show up.

+1
Also That shortcut you made may interfere with firefox screen capture.
Just a Heads Up. :)

---

