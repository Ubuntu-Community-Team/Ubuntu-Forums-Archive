---
title: "GDM Won't Let me In"
date: 2007-07-21
forum: General Help
---

### Post by Aifel on 2007-07-21
So, when I try to login, gdm gives me an error.

"GDM could not write to your authorization file. This could mean you're out of disk space or that your home directory could not be opened for writing. In any case, it's not possible to login."

I've tried reinstalling gdm, which didn't do anything. I've reconfigured x11, which also did nothing. Can anyone offer assistance?
And no, the computer is not out of disk space.

---

### Post by sonny on 2007-07-21
Try changing permissions on your ./home/user directory. Login at a terminal (by pressing Ctrl+Alt+F1) with your user or with root and type: "sudo chmod -R 755 /home/your-user" then type "sudo /etc/init.d/gdm restart" and try to login once more.

If you can't loging in comandline mode, then use a livecd to change the permission of you home directory.

---

### Post by Aifel on 2007-07-21
OK, solved it.

---

### Post by compsariomike on 2007-07-25
I had the same problem and this solution worked...once.  The next time i turned the computer on I got the same thing.  I'm new...extreeeeeeeeeemly new to ubuntu mainly because ii'm completely sick and tired of Winblows.  I really would like to get back into Ubuntu so if anyone could help i would much appreciate it.

---

### Post by Wim Sturkenboom on 2007-07-25
Your disk might be full. Check which partition is full and cleanup. To check, log in in a console (<ctrl><alt><Fx> (where x is 1..6)) and run the command *df -h*,

---

### Post by compsariomike on 2007-07-25
I'm very thankful to the speedy reply, but i don't think it's possible for me to have filled the 250GB hardrive in the past few hours since installing Ubuntu.  

And as for the putting stuff into the terminal...can i do that by going to recovery mode?  Because if not itt does me no good.

---

### Post by Wim Sturkenboom on 2007-07-25
You can but I don't think you have to. Just press the above given key combination. It shopuld take you to a console.

And you can easily have done an incorrect partitioning where your home partition is only 1MB instead of 10GB or 100GB.

---

### Post by ghonz on 2007-07-25
I have a smiliar issue, I was downloading a dr who torrent which was larger than i expected and it filled up my computer.

When I try to log in I get the same message that these guys get.

I'm guessing once I free some space I can log in again, so my question is how do I go about deleting a file without being logged into GDM.

> **Wim Sturkenboom said:**
> Your disk might be full. Check which partition is full and cleanup. To check, log in in a console (<ctrl><alt><Fx> (where x is 1..6)) and run the command *df -h*,

---

### Post by compsariomike on 2007-07-25
Well, I again thank you for your help but i solved the problem.  A cursed at it for many minutes and then decided to reboot and re-install again.  I suggest that if anyone is doing the same as I did, imidiately update or the system will  start to freeze and you'll get the GDM error.

---

### Post by Wim Sturkenboom on 2007-07-26
> **ghonz said:**
> ... so my question is how do I go about deleting a file without being logged into GDM.I tried to explain that, but obviously not clear enough.
When you press the key combination <ctrl><alt><Fx> (where x is 1..6), you should be taken to a console where you can login with your normal username and password.
The following are some commands to use while in the console:
*ls -l* displays content of directory
*cd* allows you to go to another directory (_cd abc_ takes you to directory abc, _cd .._ takes you a directory up (parent))
*rm* removes a file (e.g. _rm verybigfile_ to remove the file called verybigfile)
*exit* to logout

<ctrl><alt><F7> will take you back to the GUI


> **compsariomike said:**
> ...  I suggest that if anyone is doing the same as I did, ... Can't remember to have seen what you did.
I run Dapper and never had the issue.

---

### Post by compsariomike on 2007-07-26
I was running Feisty at the time and i'm still not too sure why GDM was messing up, but i found that I solved the problem by installing the easy way (the alternate CD).

---

