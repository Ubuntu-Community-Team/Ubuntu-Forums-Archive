---
title: "Simple script with 3 commands (wine, xte)"
date: 2018-06-17
forum: General Help
---

### Post by klopp91 on 2018-06-17
I am very new to Ubuntu and I basically use it to run an .exe in a Virtual Desktop. For automation purposes I created 3 commands that will make an .exe run, fill-in password, and hit Enter, so the program launches.

```
DISPLAY=:1 wine /path_to_exe/program.exe
DISPLAY=:1 xte 'str mypassword'
DISPLAY=:1 xte 'key Return'
```

With these 3 simple commands from an external SSH Terminal session, the program is executed in the Virtual Desktop, password is filled-in and then launches normally. Issue is I cannot combine these 3 commands into a crontab nor a script to work toghether.


I tried different scenarios in Terminal which don't work.
```

command1;sleep 5;command2;sleep 2;command3
command1 && sleep 5 && command2 && sleep 2 && command3
command1; command2; command3
```

I also created a script.sh with following code, which would also not work.
```
#!/bin/bash
DISPLAY=:1 wine /path_to_exe/program.exe
sleep 5
DISPLAY=:1 xte 'str mypassword'
sleep 2
DISPLAY=:1 xte 'key Return'
```

---

### Post by again? on 2018-06-17
Your script won't continue until your first command exits or you append with "**[COLOR="#FF0000"]&[/COLOR]**"
eg
```
#!/bin/bash

export DISPLAY=:1

wine /path_to_exe/program.exe **[COLOR="#FF0000"]&[/COLOR]**
sleep 3  #give time to open
xte 'str mypassword'
xte 'key Return'
```

---

### Post by klopp91 on 2018-06-18
Thank you. I can't wait to test it. I finally managed to work around the issue with a complete amateur solution: I created a script for each of the 3 commands (script1.sh, script2.sh, script3.sh), and then joined the 3 toghether within another script123.sh which combines the three like script1.sh & script2.sh & script3.sh. However, as you mention, script2.sh was not loading properly untill I stopped somehow script1.sh by placing "echo $?" at the end I remember. So indeed has to do with stoping the first command. I'll try to keep them in one script though as you indicate.

---

### Post by klopp91 on 2018-06-18
Ok, so the script now works perfectly with the above correction, within a single .sh file with all commands toghether and a crontab to execute the script. Thank you very much.

---

