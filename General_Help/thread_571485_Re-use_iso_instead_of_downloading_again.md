---
title: "Re-use iso instead of downloading again"
date: 2007-10-09
forum: General Help
---

### Post by Gordonbp531 on 2007-10-09
I installed Wubi, it downloaded the iso file and all was OK. I then got a hang at 79% of the install. I re-booted to Windows, uninstalled Wubi (but made a backup of the iso file) and restarted the installer. it now wants to re download the iso. how can i make it use the one that's already downloaded?

---

### Post by ago on 2007-10-09
Did you select the same distro as last time?

---

### Post by Gordonbp531 on 2007-10-09
I don't think I did - because I re-did it and it worked. 
However, it's hung again (for over 20 minutes now) on configuring wvdial, at 79% of "Select and install software".
is there any way around this?

---

### Post by ago on 2007-10-09
> **gendibal said:**
> I don't think I did - because I re-did it and it worked. 
However, it's hung again (for over 20 minutes now) on configuring wvdial, at 79% of "Select and install software".
is there any way around this?

That's usually when you have <= 256MB of memory

---

### Post by Gordonbp531 on 2007-10-09
> **ago said:**
> That's usually when you have <= 256MB of memory

the machine has 1GB RAM - are you saying that the install won't recognise that?

---

### Post by ago on 2007-10-09
No that's fine, I am only saying that people run into this issue because of low memory, which is not your case. How long did you wait at 79%? Give it 5-10 minutes.

---

### Post by Gordonbp531 on 2007-10-09
> **ago said:**
> No that's fine, I am only saying that people run into this issue because of low memory, which is not your case. How long did you wait at 79%? Give it 5-10 minutes.

It's been 30 minutes or more.
I found this thread about hanging on wvdial with the solution of going into a console and killing the wvdial process
[http://ubuntuforums.org/showthread.php?t=172686](http://ubuntuforums.org/showthread.php?t=172686)

I've killed the process, but when I type "exit" to leave the ASH shell all it does is take me back to the shell again, is there some other command or key combination i need to use?

---

### Post by Gordonbp531 on 2007-10-09
well I'm buggered!
While I was away typing the previous response, it somehow slipped out of the console and reverted to the Windows XP Ctl-Alt-Del screen. I rebooted, chose Ubuntu, got lots of red FAIL and then a restart.
Chose Ubuntu again, and Bingo! All seems to be OK!

Very odd.....

---

