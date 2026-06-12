---
title: "Can't Log In?"
date: 2007-08-08
forum: General Help
---

### Post by 417xray on 2007-08-08
Hello,

I am running Ubuntu 6.10 and have been for about 6 months.  Just last night i tried to log in and the log in screen accepts my user name and password, the screen goes black for a few seconds, and then returns me back to the log in screen.  I just can't get past the log in screen no matter which user name I type in.  It seems as if i am in a loop.  No matter which session type I choose I can not log into the system be it KDE, GNOME, or the fail-safe terminal option.

I was trying to run MONDO prior to this problem and sending the backup to a DVD.  Mondo failed and I had to end the program.  I rebooted and that's when I got locked out.  The archves were never sent to the DVD recorder.  Could the backup file image be taking up all my disk space so that i can't log in?

Any ideas?

Thanks in advance,
john

---

### Post by dougfractal on 2007-08-08
boot into rescue mode or liveCD

> df -h   # disk info
du -sh ~/    # disk usage of home
du -h --max-depth=1 ~/    # disk usage of homefolder one level


---

### Post by 417xray on 2007-08-08
Thanks dougfractal for the reply!  I'll give it a go and let you know.

Thanks.

---

### Post by 417xray on 2007-08-26
Hello,

Back again and I got hold of a Knoppix CD and after I booted it shows that my hda1 is completely full, 100%.  I guess that's why I can't log in.

Next, I tried to delete some files but as a Knoppix user booted off the CD I do not have permission to change attributes or delete anythiing on the hard disk.

I can see all the files on the disk but can take no action upon them.

Ideas?

Thanks.

---

### Post by dougfractal on 2007-08-27
from knoppix  login as root
> sudo -s
konqueror

[www.knoppix.net/wiki/](www.knoppix.net/wiki/)
> Q: What is the root password?
A:

From the Using FAQ : there is none; in Knoppix LiveCD all passwords are locked by default.

You can set root password by going Knoppix Menu->Root Shell and typing "passwd", then enterting a root password, also there are several sections you can read dealing with this subject in KNOPPIX/README_Security.txt. You can also type "sudo su" or "sudo -s" in any console window, or use <ctr>-<alt>-F2 to get at the text console with already opened root shell.

Apparently, however, in some versions of Knoppix, if you type 'sudo -s', it will ask for a password. If you simply press return without entering anything, it will tell you 'Authentication Failed."


---

### Post by 417xray on 2007-08-27
Hello dougfractal,

Thanks for your response.  I actually tried something else last night.  When the GRUB starts to load it prompts you to hit the ESC key and then gives you a menu of kernal boot options.  The normal kernal, rescue, and memtest.  I think that's all.

Anyway I highlighted the rescue kernal and then hit 'e' for edit.  That brings you to another screen and gives you some more boot options.  Then I hit 'b' for boot and the kernal starts to load, no graphics, and finally prompts me for the root password.  I entered it and went right to the command prompt.   You just have to remember the root password.

I was golden then!  I had all the rights to the files and directories.  I got rid of all the MONDO files and can now log back in.

Again, thanks so much for your help and that's good to know about the Knoppix root log in.  I will have to try it.

---

