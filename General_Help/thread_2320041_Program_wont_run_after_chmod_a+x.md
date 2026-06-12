---
title: "Program wont run after chmod a+x"
date: 2016-04-09
forum: General Help
---

### Post by eder.pereira on 2016-04-09
Hi, there.


Ive been a regular linux user since Red Hat 3 around 1998.

Regular, but not geeky. I practically dabble at Terminal.

Thing is, to be honest, since Ubuntu and its tutorials came into the scene, I've found it much easier to simple copy and past stuff in the Terminal. I miss my days with the bible and Red Hat and -after - Slackware for-dummies. This is so, that I believe this is my first post in ten years!


This happened twice this week:

I've been working on getting some emulator front-ends up and running in my home entertainment ubuntu laptop.

After all is set and done and i am ready to run the program for the first time, i double-click it and nada.

I tried the chmod a+x command and apparently it worked fine.

Nonetheless, when i key in the command, Terminal says "Command not found"

[FONT=arial]Check it out:

[/FONT]eder@LinuxLaptop:~/fusion/Fusion$ ls
Fusion  History.txt  Readme.txt
eder@LinuxLaptop:~/fusion/Fusion$ chmod a+x Fusion
eder@LinuxLaptop:~/fusion/Fusion$ Fusion
Fusion: command not found






I'd greatly appreciate any heads-up.
[FONT=arial]
PS: for the developers out there, I believe I speak for a lot of folks when I say "bring Hardy Heron back!"

=)[/FONT]

---

### Post by steeldriver on 2016-04-09
Since ~/fusion/Fusion is probably not on your executable search path ($PATH), you need to give an absolute or relative path to the program

```

~/fusion/Fusion/Fusion

```
or
```

./Fusion

```

Hope this helps

---

