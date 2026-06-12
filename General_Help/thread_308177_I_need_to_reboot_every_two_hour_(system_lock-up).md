---
title: "I need to reboot every two hour (system lock-up)"
date: 2006-11-27
forum: General Help
---

### Post by Aleksandersen on 2006-11-27
Hi,

I have had some odd lock-up problems that I have been struggling with the last few days or so.

My systems seems to lock-up every two hour. I can barely move the mouse and the rest of the system is non-responsible. I cannot get anything to work and need to forcefully restart the system to get it up and running aging.

How can I figure out what is causing these periodic lock-ups? ](*,)

---

### Post by wieman01 on 2006-11-27
Anything in "dmesg"? Run this from a terminal & post the results:
> dmseg

---

### Post by Aleksandersen on 2006-11-28
I can't run a terminal or anything. The only thing I can do is move the mouse a couple of inches at a time...

---

### Post by wieman01 on 2006-11-28
Switching to a terminal session (ctrl + alt + F1) is not possible either? If it is, do this:
> dmesg >> my_system_message.txt
Then post the contents once you have rebooted.

---

### Post by Aleksandersen on 2006-11-28
No, I cannot switch to a terminal session. ](*,) It don't work.

---

### Post by jimbob on 2006-11-28
While things are running good, open a terminal window and enter 'top' ( no tics ).

Move it up in the corner somewhere and keep an eye on it.  When your system slows to a crawl see what process is hogging the cpu.

This might give you a clue.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by Aleksandersen on 2006-11-28
CPU and memory usage for Banshee and Evolution (the two applications I use the most other other than Firefox/Opera) spiked up really high at the same time.

Then the terminal and the rest of the system froze and I had to reboot.

:-k Do this mean I can't use those any more?

---

### Post by jimbob on 2006-11-28
Do the same thing as above but try one at a time - process of elimination type thing.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

