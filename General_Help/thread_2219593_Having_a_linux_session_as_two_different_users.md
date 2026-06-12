---
title: "Having a linux session as two different users"
date: 2014-04-24
forum: General Help
---

### Post by lunix2 on 2014-04-24
**In response to popular request** I will explain *what I am trying to accomplish*.

I  am working with configuring (and re-configuring) several Linux boxes,  most of which are to run headless. So I have setup a Linux box where I  can plug/unplug HDDs, copy partitions, edit configs, etc. all as root.  I  can search for a file, then right-click and do something with it (like  edit it, for instance) as root.

My XP box is where I have done  embedded systems design and development, and was also my personal  computer for Email, Web browsing, watching video, doing  teleconferencing, etc.  I want to virtually eliminate XP (and all of  Windows), and do everything on a single box without having to log in/out  or switch users all the time.  Many of my tools, as well as my schematic  capture, and PCB layout run only under Windows, so I will dedicate a  box just to that.

We're taliking here about my main, everyday  computer.  When an Email arrives for user "bill", I want root to hear  the notification, while the Emailer and browser run as user bill.  So I  want to start my PC, and have it run a login script for user "bill"  which will, as root, switch to desktop 4, and start a terminal with four  tabs, one of which will be a local session, the other three will have  ssh sessions to headless boxes.  In that local tab, I want to spawn a  file manager, and one or two additional GUI programs, running with root  priviledges. And I want that tab to return immediately to a root bash  prompt, without waiting for the spawned programs to close.

Thanks for reading this wordy post.  And thanks for trying to help me.

Bill

---

### Post by bapoumba on 2014-04-24
In Ubuntu, a regular user in the sudo group can be granted root permissions to run admin tasks that require elevated privileges. There is not need to open root sessions as you describe, because if Bill is in the sudo group, you can run your own tasks as user Bill and gain root permissions with sudo whenever needed.
Please read at [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
Please also understand that when threads are closed by Staff, if you want to contest the closing or discuss it, you are expected to start a thread in the Resolution Center : [http://ubuntuforums.org/forumdisplay.php?f=123](http://ubuntuforums.org/forumdisplay.php?f=123). Not open new threads on the same subject.
So while you have a read (and one additional may be at the forums policy Elfy pointed you at), I'm closing yet again this one.

---

