---
title: "How do I completely remove a program and all it's data in Ubuntu 12.04 ?"
date: 2013-03-09
forum: General Help
---

### Post by daldude on 2013-03-09
How do I completely remove a program and all it's data in Ubuntu 12.04 ? I installed a program called Minbar that keeps track of Muslim Prayer times and made the mistake of selecting an option in the programs settings "Minimize to tray" and now I con't bring up the programs window to disable that option and I tried uninstalling the program and reinstalling it and it still does the same thing as if it some how remembered it's settings. I tried running nautilus as a super user and selecting show hidden files and then doing a search for minbar and deleting all the files it found after uninstalling the program and rebooting and it still will not display the programs window to let me change it's settings so that means it is running minmized in the background but since 12.04 no longer has the tray I can't access the program to change it's settings. Is there a way to bring a program that is running in the background to the foreground that is running in memory and force it to be maximized or reset it to it's default settings? I even tried using synaptic package manager and doing a mark for complete removal and it still has the same problem I can't get the programs window to come up to change it's settings.:(:mad:

---

### Post by timgood on 2013-03-09
From a terminal type:

sudo apt-get remove --purge programname

Hope this helps.

---

### Post by ibjsb4 on 2013-03-09
Gksudo nautilus should of done the trick.  When you searched for leftover files were you in nautilus "Filesystem"?

[https://help.ubuntu.com/community/AptGet/Howto#Removal_commands](https://help.ubuntu.com/community/AptGet/Howto#Removal_commands)

---

### Post by schragge on 2013-03-09
Somehow, I don't think that purging the package will help. I guess the user preferences for minbar are kept in some subdirectory of the $HOME directory. *apt-get purge* doesn't touch $HOME. I'd rather suggest something like [s]*dconf-editor* from the package *dconf-tools* (for GNOME 3) or[/s] [gconf-editor]("http://manpages.ubuntu.com/manpages/precise/en/man1/gconf-editor.1.html") (for GNOME 2)[s], but TBH I don't know if settings for minbar will show up there[/s]. [highlight]Edit.[/highlight] minbar is a GNOME 2 application, so definitely try gconf-editor:
```

sudo apt-get install gconf-editor

```
Then **Alt**+**F2**, enter *gconf-editor*, open path *apps/minbar/prefs*, and uncheck *hidden*.

Alternatively, open a terminal and type
```
gconftool-2 -t bool -s /apps/minbar/prefs/hidden false
```

---

### Post by 3rdalbum on 2013-03-09
Although others are answering the thread title, what would be more useful is to be able to see the program's notification area icon.

 [http://m.webupd8.org/2011/04/how-to-re-enable-notification-area.html?m=1](http://m.webupd8.org/2011/04/how-to-re-enable-notification-area.html?m=1) 

This old article still applies to Ubuntu 12.10. You should also contact the developer of the program and ask them for Indicator support, as the notification area will be removed in 13.04.

---

### Post by fantab on 2013-03-09
> **daldude said:**
> How do I completely remove a program and all it's data in Ubuntu 12.04 ? I installed a program called Minbar that keeps track of Muslim Prayer times and made the mistake of selecting an option in the programs settings "Minimize to tray" and now I con't bring up the programs window to disable that option and I tried uninstalling the program and reinstalling it and it still does the same thing as if it some how remembered it's settings. I tried running nautilus as a super user and selecting show hidden files and then doing a search for minbar and deleting all the files it found after uninstalling the program and rebooting and it still will not display the programs window to let me change it's settings so that means it is running minmized in the background but since 12.04 no longer has the tray I can't access the program to change it's settings. Is there a way to bring a program that is running in the background to the foreground that is running in memory and force it to be maximized or reset it to it's default settings? I even tried using synaptic package manager and doing a mark for complete removal and it still has the same problem I can't get the programs window to come up to change it's settings.:(:mad:

The Application you are using will store its 'user preferences' in /home directory, and this file will be hidden. To reveal it you must hit Ctrl+H when you are browsing in /home. Just delete that particular .(dot)folder and you will be able to reset your preferences again. In case you don't find your hidden folder in /home then search /home/.config... (You don't have to be 'root' to do this)

Uninstall the application and

Then try:
$ sudo nautilus

And from the search bar search for the application in the Filesystem... delete all the files and folder you may find after you uninstall the application first.

---

### Post by schragge on 2013-03-09
> **fantab said:**
> Then try:
$ sudo nautilusPlease don't. Intstead, do ```
gksudo nautilus
``` See [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by daldude on 2013-03-09
FINALLY I fixed the problem. Thanks to all that helped. I used the configuration editor and found a option start minimized and unchecked that but at first I only saw an option that was labeled hidden and when I unchecked that and it did not solve the problem I was still frustrated but then after I settled down and studied all the options in the prefs folder I found the start hidden option:oops:#-o :redface: and unchecked it.:):smile::grin:=D>\\:D/

---

### Post by ibjsb4 on 2013-03-09
Good show :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

