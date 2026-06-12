---
title: "cron or sleep"
date: 2007-10-14
forum: General Help
---

### Post by jmvidalvia on 2007-10-14
Hello!
I am checking every 5 minutes a folder, and then move files, etc.
I made a cron that works every 5 minutes but wonder whether it wouldn't be better to just add a sleep 300 line in my script.
What I don't like about cron is that I have a new login every 5 minutes, and my auth.log is becoming bigger and bigger.
But...if I have some sleep scripts, how will I now which is the right one if I nedd to stop it?
Thanks a lot!

---

### Post by thirddeep on 2007-10-14
If you use sleep in a script, you will only have 1 PID.

I would still recommend cron, that way you do not have to worry about the process dying.

Thd.

---

