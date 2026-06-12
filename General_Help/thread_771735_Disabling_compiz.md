---
title: "Disabling compiz"
date: 2008-04-27
forum: General Help
---

### Post by bongtothesoo on 2008-04-27
Hello, I'm trying to make my laptop switch to tablet/laptop mode and disable compiz at the same time.
I know that I can disable compiz with "metacity --replace" and enable it by "compiz --replace".
I have a Fujitsu T4210 and following this [howto]("https://help.ubuntu.com/community/T4220") I can go into tablet mode with "rotate tablet" and back to laptop with "rotate laptop".
all I want to do is write a single script that launches "metacity --replace" and "rotate tablet" (in that order) and write a script that launches "rotate laptop" and "compiz --replace" (in that order)
I tried already by creating a Tablet.sh and a Laptop.sh with the two commands in two separate lines but it doesn't seem to work.

For the Tablet.sh I did> metacity --replace
rotate tablet

and for the Laptop.sh> rotate laptop
compiz --replace

What am I doing wrong?[PHP][/PHP]

---

### Post by FuturePilot on 2008-04-27
Maybe a dumb question but did you start the scripts off with this at the very top?
```
#!/bin/bash
```
Also make sure they are executable. 
```
chmod +x Tablet.sh
chmod +x Laptop.sh
```

---

### Post by bongtothesoo on 2008-04-27
I actually hadn't so I went back and added them there. And yes they are executable. But it still doesn't fix the problem.
Running Tablet.sh disables compiz but nothing else. Running Laptop.sh will enable compiz but will go into tablet mode at which point I have to ctrl+alt+backspace...:confused:

---

### Post by FuturePilot on 2008-04-27
Hmmm. Lets try this. Add a semicolon 
```
;
```
to the end of the first command of each script.
So Tablet.sh will look like
```
#!/bin/bash
metacity --replace;
rotate tablet
```
And Laptop.sh will look like
```
#!/bin/bash
rotate laptop;
compiz --replace
```

---

### Post by Rocket2DMn on 2008-04-27
Try
```
#!/bin/bash
metacity --replace &
rotate tablet &
exit 0
```
Then run it with
```
source Tablet.sh
```
instead of
```
./Tablet.sh
```

---

### Post by bongtothesoo on 2008-04-27
Thanks guys
Pilot, unfortunately the ; did not work... but thank you so much for trying to help.
Rocket, your method works like a charm. One thing though... How would I make a launcher out of the way you wrote the scripts, having to run with "source" and all...?

---

### Post by Rocket2DMn on 2008-04-27
The command that the launcher runs is just source Tablet.sh command.  You will probably need to specify the entire path to the shell script though, so like
```
source /path/to/script/Tablet.sh
```
You can try running it with just
```
./Tablet.sh
``` it may actually work, you'll just have to try.

It's the same stuff for your Laptop.sh file, too, of course.

---

### Post by FuturePilot on 2008-04-27
Woops, it was & :oops:

You can actually put a launcher right on the panel if you want. Right click on the panel and select Add to Panel...
Select Custom Application Launcher and for the Type select Application in Terminal. For the command just put in the path to the script.

---

### Post by bongtothesoo on 2008-04-27
yup just the path without the source works
thank you so much

---

