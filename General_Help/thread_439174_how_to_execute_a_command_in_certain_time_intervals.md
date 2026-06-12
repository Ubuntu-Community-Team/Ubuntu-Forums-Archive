---
title: "how to execute a command in certain time intervals ?"
date: 2007-05-10
forum: General Help
---

### Post by manjula.mh on 2007-05-10
well guys is there a way to give instruction to ubuntu to execute a certain command in a given time intervals ?

e.g. say i want to execute command ./dial every 30 mins... is there a way to accomplish this ?

my real problem is my Internet connection get D/C due to crappy ISP and ubuntu doesn't reconnect automatically. so when i leave torrents to download over night usually it stucks because internet get DC. i posted a diffrent thread asking for a soloution and nothing much came up. 

But i got this idea if i can execute the this command ./dial in command prompt regardless of internet conectivitly i will be able to maintain a good connection so please help me

---

### Post by moterpent on 2007-05-10
Hi manjula.mh,

To answer the first part of your question, you may want to look at cron (man cron, man crontab, man 5 crontab).  It allows you to schedule events, at the command line, up to as frequently as once every minute.  

As far as the second part of your question is concerned...  It's been a while since I've fought with dial-up but I've got to believe that there is some sort of ability for the system to automatically reconnect on a disconnect.  Maybe someone who actively uses dial-up will know better.  If I get some time I'll do some further digging.  I can't imagine it will be too hard to fix.

--- Edit ---

Have you tried the "Retry if connection breaks or fails to start" option under -- Administration -> Network (see attached screenshot)?

---

### Post by kragen on 2007-05-10
There may be a better solution, but the one that pops to mind is cron - the scheduling daemon. [http://www.linuxhelp.net/guides/cron/](http://www.linuxhelp.net/guides/cron/) is a fairly good starter guide, but very basically if you run

```
crontab -e
```

You will be presented with a file , each line corresponding to a scheduled event - the link I gave explains it in more detail, but an example line:

```
01,31 * * * * command_to_execute
```

will run "command_to_execute" at 01 and 31 minutes past the hour, every hour, every month, every day of the week etc... (that's what the *'s in the hour and month columns are for).

I'm not sure what the "User that the command will run as" column is about in the linked article - perhaps the article is outdated or something, but my crontab doesn't seem to need it.

It's worth noting that you can have problems with certain commands - if for example you need to run a graphical command, you may need to specify "export DISPLAY=:0" as part of your command for it to work properly.

I suppose an alternative to this would be to knock up a quick script or something - it depends on how good you are with programming, myself I know very little about scripting :)

---

### Post by manjula.mh on 2007-05-10
Thanks for the help i think for now i stick with crontab .. don't know much about scripts...
Thanks for the help..

---

