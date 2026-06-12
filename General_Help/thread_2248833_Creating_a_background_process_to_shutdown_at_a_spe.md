---
title: "Creating a background process to shutdown at a specified time with warning message"
date: 2014-10-17
forum: General Help
---

### Post by nickjanoyan on 2014-10-17
I'm using the LXDE desktop and I'm trying to create a background process that will automatically shutdown my computer at a specified time. I know how to do that part, but I'm not able to get it to stay in the background after I close the terminal. Here's what I type in the terminal.

```
sudo shutdown 15:00
```

When I do that it works and tells me my computer will be shutdown at that time, but after I close the terminal and look at my task manager, I don't see it running. I tried this which has helped me in the past to launch programs like Chromium from the terminal without it closing the program when I close the terminal. This is what I typed.

```
sudo shutdown 15:00 &
```

and this was what it showed after. 

```
[1] 4056
```

In the past when I've used "&"it's launched the program, but this is just giving me what I'm guessing is the number ID for the process. However when I look at the task manager that ID is not listed anywhere. Does "&" only work for GUI programs? Maybe that's why it's not working. I don't know what else to do, so I'm hoping you guys could help me. All I want to do is have my computer shutdown at a specified time automatically without requiring the terminal window to be open. Also if there's anyway to have a warning message pop up like 5 minutes before the shutdown to let me know my computer is about to shutdown, that would really help. Thank you.

---

