---
title: "How to search only files from 2014?"
date: 2015-02-04
forum: General Help
---

### Post by 171742 on 2015-02-04
Hello,

I got a folder X and want the search to show only files from 2014. How to do that, best without terminal?

Thanks!

---

### Post by Holger_Gehrke on 2015-02-04
What version of Ubuntu and what Desktop Environment are you using ?

On my system (Ubuntu 12.04 with Unity and XFCE) I have something named gnome-search-tool that can search for files by several criteria, with time of modification one of those.

---

### Post by blueridgedog on 2015-02-04
Open a command prompt/shell and:

cd /path/to/your/files
find . -type f -newermt "2014-01-01" ! -newermt "2014-12-31"

---

### Post by TheFu on 2015-02-04
Why fear the terminal?  Without it, you are missing out on 90% of Linux power.
I like blueridgedog's answer. Dump that into a script and you'd done, though I'd leave off the cd and have the CWD be assumed. More flexible that way.

'find' is one of those commands that can be simple or hard, depending on your needs. It is like a swiss army knife for locating things on a system. Well worth your time to learn, IMHO.

---

### Post by 171742 on 2015-02-04
Hello,

thanks, but I need to coop all these files to another folder. And I just dont have the time to learn to use the terminal. 
How to do that?

Ubuntu 14.4 lts

Thanks!

---

### Post by TheFu on 2015-02-04
find . ...... -exec cp {} /path-to-target-folder \'

Or you could use xargs as the target pipe for the output from find.

The terminal blows away point-n-click for power and flexibility. You'll waste more time fighting against it than the effort it takes to learn a few commands.   IMHO.  I know - I avoided the terminal for about 6 months.

[http://content.hccfl.edu/pollock/Unix/FindCmd.htm](http://content.hccfl.edu/pollock/Unix/FindCmd.htm) has examples.  BTW, I don't claim to "know" find. I lookup the answer I need in the manpage - WHEN I NEED IT.  The trick with Liunx/Unix is to know what is possible from a few hundred commands, not the details for any of them for how to do it.  When you need to know more, the manpage for every command has the details.

---

### Post by 171742 on 2015-02-04
Hello,

thanks for all, but can anyone give me a way without terminal? Please spare the rest for another thread.

Br,

---

### Post by Holger_Gehrke on 2015-02-04
> **171742 said:**
> 
thanks for all, but can anyone give me a way without terminal? Please spare the rest for another thread.


How are we supposed to know which tools are available to you if we don't know what version of the OS and what Desktop Environment you are using ? That's one of the reasons you're going to get told to just use a terminal, the command line tools are always available, no matter what your graphical user interface is  and stay the same no matter what language the system is set to use(well, the output might change slightly, but the name of the program, it's options and parameters don't).

The tool I mentioned in my previous post -- gnome-search-tool -- can search for files of a specified age-span and you can drag-and-drop the search-results into a directory in the file manager. **Attention**: if you just drag them, the files will be **moved**. To copy them, hold the Ctrl-key while dragging. I can't tell you where you can find this tool in your 

If all the files are in one directory -- not distributed into sub directories -- you can just set the file manager to give you a detailed view, sort this view by date by clicking on the header of the date column and then just manually select files of the right age.

---

### Post by 171742 on 2015-02-05
> **Holger_Gehrke said:**
> How are we supposed to know which tools are available to you if we don't know what version of the OS and what Desktop Environment you are using ? That's one of the reasons you're going to get told to just use a terminal, the command line tools are always available, no matter what your graphical user interface is  and stay the same no matter what language the system is set to use(well, the output might change slightly, but the name of the program, it's options and parameters don't).

The tool I mentioned in my previous post -- gnome-search-tool -- can search for files of a specified age-span and you can drag-and-drop the search-results into a directory in the file manager. **Attention**: if you just drag them, the files will be **moved**. To copy them, hold the Ctrl-key while dragging. I can't tell you where you can find this tool in your 

If all the files are in one directory -- not distributed into sub directories -- you can just set the file manager to give you a detailed view, sort this view by date by clicking on the header of the date column and then just manually select files of the right age.

Thanks,

how to I start this search tool? That seems to be it. I have got ubuntu 14.4.lts

---

### Post by Holger_Gehrke on 2015-02-05
> **171742 said:**
> Thanks,

how to I start this search tool? That seems to be it. I have got ubuntu 14.4.lts

**IF** it's installed (and I think it's part of the default install, it was on 12.04), it should be as simple as opening the dash, typing 'search' and clicking on it. If that **doesn't** work, try 'gnome-search-tool' on the command line to check if it's installed. If it's not, you should get an error message along the lines of "Command 'gnome-search-tool' not found". You can install it with 'sudo apt-get install gnome-search-tool' on the command line.

---

