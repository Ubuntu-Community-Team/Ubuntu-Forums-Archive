---
title: "Application timed shutdown"
date: 2007-02-15
forum: General Help
---

### Post by AmazingRando on 2007-02-15
I've recently fully moved over from Windows to Ubuntu (horray!) and it's been great so far.  If there's one thing that I'm missing however, it's an easy to use tool for shutting down apps, launching apps, or suspending the machine.  In Windows I used an app called [RS Somnifero]("http://www.ricosoftware.net") .  It was great because I could use it to shutdown an app after a certain amount of time (e.g. a video before I went to sleep), or suspend the computer when I was done encoding and CPU utilization had fallen below a certain amount for a certain number of minutes.  I know I can run cron jobs and the like, but is there anything easier and more comprehensive?

Thanks

AR

---

### Post by Artemis3 on 2007-02-15
Most unix like systems have always included the command "at"

It cannot be more simple:

```
echo "killall mplayer" | at 4am
```

---

### Post by AmazingRando on 2007-02-16
> **Artemis3 said:**
> Most unix like systems have always included the command "at"


You're right, that's pretty darn easy.  :D Any ideas on how to do something similar when CPU or network utilization drops below a certain level for X minutes?

Thanks!

AR

---

### Post by sorin.stirbu on 2007-07-09
> **Artemis3 said:**
> Most unix like systems have always included the command "at"

It cannot be more simple:

```
echo "killall mplayer" | at 4am
```

that cmd is just for mplayer ? 

if i would like to shut down my PC at a certain hour in the night (when i am sleeping) would it be like this ?!?!? :
> echo "killall" | at 3:30am

---

### Post by bazmati on 2008-03-04
> **sorin.stirbu said:**
> that cmd is just for mplayer ? 

if i would like to shut down my PC at a certain hour in the night (when i am sleeping)


I had same desire as you and wanted to share the 'easy method' 
I did a search on the 'man' page for the shutdown command found a few interesting flags

the -P flag will power off your system either Now  or at a given HH:MM (24h format) time 
the -c flag will cancel the shutdown 

you need to be root so:
```
sudo shutdown -P 2:45
``` 
oh darn i can't sleep so i don,t want my system to shutdown a 2:45 am anymore
so open another terminal window and in it type 
```
sudo shutdown -c
```

Sweet dream :)

---

