---
title: "notify-send and calendar events"
date: 2008-06-12
forum: General Help
---

### Post by meg23 on 2008-06-12
I am trying to set up notify-send to inform me of the date and 

calendar holidays. However, I have not been able to get the 

variable to be filled in with the actual date. In this command, 

jdate represents the calendar date. If there isn't a simpler way 

of doing this, how can I get the value of "d" to be printed in 

the notify-send notification box?

#! /bin/sh
d=$(jdate)
notify-send -u critical -t 30000 -i mail-notification "Today is the " echo $d

---

