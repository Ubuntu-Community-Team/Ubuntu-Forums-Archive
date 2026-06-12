---
title: "After Ubuntu installations"
date: 2008-01-28
forum: General Help
---

### Post by joemarshal on 2008-01-28
Hi 
 I am new to Linux.I had a windows xp media center version on my system. I installed ubuntu on a seprate partition as ext3 with a memory of 10GB and a swa[ space of 1GB . After successfully installation the system boots up and showing the OS selection menu which has Four options 
1.Ubuntu Generic
2.Ubuntu Generic (Recocvery Mode )
3.Ubuntu memtest
4.Windows Media center

When i select the first option The system shows me a messgae 
"Starting up..........."
It is showing a blank screen for some five minutes or more and get restarted ,this continues for 2 3 times and i tried the second option which after loading the drivers it give me a command prompt like boot@joe# there i typed "exit"  then it loads the Os and asking for username and password
then i can work on it thats fine and gr8
Then i restart my system and tried the first  option then condition was same.
But there is no problem with the windows it works fine

My sys Config is 
P4 1.5Ghz 
with 640MB ram 
60 GB hard disk space 
can any one suggest me  a solution i had installed ubuntu 7.04
is it due to wrong installation if so can anyone guide me the installation 

Thanks on advance
Joe:popcorn:

---

### Post by cdenley on 2008-01-28
You can try this
```

sudo update-grub

```

This will reconfigure the boot options. Recovery mode should give you a root terminal without you logging in as you described. The first option shouldn't. This should fix it.

---

