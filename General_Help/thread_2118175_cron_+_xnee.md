---
title: "cron + xnee"
date: 2013-02-20
forum: General Help
---

### Post by Leo Matheus on 2013-02-20
i had a little problem with that. i want to use xnee to make some actions, and this action must be make every hour, so i think on use cron for that. the only problem is that cron is not executing the actions, thre is no change or moviment on the scream. So, im doing some think wrong, or cron just will not make that? if not, there is any other software i can use to execute the xnee correct?

---

### Post by thermion on 2013-02-20
Could you please post the line of your crontab regarding *xnee*?
Since I'm not that familiar with xnee, is the entry in your crontab any different to the way you usually run *xnee*?

---

### Post by Leo Matheus on 2013-02-20
sopme think like that


03 *    * * *   root cnee --replay -f /(path)/test.xns -time 5


cnee is command line of xnee

---

### Post by thermion on 2013-02-20
If you want to run this command every hour, the syntax is:

[I]0 */1 * * * [your command here]

[/I]PS: why is there a "root" before cnee?

---

### Post by Leo Matheus on 2013-02-20
the root is the user that execute the command.
but my main problem isnt the time, its more like " the mouse clicks and the letters the i type on the keybord are not beeing retype, and if i run the command manually its works"

---

### Post by thermion on 2013-02-20
Hmm... and this is your crontab, or the crontab of the user root?
If you need to run this command as root, use *sudo crontab -e*, and drop the "root" right before your command.

---

### Post by Leo Matheus on 2013-02-25
i have found what i need, its called gnome-schedule, so i think this thread is solved.

---

