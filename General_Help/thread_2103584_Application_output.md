---
title: "Application output"
date: 2013-01-10
forum: General Help
---

### Post by JoccE on 2013-01-10
Hello.

I got an application that i start via a web panel with the php command:
shell_exec('cd /home/server/ && ./appname;');

Works great. 

but i want to log the output in the application (there is running text at upstart and then everytime someone logs in agians the server it appears and so on.
So i need to log in realtime.

i have tried:
shell_exec('cd /home/server/ && ./theforgottenserver > output.log 2>&1;');

That logs some of it but stops in the middle of the startup.

Any suggestion to what i could do?

Eather a php script that shows the output
or some way to log it so i then can load it.


Sorry for the bad english, hope you understand what i ment :/

Yours 
JoccE

---

### Post by JoccE on 2013-01-11
Bumps

---

