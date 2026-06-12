---
title: "Dual command in launcher"
date: 2008-03-09
forum: General Help
---

### Post by Stargazer989 on 2008-03-09
hey just a quick question;
how can i make a launcher for a bot that i have downloaded, i need the commands to come after one another.
the commands are:
cd /home/stargazer/Pictures/bot.v3.1.2
perl bot.v3.1.2.pl

if instead of answering this question you could give me a link to a guide that has to do with launchers, please do

yes this is the commands for the IdleRPG bot

---

### Post by Rocket2DMn on 2008-03-09
I'm sorry I don't have a link for launchers for you, but all they are is just a place to execute a single line of terminal code.  Don't be fooled however, you can execute multiple commands in one line by using the && symbol
```
cd /home/stargazer/Pictures/bot.v3.1.2 && perl bot.v3.1.2.pl
```
However, that is not even needed, you can just execute using the whole path
```
perl /home/stargazer/Pictures/bot.v3.1.2/bot.v3.1.2.pl
```

Your other option is to write a shell file that you can execute from a launcher, and within that shell file would be the commands that are run.

---

### Post by Stargazer989 on 2008-03-09
oops, [IMG]http://img205.imageshack.us/img205/1123/errorfp2.png[/IMG]

the other command:
```
perl /home/stargazer/Pictures/bot.v3.1.2/bot.v3.1.2.pl
```

doesn't return a error nor does it get the bot to join the wanted network/channel

---

### Post by Rocket2DMn on 2008-03-09
It doesn't return anything because it opens the bot in the background.  You can add these lines to a shell file like so:
```
gedit ~/open_bot.sh
```
Then add
```
#!/bin/bash
cd /home/stargazer/Pictures/bot.v3.1.2
perl bot.v3.1.2.pl
```
Save and close.  Make the script executable
```
chmod +x ~/open_bot.sh
```

Then you can test from a terminal by running
```
source ~/open_bot.sh
```

edit: All this puts the shell script in your home directory.

---

### Post by forrestcupp on 2008-03-09
Like Rocket2DMn suggested, a bash script is the best way to go.  With a bash script, you can have as many commands as you want.  Then you just make a launcher to that script.  You don't have to be afraid of all of that advanced scripting language.  Any terminal command will work in a script.

---

