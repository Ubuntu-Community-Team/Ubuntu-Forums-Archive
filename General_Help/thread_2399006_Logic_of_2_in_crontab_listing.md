---
title: "Logic of */2 in crontab listing"
date: 2018-08-20
forum: General Help
---

### Post by raleigh3 on 2018-08-20
Can someone help me figure out the logic of */2 in this cron listing?

It looks like day of month divided by 2 to me?

```
You can use the following cron arrangement. The fields denote (from left-to-right): 
Minute, Hour, Day of Month, Month, Day of Week. The "*/2" in the Day of Month field means "every two days".

  0      23     */2       *       * insert_your_script_here.sh
     

```

---

### Post by deadflowr on 2018-08-20
Step values: [https://stackoverflow.com/questions/27412483/how-do-cron-steps-work]("https://stackoverflow.com/questions/27412483/how-do-cron-steps-work")

---

### Post by SeijiSensei on 2018-08-21
*/2 means run the command when the time code in question is divisible by two.  So the command runs on the 2nd, 4th, 6th, etc. day of the month.

---

