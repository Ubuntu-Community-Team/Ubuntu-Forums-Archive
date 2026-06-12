---
title: "evolution caledar &quot;read only&quot; problem"
date: 2007-10-16
forum: General Help
---

### Post by Denny Johnson on 2007-10-16
I've just got evolution running, when I try to enter events in the calendar, I get the following:
[B]Cannot create a new event
You have a read-only calendar source selected. Change to Calendar View and highlight a calendar that can accept appointments.[/B]
I've tried, but no joy.
Can anyone tell me how to get out of this READ ONLY mode.
Thanks

---

### Post by Cannaregio on 2008-04-03
Better late than never :-)

This is an obvious kind of bug. In fact evolution works ok for some months, and then suddendly you get this obnoxious message:
```
You have a read-only calendar source selected. Change to Calendar View and highlight a calendar that can accept appointments.
```
Bug has been filed and put to sleep on
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg542643.html]("http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg542643.html").

-----------------------------------------------
What you have to do to correct this problem:

1) Open evolution
2) Click the "calender" tag
3) Click "on this computer" top left
4) If "personal" is checked, uncheck it
    If  "personal" is unchecked, check it
This should theoretically already work, however in my case it did not, so I added the following:
5) ==> edit ==> preferences ==> Calendar publishing
6) Add ==> Publishing location
7) click on SSH and substitute with "custom location"
8 ) reclick on custom location and substitute back to SSH
9) exit calendar preferences, if necessary "force quit" the whole calendar application
10) if necessary restart, anyway recheck "personal" on the top left "on this computer" frame.

That's it. Now you'll be able to fix your appointments and the buggy application will accept them. Enjoy.

---

### Post by Denny Johnson on 2008-04-03
Thanks Can......I'd got it working, but I'm sure your post will also be appreciated by others in the future.

---

