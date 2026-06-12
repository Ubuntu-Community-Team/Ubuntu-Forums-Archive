---
title: "crontab/current directory error"
date: 2016-03-28
forum: General Help
---

### Post by YaPaY on 2016-03-28
Dear all,

I have a command, it works if I in same directory

for example

mono /home/yapay/WebGrab/WebGrab+Plus.exe "$(pwd)"

works only if current directory /home/yapay/Webgrab is. If not I get this error:

config file /home/WebGrab++.config.xml doesn't exist
execution stopped

I would lik to execute this command with crontab but I am getting error because of this reason. How I can solve this

---

### Post by SeijiSensei on 2016-03-28
it's looking for the config file in /home, not in /home/yapay or directories below it.  You'll need to look into how mono is configured to know why.

---

