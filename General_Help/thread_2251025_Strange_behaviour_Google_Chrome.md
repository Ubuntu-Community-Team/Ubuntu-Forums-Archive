---
title: "Strange behaviour Google Chrome"
date: 2014-11-01
forum: General Help
---

### Post by john_burns2 on 2014-11-01
I've just installed Ubuntu12.04.5 on an older computer and downloaded the .deb file for Google Chrome (latest version) Installed it via Ubuntu Software centre. It warns me this program starts via terminal. So opened a terminal up and typed "google-chrome"  Chrome starts but I've tried locking the icon to the launcher then re-starting from there. Just doesn't start from the launcher at all. I get this message in terminal when starting Chrome.... >   ATTENTION: default value of option force_s3tc_enable overridden by environment.
[2545:2545:1101/183021:ERROR:desktop_window_tree_host_x11.cc(1547)] Not implemented reached in void views::DesktopWindowTreeHostX11::MapWindow(ui::WindowShowState) [2545:2580:1101/183140:ERROR:channel.cc(316)] RawChannel read error (connection broken)

Anyone know what this means and more importantly, how to make Chrome start from the launcher? (PS, I have made Google Chrome the default browser)

Thanks in advance

---

### Post by Frogs Hair on 2014-11-01
I've not seen a prompt to start Chrome from the terminal and this could suggest a compatibility problem with 12.04. I last used Chrome with 13.04. Make sure all updates are installed and wait for a 12.04/Chrome user to weigh in.

---

### Post by yancek on 2014-11-01
On Ubuntu 12.04, I don't have any problem starting google-chrome from a terminal with either:

google-chrome or /usr/bin/google-chrome

Most any application will start from a terminal with a full path so I don't see how that could be a problem.  I don't recall seeing the message you report about it starting from a terminal when I installed it.  Which deb file of google-chrome did you download and which version is it?  How did you put the google-chrome icon in the Unity Launcher?  I have it there and it starts without problems.  I don't have any idea what the errors you listed at the end of your post mean.  You might try googling each and see what you get.

---

### Post by vasa1 on 2014-11-01
Somewhat related: [http://ubuntuforums.org/showthread.php?t=2251068](http://ubuntuforums.org/showthread.php?t=2251068)

---

### Post by mc4man on 2014-11-01
Well both seem similar to here - 
[http://ubuntuforums.org/showthread.php?t=2248972](http://ubuntuforums.org/showthread.php?t=2248972)
Seems to be a possible issue with gpu decoding, video drivers,  ect.

---

### Post by john_burns2 on 2014-11-03
Solved it... Apparently when I selected the "make Google Chrome my default browser" option, it creates three files. These are located in /local/share/applications. Selecting "show hidden files" reveals all the files in this location. Deleting every file that has the name Chrome in it and deleting these (and emptying the rubbish bin afterwards) makes Google Chrome start from the launcher correctly.

---

