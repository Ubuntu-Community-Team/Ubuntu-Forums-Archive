---
title: "How to start/resume a cron job by system load average?"
date: 2013-04-30
forum: General Help
---

### Post by nodnolse1 on 2013-04-30
Hi, I'd like to 'cron' 'recollindex'** or others commands or scripts wile the system load is less than 0,5 and terminte/kill/pause them when the system load is over 0,9 for instance, and resume/restart the job when the system load is become less then 0,5 for 15 minutes always for instance. Thanks




** [http://manpages.ubuntu.com/manpages/precise/man1/recollindex.1.html](http://manpages.ubuntu.com/manpages/precise/man1/recollindex.1.html)

---

### Post by prodigy_ on 2013-04-30
If you simply want to ensure that scripts don't impact the responsiveness of your system, see **man nice**.

---

### Post by manishiitg on 2013-04-30
i dont think this is possible. cron is simply managed from crontab

the script inside your cron job should check the system resource and then execute itself

---

### Post by matt_symes on 2013-04-30
Hi

I don't think there's any built in way to do this. I have never come across it. There may be something you can install that would do that for you though, but once again, i have not come across it.

Alternatively, you could create a script that checks the system load and pauses and unpauses recoilindex depending in system load. 

That may work but it's something i have never tried. Here's some pointers..

For system load

```
cat /proc/loadavg
```

To pause...

```
kill -STOP <pid_of_recoll>
```

To continue...

```
kill -CONT <pid_of_recoll>
```

Kind regards

---

### Post by nodnolse1 on 2013-04-30
Thanks for the idea, it is what i'll do. A more question if you can, does exist a way to start a job when input devices are unused since xx mins? Thanks

---

### Post by matt_symes on 2013-04-30
Hi

> **nodnolse1 said:**
> Thanks for the idea, it is what i'll do. A more question if you can, does exist a way to start a job when input devices are unused since xx mins? Thanks

What input devices ?

Kind regards

---

### Post by nodnolse1 on 2013-05-02
> **matt_symes said:**
> Hi



What input devices ?

Kind regards

I mean Keyboard or Mouse. Kind regards, Paolo

---

### Post by matt_symes on 2013-05-02
Hi

Maybe ```
xprintidle
``` would help here.

```
sudo apt-get install xprintidle
```

It will print how long the x session has been idle in milliseconds.

You may have to specify the DISPLAY variable and run the command as a user.

```
export DISPLAY=:0;
idle_time=$(sudo -u <user_name> xprintidle);
echo $idle_time > /tmp/idle_time.txt
```

Experiment a bit and see what you can come up with.

You can also play with ...

```
su -c <user_name> .....
```

...instead of sudo.

Kind regards

---

