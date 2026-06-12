---
title: "Packages Install But Don't Display"
date: 2012-12-02
forum: General Help
---

### Post by LinuRob on 2012-12-02
[FONT=Tahoma]**[SOLVED**] [/FONT]**Packages Install But Don't Display**.
[FONT=Tahoma]
Hello,

Ever since i upgraded to 12.10 and then downgraded back to 12.04 i have had a major issue regarding Ubuntu Software Center which has become very frustrating.

Whenever i install a package via Ubuntu Software Center (or Terminal) the package does not display anywhere on my system once the installation has completed. 

Let's say i have just downloaded and installed Chromium. The process goes fine as it should and so i exit to launch my newly added program. Chromium is not displayed in the program launcher so i decide to do a whole computer search. This reveals absolutely nothing and i cannot find the program at all.

Before i updated it was absolutely fine and worked perfectly so this really confuses me. 

My computer has no hard drive and is running Ubuntu 12.04 through a USB drive with 2GB of Persistence enabled.

Please.... someone help me. I've almost given up on this now and i desperately need some help.

Thanks everyone.
[/FONT]

---

### Post by ibjsb4 on 2012-12-03
If you have searched your entire file system and did not find [FONT=Tahoma]Chromium, then its not installed.  So just to be sure, try this in terminal.

[/FONT]```
sudo apt-get install chromium-browser
```[FONT=Tahoma][FONT=Tahoma]

If it shows up installed and you still cannot find it then one more time in terminal enter:

[/FONT][/FONT]```
chromium-browser
```[FONT=Tahoma] 

[/FONT]

---

### Post by LinuRob on 2012-12-03
> **ibjsb4 said:**
> If you have searched your entire file system and did not find [FONT=Tahoma]Chromium, then its not installed.  So just to be sure, try this in terminal.

[/FONT]```
sudo apt-get install chromium-browser
```[FONT=Tahoma][FONT=Tahoma]

If it shows up installed and you still cannot find it then one more time in terminal enter:

[/FONT][/FONT]```
chromium-browser
```[FONT=Tahoma] 

[/FONT]

Hi,

I've used the advice you gave me on UFRaw which is another program i have been struggling with. The response to 'sudo apt-get install ufraw' in the terminal was this.

"ubuntu@ubuntu:~$ sudo apt-get install ufraw
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ufraw is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 248 not upgraded."

Then i used the simple 'ufraw' command to lauch the program and.... It worked! 

Seems a bit odd how it won't appear in any search or on the program bar, yet when you type it into the terminal it works perfectly. Strange.

Thanks very much for your help, looks like we've solved the issue then.

---

### Post by ibjsb4 on 2012-12-03
ufraw is CLI, another words a terminal program.  So that one would not have a start icon, but I don't know why you couldn't just make one.

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

