---
title: "freezing"
date: 2018-07-06
forum: General Help
---

### Post by jgw on 2018-07-06
I am running with ubuntu 18.04  

system description/info: [https://pastebin.com/vE8KA0YJ](https://pastebin.com/vE8KA0YJ)

My machine has been freezing with some regularity.  Sometimes I can wait it out and sometimes I am forced to reboot.  I am also running an addon called "system monitor" and I am assuming that it is the gnome version of the program (there are two "system monitor" addons.  Anyway, one of the things it displays is cpu status (and also memory and net).  I have been noticing that things get a little hinky when the iowait goes over 100% to over 350%  (if you put the mouse over the cpu graph it displays the iowait (along with user, system nice and other) I have no idea what the percentages are of)  I have researched the iowait thing and the fixes seem to be multiple and a little hinky.  One other thing is the memory which is always mentioned although no suggestions that I should increase it.  

I have included a hardinfo report in pastebin.   If you need any logs just ask.  This one drives me nuts.  Thank you..............

---

### Post by mdurham on 2018-07-06
You have to find the process that is taking up the cpu time. Run the Administration system monitor and select
"show all processes" from it's menu. Then select the processes tab. You should see the offender at the top of the list.
Good luck

---

### Post by jgw on 2018-07-07
Thank you for the response.

I only have one system monitor and do not know what the Administration system monitor is.  I searched and also googled for it and nothing. 

Anyway, I can run it, minimize it, etc. but, when the system freezes I can't get to it as my mouse no longer works.  If I have to re-boot then the info is lost.  Is there some way to have the system record the top .   I also searched the gnome extension site for "system monitor".  I got back 6 pages but only about 4 with "system monitor" as the title of the extension.  I wonder if there is a logfile someplace with the information I need.

Thoughts?

Incidentally, when I tried to post this reply I was told I didn't have authorization.  I then refreshed and found that I had to re-login.  Just thought I would mention that as it was odd and may be a symptom of something.

---

