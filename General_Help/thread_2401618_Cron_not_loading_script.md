---
title: "Cron not loading script"
date: 2018-09-20
forum: General Help
---

### Post by webmiester on 2018-09-20
When I put this line in Cron, it should load my script every 1 minute.  But it doesn't:

1 * * * * /home/user/Desktop/script.sh

Now I read that it didn't work perhaps because script.sh isn't executable as per Cron's shell so I made it:

1 * * * * chmod +x /home/user/Desktop/script.sh
1 * * * * /home/user/Desktop/script.sh

Now it still doesn't work :(
Script.sh works when loaded from the command line.  Does anyone have any ideas what is wrong?

---

### Post by ajgreeny on 2018-09-20
It may help if you show us the full text of that **script.sh** otherwise we are working in the dark.

---

### Post by webmiester on 2018-09-20
The script is actually 

#!/bin/bash/
xmodmap -e "clear Control" &
xset s 0 0 &
xset s off &
Exit 0

You see what I'm trying to do is prevent people from.opening a new window (cntr-n) in a station then changing some of my browser's settings.

I've placed the xmodmap command on a startup script but for some terminal, the script doesn't work (but it works on others), I've also tried having a script that reloads it a few times after x amount of seconds after the browser launches, but it still sometimes doesn't work.  So now I want to try launching it repeatedly so that it will work, but Cron doesn't launch the script right.

The script works when I launch it from the command line.

---

### Post by Impavidus on 2018-09-20
Don't put chmod in your crontab. If the script isn't executable, you have to use chmod, but you only have to use it once. If you can execute the script in the terminal, it's executable, so you don't need chmod.

The line```
1 * * * * /path/to/script
```will execute the script every hour, at one minute past the hour. That's not what you intend. To make the script run every minute, use```
* * * * * /path/to/script
```But I doubt that's the best way to solve your problem.

---

### Post by webmiester on 2018-09-20
> **Impavidus said:**
> Don't put chmod in your crontab. If the script isn't executable, you have to use chmod, but you only have to use it once. If you can execute the script in the terminal, it's executable, so you don't need chmod.

The line```
1 * * * * /path/to/script
```will execute the script every hour, at one minute past the hour. That's not what you intend. To make the script run every minute, use```
* * * * * /path/to/script
```But I doubt that's the best way to solve your problem.

Oh wow thanks.  This explains it very well.  How about if I want it to load every 15 minutes, what should I do?

If I put

15 * * * * command, then it will load 15 minutes after every hour.

Will this line work:

15 0 * * * command

Well actually I'll also be putting up a script that will backup my files, so I will really need to understand this thing.  So far I've learned that how I initially understood the first column is wrong.  Thank you so much

---

### Post by Impavidus on 2018-09-21
See [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

To run something every 15 minutes, you can use```
*/15 * * * * command
```
If you use```
15 0 * * * command
```it will run at fifteen minutes past midnight.

---

