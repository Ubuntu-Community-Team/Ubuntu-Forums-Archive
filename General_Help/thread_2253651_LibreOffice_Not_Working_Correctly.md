---
title: "LibreOffice Not Working Correctly"
date: 2014-11-21
forum: General Help
---

### Post by Bill_McConnell on 2014-11-21
I bought a System 76linux laptop this fall.  In the last couple of days, I have been unable to open and save some types of LibreOffice files, especially spreadsheets in Excel format and Word documents.  This is a new problem; for several weeks I have successfully opened, created, and saved files in all formats under LibreOffice.  I would welcome suggestions on how to attack this issue.

---

### Post by dragonfly41 on 2014-11-21
Can you open LibreOffice via command line

sudo libreoffice

and try Writer with sudo permissions?

---

### Post by amanchesterman on 2014-11-21
Also it would help to know if your version of LibreOffice is up-to-date. With a document open on the screen, click on Help > About LibreOffice and let us know what it says.

---

### Post by Mark Phelps on 2014-11-21
>  I have been unable to open and save some types of LibreOffice files, especially spreadsheets in Excel format and Word documents. 

These files you're trying to open -- are these files you have created in LO, or are these files other people created in MS Office and have sent to you?

---

### Post by Bill_McConnell on 2014-11-21
Thank you both for the quick response.  My version is 4.2.7.2 Build ID 42m0(Build:2), whichI think is up to date (the software installer ran a day or so ago).

At first, I could no start LibreOffice with sudo because it recgnizedthat I had a version running.  I closed all open files, but got the same complaint, so I rebooted.  After the reboot, I was able to open LibreOffice with a sudo command, and open and close both excel and word file types.  I shutdown and rebooted again, and am able to access and save all file types even without sudo.

So, I will mark this thread as solved, but I wish that I had rebooted before I posted, because maybe that would have been enough.  On the positive side, I have a new arrow in my quiver in trying sudo for application issues.

Thanks again for the help.

Bill

---

### Post by ajgreeny on 2014-11-21
Actually, you should not use **sudo** for root permissions for a GUI application.  It is possible, though not likely, that it could lock you out and stop you from logging in to your user account.  See Root-Sudo in my signature for details.

If you must run the app with root permissions you should use gksu/gksudo at the moment, even though it is being deprecated in favour of pkexec at some point in the future.

---

### Post by Impavidus on 2014-11-21
Just use sudo as a way to work around all kind of problems doesn't sound very wise. You only need sudo/root permissions for changing your system configuration or some low level hardware access. If it works agains a problem with a user program editing a user file, something else must be wrong already. Which is good to know, but just using sudo for the application is not going to solve the root cause of your problem and is quite likely to cause even more problems. I wouldn't run LibreOffice with root permissions at all. One should never need it.

---

### Post by vasa1 on 2014-11-21
I too was wondering about the wisdom of using sudo in OP's context but didn't say anything because "it worked".

---

### Post by dragonfly41 on 2014-11-22
My suggestion to use sudo opened up a Pandora's box.
I accept that gksudo would be a better idea.

> 
If you must run the app with root permissions you should use gksu/gksudo at the moment, even though it is being deprecated in favour of pkexec at some point in the future.


...

Putting my suggestion into context the idea was to unlock any temporary hang up in LibreOffice (which is not exactly a high risk application holding lurking viruses)  and then resume normal (non sudo) user permissions after unlocking.

Sometimes it is necessary to take a calculated risk. 
e.g. OP has a locked spreadsheet which is urgently needed to hit some deadline.

That argument apart, my guess from the OP's account is that it was the reboot which probably fixed any lock and not the use of sudo.

---

### Post by Impavidus on 2014-11-22
Sometimes sudo works, for example to remove a lock that shouldn't be owned by root in the first place. But sometimes I see newbies advising other newbies that they should try sudo as a magical way to tackle all problems. I know you're not a newbie, which is why I didn't bluntly say not to use sudo here.

If a problem (or only it's symptoms) is removed by using sudo, it was probably caused by incorrect usage of sudo.

---

