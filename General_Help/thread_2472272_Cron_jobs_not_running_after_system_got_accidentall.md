---
title: "Cron jobs not running after system got accidentally rebooted"
date: 2022-02-22
forum: General Help
---

### Post by cocox on 2022-02-22
Hello,

Is there anything i can do to have my cron jobs run regardless whether my Ubuntu server crashed and i didn't notice?

I was expecting to get some emails from my cron jobs and i didn't get anything. When i turned my monitor on i noticed my Ubuntu server had restarted for some reason.

After i logged in, the cron jobs run and sent the emails.

I wouldn't like this to happen again. I would like for the cron jobs to execute whether i logged in or not after an unexpected reboot.

Thanks!

Running Ubuntu server 20

---

### Post by TheFu on 2022-02-22
Cron should run regardless of users being logged in.  The only way that wouldn't happen is if the script requires a user-session to work.  If it runs a program that links to X/Windows, then almost always, those programs will fail, since X/Windows requires an X/Session which requires a user login to work.

Remove all the dependencies and assumed environment variables if you want something to run. Heck, don't even trust the PATH.  This is part of scripting best practices. Most people ignore it or never learned it until something like you are seeing has happened.

Of course, if a program that is part of the cron task is what crashed the system, it will already be passed the "start time" that cron uses to decide if something show be run or not.  You can figure that out by using logging and 'echo' statements in the script that are written to files as part of the process.

No Linux system should have any unexpected reboots.  They should remain booted until we reboot them - 1, 5, 10 months. I don't strive to have very long uptimes, but 2 weeks between new kernels is common.
```
$ uptime
 19:28:03 up 10 days,  8:08,  5 users,
```
is on a random system here.

---

### Post by cocox on 2022-02-22
hey thank you for the reply! my Ubuntu server rebooted because i accidentally unplug the power stripe the other day. Is on a Raspberry Pi, so it's nothing like a serious in production system...

this my cron job line:
1 16 * * 1-5 /usr/bin/python3 /home/cocox/Python/OEGD/xyz.py >/dev/null 2>&1

From what you said, i don't see anything that might depend on the users being logged in. Maybe i am missing something. Do you see something wrong with it? Thanks

---

### Post by TheFu on 2022-02-23
Stop redirecting output to null so you can see what is happening. Send it to a file.

If the computer isn't on at 16:01 weekdays, then that script won't run. Perhaps running it through anacron "daily" would be a better fit? You won't control when it runs, but it will run once per day, if the computer is powered on during that day.  

BTW, why not just put the python3 inside the script on the #! line?

I've never put Ubuntu on r-pi hardware. I thought it was odd on that hardware. Doesn't Canonical mandate using Ubuntu Core?  If true, eeeeew.

---

### Post by ActionParsnip on 2022-02-23
or add lines in the script to show the lines of code are being ran. You could even add lines to populate dmesg :)

---

