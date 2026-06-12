---
title: "Bash Script Doesn't Show Commands Running in Terminal Window"
date: 2017-07-12
forum: General Help
---

### Post by qschris on 2017-07-12
I really hate posting this question, but I must be using the wrong search terms on the forum and Google.


I want to use a bash script to launch one terminal window, run several commands, and see the progress as each command runs.


I can launch a terminal window, but the commands run in the background instead of showing in the terminal window.


I'm using a persistent version of Xubuntu 16.04 running from a thumb drive made by Yumi from an ISO.




My test script looks like this:
```
#!/bin/bash
xterm -hold -e mousepad
xterm -hold -e thunar
...etc

```





I would expect to see something like this in the terminal window
```
ubuntu@ubuntu:~$ mousepad
ubuntu@ubuntu:~$ thunar
ubuntu@ubuntu:~$ 

```



Instead, I'm seeing a terminal window open, no prompt, but a blinking cursor, and mousepad opens. I then close mousepad and the command window. After that, another similar command window opens, followed by thunar. -- I expect to have to close mousepad to get the next command to run, but there is no prompt, multiple terminal windows, and the terminal does not show the commands being run.


Thanks in advance for your ideas!

---

### Post by TheFu on 2017-07-12
You need an '&' to detach the program from the current terminal.

```
xterm -sb &
```

I would run each program and have the stdout and stderr sent to a log file for each cmd, then **tail -f** each log file in a different window, if that is really what you want.  That way, you have the logs even if you don't catch everything scrolling by.

For example, I have a little script that patched all my systems. I run it weekly, usually on Saturday mornings.

```
$ sudo weeklyupdates.sh | tee -a log.weekly
```

Then I have the log to review if anything didn't work or I notice issues in the next few hours.

---

### Post by qschris on 2017-07-14
Thanks, that gets me part of the way there. Outputting to a log will give me the same results. Is there a way to make the output verbose? I tried testing with this command:
```
sudo apt-get install blah | tee -a ~/Desktop/installation_log
```

And only received this output in the log:
```
Reading package lists...
Building dependency tree...
Reading state information...
```

But if I ran that in terminal, I would see an error:
```
Reading package lists...
Building dependency tree...
Reading state information...
**E: Unable to locate package blah**
```

If something fails, I want to catch it all. Thanks!

---

### Post by TheFu on 2017-07-14
You need to **redirect** stderr too. Learning about redirection is a core skill to have. I would redirect all stderr into stdout, then send that into the 'tee' program.  Any basic Unix/Linux intro book/class would cover it.

---

### Post by qschris on 2017-07-24
That appears to have worked, thank you for you assistance!

---

