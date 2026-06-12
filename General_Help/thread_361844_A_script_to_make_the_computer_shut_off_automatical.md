---
title: "A script to make the computer shut off automatically?"
date: 2007-02-14
forum: General Help
---

### Post by Athanasius on 2007-02-14
Is there a way to make the computer shut off at a designated time?  I am not talking about a server or anything, just a desktop.

---

### Post by thelocust on 2007-02-14
There is a program called Cron that will run what ever program you want at a designated time. Tie that with a script and you should be good to go.

---

### Post by thelocust on 2007-02-14
You can use "sudo shutdown" I don't know much about writing script so I don't know how to make accept the root password with out you entering it.

---

### Post by Athanasius on 2007-02-14
chron?  how does that work?

---

### Post by highneko on 2007-02-14
Edit: Nvm, this is a bad way of doing it probably. llamakc posted a good example below.

---

### Post by llamakc on 2007-02-14
You would edit the crontab as root or by using sudo.



```


 # sudo crontab -e OR
 # sudo crontab -e -u root (2) Append following entry to it (shutdown at 20:00 hrs [24 hrs format]):
 0 20 * * * /sbin/shutdown -h now (3) Save the changes and exit to shell prompt. 


```


Or, by using the "at" command:




```


**# sudo at 8pm**
*at> **halt***
(Press CTRL+D)


```

---

### Post by mannheim on 2007-02-14
Edit: I missed llamack's post above. What I wrote below is incorrect as far as the usage of "shutdown" goes. The command needs an argument (e.g. "now") as llamack showed.

If you want the machine to shut down at 21:17 every evening, then I think you can do it using cron and shutdown, as thelocust says. Create a text file called "my_shutdown" or whatever using Text Editor, containing the single line:
```
17   20  *   *   *  root shutdown
```
Put a copy of this file in the directory "/etc/cron.d". You will need to use sudo:

```
sudo cp my_shutdown /etc/cron.d/
```

That should be all, I think. (Of course, I haven't tested this.) The format for the line in the text file is that the first two entries specify the minute and hours; the next three entries specify the day-of-the-month, the month, and the week-day. The entry "*" means "any". So if you did instead
```
17   20  *   Sep   Thu  root shutdown
```
then the machine will shutdown at 20:17 every Thursday in September.

---

### Post by SeanTater on 2007-02-14
Isn't it rather redundant to use "at" or "cron" If you have to tell shutdown "now" ?

Wouldn' t this work?```
shutdown 16:42
```

---

### Post by chalex on 2007-02-14
> **SeanTater said:**
> Isn't it rather redundant to use "at" or "cron" If you have to tell shutdown "now" ?


Yes, unless he wants to schedule it to shut down at the same time each day.

---

### Post by dcstar on 2007-02-14
> **SeanTater said:**
> Isn't it rather redundant to use "at" or "cron" If you have to tell shutdown "now" ?

Wouldn' t this work?```
shutdown 16:42
```

All cron commands must have the full path to whatever binary/script you are running, if you want to find out where a particular command is, then:
```
whereis **shutdown**
```
will show you where the **shutdown** command resides in the filesystem.

Cron does not run in a shell environment where paths are set.

For the particular requirement of this thread, I would use the command "**init 0**" in any cron/at setup (with the full path to the init command, of course).

---

### Post by Athanasius on 2007-02-15
I do want it to shut down at the same time every day

---

### Post by Athanasius on 2007-02-15
In Edgy, I see the file chrontab (in /etc/) and there are other commands in it.  I will try to put the command in there and see what goes on.

---

### Post by Athanasius on 2007-02-15
I added 
```
12 22   * * *   root	/sbin/shutdown -h now
```
to chrontab and it works (I tested it with another time).  

Now, if I want it to shutdown at 10:22pm every night except for Saturdays, on which I would want it to shutdown at 11:00pm, how would the entry be made?

---

### Post by hannaman on 2007-02-15
That would require two lines in the crontab.  Something like:

22 22 * * 0,1,2,3,4,5 root /sbin/shutdown -h now
0 23 * * 6 root /sbin/shutdown -h now

If I remeber correctly, the fifth field is the day of the week with Sunday being 0, Monday 1, etc.

---

### Post by ferretti75 on 2007-06-28
Ok,

what about if I have to turn off the pc from time1 to time2 and be sure that it stays turned off (i don't mind to turn it on again, i just want that if someone turns it on again, it checks and shuts down again) ?  

I thought of a root shell script run by a cron job every 5 minutes. If it is running between time1 and time2 then perform a shutdown ( init 0 ) .... but, during the tests, the script launched from a cronjob does not shutdown the pc ( i know it runs because I am logging ... ) & returns no error !!


Any work-around/debugging hint would be appreciated


cheers

Marco

---

