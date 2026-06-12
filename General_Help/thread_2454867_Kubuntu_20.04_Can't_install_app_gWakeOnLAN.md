---
title: "Kubuntu 20.04: Can't install app gWakeOnLAN"
date: 2020-12-07
forum: General Help
---

### Post by keijo-kukka on 2020-12-07
Hello Gurus!
I consider myself as a rookie in Linux and have started using Kubuntu 20.04 as my default OS only few months ago. Before Kubuntu I had Ubuntu 18.04 and I've also tried Debian 10.

I'm struggling while trying to install an app called "gWakeOnLAN" in my Kubuntu. See: [https://www.muflone.com/jekyll/gwakeonlan/english/](https://www.muflone.com/jekyll/gwakeonlan/english/)

I've used it before successfully while in Ubuntu 18.04, but I can't get it to install in Kubuntu 20.04. There seems to be only one installable Debian package (gwakeonlan_0.5.1-1_all.deb) which is pretty old version: [https://www.muflone.com/gwakeonlan/english/download#tabs|Tabs_Group_name:Tab_v051](https://www.muflone.com/gwakeonlan/english/download#tabs|Tabs_Group_name:Tab_v051)
To my understanding the problem is that this Debian package requires python-gtk2 (>= 2.12) dependency which I'm missing. My only current installed Python version is 3.8.5.

The error message I get while trying to install it via **sudo dpkg -i** command is below:

[FONT=monospace][FONT=monospace][COLOR=#000000]$ sudo dpkg -i gwakeonlan_0.5.1-1_all.deb [/COLOR]
Selecting previously unselected package gwakeonlan. 
(Reading database ... 326292 files and directories currently installed.) 
Preparing to unpack gwakeonlan_0.5.1-1_all.deb ... 
Unpacking gwakeonlan (0.5.1-1) ... 
[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] dependency problems prevent configuration of gwakeonlan: [/COLOR]
 gwakeonlan depends on python-gtk2 (>= 2.12); however: 
  Package python-gtk2 is not installed. 
 gwakeonlan depends on python (>= 2.5); however: 
  Package python is not installed. 

[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] error processing package gwakeonlan (--install): [/COLOR]
 dependency problems - leaving unconfigured 
Processing triggers for man-db (2.9.1-1) ... 
Processing triggers for desktop-file-utils (0.24-1ubuntu3) ... 
Processing triggers for mime-support (3.64ubuntu1) ... 
Errors were encountered while processing: 
 gwakeonlan
[/FONT][/FONT]
Could someone please confirm me that is the problem the missing Python version [FONT=monospace][FONT=monospace]python-gtk2 (>= 2.12)[/FONT][/FONT]?
Can I install the older version of Python (2.12?) along with my current Python 3.8.5 and should I do it? Should I expect any conflicts with two installed Python versions?

There seems to be also a tarball ([gwakeonlan-0.7.0.tar.gz]("https://github.com/muflone/gwakeonlan/releases/download/0.7.0/gwakeonlan-0.7.0.tar.gz")), which is also much newer version, but I am not sure how to install tarballs correctly in Linux. I'd be glad to have the most recent version rather than the old Debian version.
Would you recommend to install the tarball version instead of .deb version and how should I do it?

Thank you very much!

---

### Post by CatKiller on 2020-12-07
Python 2 is definitely dead, and messing around with Python versions can cause severe knock-on problems if it goes wrong; all the package management is done with Python. So I'd advise against messing with that.

I use wakeonlan, which is still in the repositories, and uses Perl. It's just a command line tool for sending the magic packets and is easy to use.

---

### Post by keijo-kukka on 2020-12-16
Okay, thanks for the reply CatKiller! I trust your advise and forget the legacy Python version. I also did install wakeonlan from repo and it works okay. I just think app with GUI would've been more convenient in this case (takes less time to open an app and click the option instead writing a command).

---

### Post by CatKiller on 2020-12-16
Every command is scriptable.

The .desktop files that launch *everything* GUI-based on your system - applications, panel widgets, context menus - are just text files. You can create one for your wakeonlan command and stick it anywhere that's convenient.

Also, even if you're writing the command in the terminal, it remembers what you've already written and can fill things in with Tab. I've got my shell set up so that typing the first bit and pressing Page Up will find the last time I typed that string. I can't remember what the default keybinding for that function is, and the file I need to edit to make it that keybinding only gets changed when I do a full install, so I'd have to look up which one that is to know.

---

### Post by keijo-kukka on 2020-12-21
Thanks for the tips! I assume by scripting you mean bash scripting and making aliases of your fav commands? I gotta to learn that. For some peculiar reason my wakeonlan commands are executed and received fine only when the target is already online (I can verify this in Windows targets with 'WakeonLAN Monitor' app), but they are unable to wake any target when they are offline. Oh well, I guess I just need to keep on using Ampare Wake On Lan which works fine.

---

### Post by SeijiSensei on 2020-12-21
If you right-click the menu item on the left-end of the KDE panel, you can choose Edit Applications. This will bring up the KDE Menu Editor. You can create a New Item and enter the command you want to use in the dialog box. [https://docs.kde.org/trunk5/en/kde-workspace/kmenuedit/quickstart.html](https://docs.kde.org/trunk5/en/kde-workspace/kmenuedit/quickstart.html)

You can create a desktop launcher by right-clicking on the Desktop and choosing Create New > Link to Application.

---

### Post by keijo-kukka on 2020-12-21
Thanks! I'll check that one out too!

---

