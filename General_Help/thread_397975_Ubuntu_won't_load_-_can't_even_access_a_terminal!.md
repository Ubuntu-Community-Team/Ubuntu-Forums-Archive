---
title: "Ubuntu won't load - can't even access a terminal!"
date: 2007-03-31
forum: General Help
---

### Post by Chicken_Man on 2007-03-31
I'm in a mode of complete desperation.
Came home last night to wake my edgy up from a 5 hour sleep. Once it's back, everything starts loading VERY slowly, like one button every 5 seconds.
After a while everything freezes and I'm forced to reset.
It starts loading as usual, then switches to verbose mode, goes past:
checking file system
fsck 1.39 [ok]
then freezes for 3 minutes and next thing I know, every single process starting from date is OUT OF MEMORY!
[xxxxxxx.xxxx] out of memory: kill process xxxx (xxxx) score xxxxx and children

NOTHING works anymore - I can't get root access from the terminal as for some reason it thinks the password is wrong. I can't access the previous kernel version either - same problem.
Basically I have no control whatsoever!

Please help!

---

### Post by r4ik on 2007-03-31
At the GRUB screen, you have a "recovery mode" option, choose it and you will get a root prompt. Then

Code:

cat /etc/passwd | grep 1000

will give you your username, you can then do

Code:

passwd USERNAME

to set a new password.

Good luck !

---

### Post by Chicken_Man on 2007-03-31
I can't get into the terminal from recovery mode either.
It's impossible to login and the only option is to keep pressing ctrl+d like a zombie for nothing to happen.

---

### Post by Chicken_Man on 2007-03-31
I tried again and this time after pressing ctrl+d i managed to login under my username.
Then it printed another out of memory message, killed chown and started loading the kernel and then gnome. Then all of a sudden a blank screen appears and everything freezes, at which point i reset again.

---

### Post by r4ik on 2007-03-31
Just to be sure,
please try

[http://www.ubuntuforums.org/showthread.php?t=375391&highlight=lost+password](http://www.ubuntuforums.org/showthread.php?t=375391&highlight=lost+password)

---

### Post by Chicken_Man on 2007-03-31
But I can't even write anything.. there's no terminal, nothing. It's not giving me any control at any point during bootup.

---

### Post by r4ik on 2007-03-31
I do not get this.
How much ram have you got please also mention 1 or two banks.

---

### Post by Chicken_Man on 2007-03-31
768MB 2 banks.
It can't be a hardware problem. Everything was working perfectly until yesterday night and nobody had touched the computer for all I know.
The only running programs were Netbeans and a firefox session.

---

### Post by r4ik on 2007-03-31
Oke lets go did you reboot if not please do.

---

### Post by Chicken_Man on 2007-03-31
Yeah a bunch of times. No matter what I choose to boot in GRUB it still hangs in the end.

---

### Post by r4ik on 2007-03-31
Try,

Crtrl Alt F1

Please,
what do you get?

---

### Post by Chicken_Man on 2007-03-31
It lets me log in, then everything hangs.

---

### Post by r4ik on 2007-03-31
Sorry if i am a pain in the ...
hangs as in cant type ?

---

### Post by Chicken_Man on 2007-03-31
Yea.. all that appears is a black blank screen. Whenever I press a button the pc speaker beeps.

---

### Post by r4ik on 2007-03-31
Hardware most prob. you're graphics card  do you have a spare ?
As in other one not sure about my language sorry.

---

### Post by Chicken_Man on 2007-03-31
Nah.. just loaded a game under windows xp without any problems.
In any case, is there a way to "repair" this installation from a cd?

---

### Post by r4ik on 2007-03-31
Sorry i thought it was a stand alone.
Repair from a cd i would not know pop one in and see what the options are or
search the forum for an answer on that.
i will so the same and post back.

Good luck !

---

### Post by r4ik on 2007-03-31
[http://www.ubuntuforums.org/showthread.php?t=392035&highlight=recover+from+cd](http://www.ubuntuforums.org/showthread.php?t=392035&highlight=recover+from+cd)

---

### Post by Chicken_Man on 2007-03-31
I'll try that,
thanks a lot!

---

### Post by r4ik on 2007-03-31
Post you're results please.
Or PM if i overlook it :)

---

### Post by Chicken_Man on 2007-03-31
The option that guy is talking about doesn't exist... :confused: And I don't want to install ubuntu from scratch.

---

### Post by r4ik on 2007-03-31
Please start a new thread hope someone else can be more helpful.

---

