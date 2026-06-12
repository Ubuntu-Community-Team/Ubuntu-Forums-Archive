---
title: "printing to windows server via Samba: need user name, password, AND accounting info"
date: 2013-02-03
forum: General Help
---

### Post by mawxcarroll on 2013-02-03
Hi,
  At my workplace printing is handled through several windows servers.  In the past, I have had no significant problems using Samba to print from Ubuntu.  However we have now moved to a system that requires additional authentication information: when I print from windows, it pops up a window asking for User ID.  This new User ID is just a 4-digit accounting code so that the correct department is charged for the printing.

I have not been able to figure out how to print with Samba under the new configuration.  For example, I currently have a job in the queue that is "Held for authentication."  Previously, I could just enter my domain/username and password and print.  Now when I do that it remains "Held for authentication."  I have tried various combinations of username, accounting code, and password to no avail.

Does anyone have any experience with this kind of situation?  Our tech support is not very Linux-friendly, so it would help if I even knew what to ask them for!

Thanks for any help.

Cheers,
tom

---

### Post by mawxcarroll on 2013-02-03
Seems to be the way this always works...as soon as I post a question, I make some progress.

It looks like I need to modify the ppd file to include the correct accounting information since Ubuntu will not prompt for it. This is according to 

[http://www.office.xerox.com/support/dctips/dc09cc0452.pdf]("http://www.office.xerox.com/support/dctips/dc09cc0452.pdf")

I haven't gotten it to work yet since I know only one piece of information (my accounting code) and it seems like I might also need to know a group number.  But at least I have some questions to ask of my tech support crew.  

I will post back if I solve this...hopefully the above document might be helpful for someone else!

Cheers,
tom

---

