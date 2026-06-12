---
title: "Cron tab to run a java file - pls help!"
date: 2017-02-08
forum: General Help
---

### Post by hannah.smith on 2017-02-08
I'm having issues getting a cron tab to run a java file every 5 minutes and have searched tirelessly and tried many things to get it to work!


I have tried to create an executable script to see if that is what's needed:


My script and java file are both stored in [B]/usr/local/bin

[/B]My crontab:


[B]*/5 * * * * /usr/local/bin/java-crontab.sh

[/B]My script:[B]#!/bin/bash
export PATH=/usr/share/doc/openjdk-6-jre-headless:$PATH
java -jar /usr/local/bin/javatest.jar
[/B]
My sys log says I don't have MTA installed - installed postfix that didn't solve
anything so I removed that. Any help would be so much appreciated!! :D

---

### Post by efflandt on 2017-02-09
cron is run with minimal env (assume that nothing is defined), and initial $PATH is undefined. Use full paths for everything run by cron. For example your $PATH does not include **/usr/bin**, so cron would not even know where to find **java**.

---