### Post by nerdtron on 2014-10-17
I can talk about scripting or even scheduling on crontab but if you just want a timer for shutdown, I have a two link for you:
Program called Easy shutdown: [http://itsfoss.com/schedule-shutdown-ubuntu/](http://itsfoss.com/schedule-shutdown-ubuntu/)
There's also Complex shutdown (more options): [http://www.maketecheasier.com/schedule-ubuntu-shutdown/](http://www.maketecheasier.com/schedule-ubuntu-shutdown/)

---

### Post by nickjanoyan on 2014-10-17
> **nerdtron said:**
> I can talk about scripting or even scheduling on crontab but if you just want a timer for shutdown, I have a two link for you:
Program called Easy shutdown: [http://itsfoss.com/schedule-shutdown-ubuntu/](http://itsfoss.com/schedule-shutdown-ubuntu/)
There's also Complex shutdown (more options): [http://www.maketecheasier.com/schedule-ubuntu-shutdown/](http://www.maketecheasier.com/schedule-ubuntu-shutdown/)
Thank you. I downloaded both programs, but EasyShutdown is the only one that appears to be working. I know nothing about crontabs, but I have created a few basic scripts before. If you could help me with that I would really appreciate it. Even though I haven't used crontabs before, I'm willing to learn if it's more effective than scripts.

---

### Post by tgalati4 on 2014-10-17
You can install the *at* command.  Use it interactively or with a one-liner:

```
echo "sudo shutdown -h now" | at 1500 17 OCT
```

To see the jobs:

```
atq
```

---

### Post by nickjanoyan on 2014-10-17
> **tgalati4 said:**
> You can install the *at* command.  Use it interactively or with a one-liner:

```
echo "sudo shutdown -h now" | at 1500 17 OCT
```

To see the jobs:

```
atq
```
Thank you. I tried what you suggested, but I got this error message.

```
warning: commands will be executed using /bin/sh
Cannot open lockfile /var/spool/cron/atjobs/.SEQ: No such file or directory
```

---

### Post by nerdtron on 2014-10-17
Can you try this on the command line:

```
/usr/bin/notify-send "Opening gedit in 5 seconds" && sleep 5s && gedit
```

It give a notification for opening gedit, after 5 seconds gedit should open.
If this is successful, we can revise this script to make it shutdown.

---

### Post by nickjanoyan on 2014-10-17
> **nerdtron said:**
> Can you try this on the command line:

```
/usr/bin/notify-send "Opening gedit in 5 seconds" && sleep 5s && gedit
```

It give a notification for opening gedit, after 5 seconds gedit should open.
If this is successful, we can revise this script to make it shutdown.
That worked. After 5 seconds gedit opened like you said it would.

---

### Post by nerdtron on 2014-10-17
Good then. Do you know how to edit a file on the command line? Because we can add this line on the crontab to schedule the shutdown.

```
 0 15 * * * /usr/bin/notify-send 'Shutdown in 5 minutes' && sleep 5m && poweroff 
```

---

### Post by nickjanoyan on 2014-10-17
Yes I do. Which file am I supposed to edit though? I've been using Linux for a few months now, but I'm still not that great at it, so I apologize for not knowing this kind of thing.

---

### Post by nerdtron on 2014-10-17
It's ok. I think I have found a 1 liner command for you. Not crontab, just run on the command line.

```
 echo  "/usr/bin/notify-send 'Shutdown in 5 minutes' && sleep 5m && poweroff" | at 15:00 
```

This will send the command poweroff at 15:00 today. I just confirmed this works on my end. (though I'm using centos VM right now)


Edit: Just corrected the single quote and double quotes

---

### Post by nickjanoyan on 2014-10-17
I typed that command, but unfortunately I got the same error I did last time.

```
warning: commands will be executed using /bin/sh
Cannot open lockfile /var/spool/cron/atjobs/.SEQ: No such file or directory
```

I did however figure out how to edit the crontab file and I added that line to the file like you suggested, so maybe we could try that other method you had in mind.

---

### Post by nickjanoyan on 2014-10-17
I typed that command, but unfortunately it gave me the same error it did last time.

```
warning: commands will be executed using /bin/sh
Cannot open lockfile /var/spool/cron/atjobs/.SEQ: No such file or directory
```

I was able to edit the crontab file though and I added that line like you suggested to the file. If you had another method in mind we can try that.

---

### Post by nerdtron on 2014-10-17
> I did however figure out how to edit the crontab file and I added that  line to the file like you suggested, so maybe we could try that other  method you had in mind. 

That's it.
BTW: I have an error on the crontab entry i provided earlier so you may to edit it back.
Just save the crontab and it will be activated.
Post the output of "crontab -l" (lower case L)here so that we can see if the line is added.

---

### Post by tgalati4 on 2014-10-17
Did you install *at*?

```
apt-cache policy at
```

The one-liner would need to be run in a root terminal:

```
sudo su
echo "poweroff" | at 1500 17 OCT
atq

```

---

### Post by nickjanoyan on 2014-10-17
Here's the output.

```
# Edit this file to introduce tasks to be run by cron.# 
# Each task to run has to be defined through a single line
# indicating with different fields when the task will be run
# and what command to run for the task
# 
# To define the time you can provide concrete values for
# minute (m), hour (h), day of month (dom), month (mon),
# and day of week (dow) or use '*' in these fields (for 'any').# 
# Notice that tasks will be started based on the cron's system
# daemon's notion of time and timezones.
# 
# Output of the crontab jobs (including errors) is sent through
# email to the user the crontab file belongs to (unless redirected).
# 
# For example, you can run a backup of all your user accounts
# at 5 a.m every week with:
# 0 5 * * 1 tar -zcf /var/backups/home.tgz /home/
# 
# For more information see the manual pages of crontab(5) and cron(8)
# 
# m h  dom mon dow   command
0 15 * * * /usr/bin/notify-send 'Shutdown in 5 minutes' && sleep 5m && poweroff
```

Does that crontab only work for 15:00? Lets say I want to change the time to something else. Like 18:00. How would I do that?

---

### Post by nickjanoyan on 2014-10-17
> **tgalati4 said:**
> Did you install *at*?

```
apt-cache policy at
```

The one-liner would need to be run in a root terminal:

```
sudo su
echo "poweroff" | at 1500 17 OCT
atq

```
Yes it's installed. I ran that command, but I got the same error again.

---

### Post by nerdtron on 2014-10-17
Looks good.
Change 15 to 18. Basically the first 5 entries are time stamps. If you see the line above from the line you added it says:
**m h dom mon dow command**

m - minute
h - hour
dom - day of month
mon - month
dow - day of week
command - the command you want to run

So basically 0 15 * * * "command here" will execute the "command here" on 0 minute of the 15th hour, every day, every month, every day of the week.

If you want to disable the crontab entry, you can erase it or put the character #  in the beginning of the line.
The output of crontab -l says it all.

---

### Post by matt_symes on 2014-10-17
Hi

> **nickjanoyan said:**
> I typed that command, but unfortunately it gave me the same error it did last time.

```
warning: commands will be executed using /bin/sh
Cannot open lockfile /var/spool/cron/atjobs/.SEQ: No such file or directory
```

I was able to edit the crontab file though and I added that line like you suggested to the file. If you had another method in mind we can try that.

As .SEQ is just a lock file, the commands to create it and change ownership to daemon may just fix the problem.

```

sudo touch /var/spool/cron/atjobs/.SEQ
sudo chown daemon:daemon /var/spool/cron/atjobs/.SEQ
```

at is a useful Linux command. You may have to set a display variable when using any GUI command with at though.

Assuming display 0 => echo "DISPLAY=:0 /usr/bin/notify-send ......

If you want the converse of shutdown and your BIOS supports it, look at ```
rtcwake
```. It's great for an alarm clock.

Kind regards

---

### Post by nickjanoyan on 2014-10-17
I did what matt suggested and then typed in ```
echo "/usr/bin/notify-send 'Shutdown in 5 minutes' && sleep 5m && poweroff" | at 16:59
``` (I changed the time to a few minutes from my current time to see if it would work).

I no longer saw that error message pop up and to confirm that the job was added, I typed in atq and it listed it. I waited until the 16:59 and even 10 minutes after that, but nothing happened. I wonder why I can't get this to work. I appreciate you guys helping me. I know this must be getting annoying.

---

### Post by matt_symes on 2014-10-17
Hi

> **nickjanoyan said:**
> I did what matt suggested and then typed in ```
echo "/usr/bin/notify-send 'Shutdown in 5 minutes' && sleep 5m && poweroff" | at 16:59
``` (I changed the time to a few minutes from my current time to see if it would work).

I no longer saw that error message pop up and to confirm that the job was added, I typed in atq and it listed it. I waited until the 16:59 and even 10 minutes after that, but nothing happened. I wonder why I can't get this to work. I appreciate you guys helping me. I know this must be getting annoying.

Use this command instead. Notice the display variable that i mentioned in my last post. This will get a notification displayed for you. I have not check the rest of the commands as i don't want to  shutdown yet :)

```
echo "DISPLAY=:0 /usr/bin/notify-send 'Shutdown in 5 minutes' && sleep 5m && poweroff" | at 16:59
```

For testing run this as it will schedule the command to run one minute after you type the comand and hit the <enter> key.

```
echo "DISPLAY=:0 /usr/bin/notify-send 'Shutdown in 5 minutes' && sleep 5m && poweroff" | at now + 1 minute
```

Kind regards

---

### Post by nickjanoyan on 2014-10-17
Okay I'm finally getting somewhere. I thought that maybe the reason why it wasn't working was because I was closing the terminal after I entered these commands, so I added "&" at the end. Here's what I typed.

```
sudo su 
echo "poweroff" | at 1724 17 OCT &
```

After that, it confirmed that the job was added and I typed in exit and then typed in atq. It didn't display anything after typing atq, so I exited the terminal and once it was 17:24 my computer shutdown instantly. 

@matt_symes I'm going to test your method too and see if it works. 

The command shutdown my computer which was great, but a warning message would really help, so I have time to close any programs that I'm using before it shuts down. Is there anyway to edit that poweroff command so it will display a warning message a few minutes before my computer shuts down?

---

### Post by matt_symes on 2014-10-17
Hi

If you want a notification when using at run the echo command with a display variable as i have mentioned three times now ;)

See my previous post. It should work for you.

Kind regards

---

### Post by nickjanoyan on 2014-10-17
I apologize. At first your command didn't work, but then I did what a previous user mentioned and typed sudo su and then I typed in your command. It worked perfectly. It showed a notification window letting me know my computer would shutdown in 5 minutes and after 5 minutes it instantly shutdown. Thank you so much everyone for helping me. It was driving me nuts trying to figure out how to do this myself. You guys were great help.

---

### Post by matt_symes on 2014-10-17
Hi

> **nickjanoyan said:**
> I apologize. At first your command didn't work, but then I did what a previous user mentioned and typed sudo su and then I typed in your command. It worked perfectly..

The poweroff and shutdown commands require elevated privileges (sudo su is one way of getting them).

You'll also need the display variable if you go down the cron route instead of using at.

I'm glad it's working for you.

Kind regards

---

