---
title: "Respawn an application unless another is running"
date: 2015-10-28
forum: General Help
---

### Post by JayRott on 2015-10-28
I have a really specific thing I am trying to accomplish with a script, but despite my research I can't figure out how to make it happen. What I need is a script that will check in a specific interval like 30 seconds to see if Kodi is running, and if not relaunch it, but only if another application called "emulationstation" is not running. The script to respawn seems pretty common, but I can't seem to figure out how to make it look for "emulationstation" and not respawn.

I hope someone who knows how to code far better than I do can help. Thank you.

---

### Post by jim_deadlock on 2015-10-28
What language are you using? You can check the processes like this:

```
ps -ef | grep -i kodi
ps -ef | grep emulationstation
```

---

### Post by JayRott on 2015-10-28
I was hoping to just use a simple bash script but honestly I couldn't code myself out of a paper bag. I am more of a copy and paste, then modify to fit my needs kind of user unfortunately.

---

### Post by The Cog on 2015-10-28
something like this perhaps? This is a  bit of a guess:
```
pgrep Kodi || pgrep emulationstation || nohup Kodi
```

I would probably add the above command to /etc/crontab to run every minute. But check it works first.
This would be the crontab line:
```
* * * * * root /usr/bin/pgrep Kodi || /usr/bin/pgrep emulationstation || /usr/bin/nohup Kodi
```
You will probably need to give the full path to Kodi executable too, 
and you probably don't actually want to run it as root either.

---

### Post by JayRott on 2015-10-28
No good. it respawns kodi fine but it will respawn even when emulationstation is running. The idea here is to use a shell script that will relaunch kodi if it crashes, but when I want to play games I have a script that killall -9's kodi and launches emulationstation. When I exit emulationstation it relaunches kodi.

---

### Post by SeijiSensei on 2015-10-28
```

#!/bin/bash

if [ "$(ps ax | grep kodi | grep -v grep)" = "" -a "$(ps ax | grep emulationstation | grep -v grep)" = "" ]
then
     code to relaunch kodi goes here
fi

```
The if statement will be true only if both programs are not running.

---

### Post by JayRott on 2015-10-28
Running the script didn't relaunch kodi so I edited it to post to a file with the code below:
```
#!/bin/bash

if [ "$(ps ax | grep kodi)" = "" -a "$(ps ax | grep emulationstation)" = "" ]
then 
 echo "Test" >> myfile.txt 
fi

```

and it didn't do that either. Am I doing something wrong? The code to relaunch kodi should simply be /usr/bin/kodi

---

### Post by SeijiSensei on 2015-10-28
You need to use the revised version I posted.  I forgot to include the "grep -v grep" commands during my first stab at it.  Without them you'll always get non-empty strings.

---

### Post by JayRott on 2015-10-29
> **SeijiSensei said:**
> You need to use the revised version I posted.  I forgot to include the "grep -v grep" commands during my first stab at it.  Without them you'll always get non-empty strings.

Thank you, this works perfectly!  Now I can kill Kodi to save resources for the games, but still have it respawn if it crashes.

---

