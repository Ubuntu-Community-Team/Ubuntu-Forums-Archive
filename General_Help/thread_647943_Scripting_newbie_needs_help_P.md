---
title: "Scripting newbie needs help :P"
date: 2007-12-22
forum: General Help
---

### Post by Anduu on 2007-12-22
Hopefully I can explain this so it makes some kind of sense.

I am really good at basic scripts but have no clue how to do anything fancy.

I have set myself up a cronjob to run Azureus sans the gui every night for a few hours.It works just fine.At present the only way I know of to shut it down (...because I am a newbie hehe...) is to add a 'killall java" cron job at the appropriate time.

Here is the script:
```
#!/bin/bash
cd /opt/azureus/
java -jar Azureus2.jar --ui=console

```

When this command is given in terminal it gives its rolling output showing what is going on and you simply type "quit" to shut it down.

What I would like to know is how to go about passing the quit command on to the process via the cronjob at the appropriate time.

Any help would be much appreciated :)

---

### Post by andrewcmcardle on 2007-12-23
I'm not to sure, you could set up a separate cron job which sends a pkill signal to the other process, using the killall command.

---

