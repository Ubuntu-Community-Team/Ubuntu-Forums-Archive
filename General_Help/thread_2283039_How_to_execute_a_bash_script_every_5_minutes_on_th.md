---
title: "How to execute a bash script every 5 minutes on the hour"
date: 2015-06-18
forum: General Help
---

### Post by greavette on 2015-06-18
Hello,

I understand how to use crontab -e to schedule jobs by the minute but in my case I want my bash script to execute every 5 minutes on the hour.  So at noon I want it to execute at 12:05 and 12:10 and 12:15...etc.

Can cron do this or do I need to do something in my bash script to check the time?

Thank you.

---

### Post by papibe on 2015-06-18
Hi greavette

Something like this should work:
```
*/5 * * * * /path/to/your/script.sh 
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by greavette on 2015-06-18
Thank you papibe for the reply.

Wouldn't this mean if I add the cron task at 12:03..the next time it will run is at 12:08?

Thank you.

---

### Post by papibe on 2015-06-18
It shouldn't.

I believe '*/5' is just an abbreviation for '0,5,10,15,20,25,30,35,40,45,50,55'.

Regards.

---

### Post by greavette on 2015-06-18
Awesome!  Thanks.

---

