---
title: "Terminal how to"
date: 2012-11-04
forum: General Help
---

### Post by offgridguy on 2012-11-04
I have been trying to use the terminal for some functions, it accepts my sudo password sometimes,  Other times says authentication error, sometimes says this function can only be performed by root.
      I am the only user, only one user account,  how do get set up as root?   How can I set the default status of sudo user ?

I am very limited in my knowledge of the terminal, have read a bunch of stuff, nothing
relevant to what I am asking here.   Thanks for looking.

---

### Post by 28c64 on 2012-11-04
You wouldn't want to set yourself up as root, that's why sudo is installed. It's dangerous if everything would be run as root all the time.

If you receive the error that the function can only be run as root, then take a close look at what you're doing and issue the sudo command if need be. The authentication error is probably due to a mis-stroke of the keys when entering in your password.

Edit: On the other hand though, tell us what you're having issues with doing specifically, we can probably help.

---

### Post by offgridguy on 2012-11-04
Specifically I have been trying to use the terminal to install a driver for my brother 
DCP7030 printer , see my thread .

[http://ubuntuforums.org/showthread.php?t=2080304](http://ubuntuforums.org/showthread.php?t=2080304)

Please don't blame this on a mis- stroke of the key board,  if you knew how many times i have tried you would realize what i mean. :)

---

### Post by 28c64 on 2012-11-04
There are logs you can check if you believe that it is telling you this in error. Next time it happens (right after it happens) go to a terminal and put:

```

nano /var/log/auth.log

```Then scroll to the very bottom and post the output here.

If it's a failed password attempt then it'll show something similar to..

```

Nov  4 23:43:36 {hostname} sudo:     {username}: 3 incorrect password attempts ; TTY=pts/1 ; PWD=/home/paul/Desktop ; USER=root ; COMMAND=gedit

```

---

### Post by offgridguy on 2012-11-05
Thank you for this info.

---

### Post by offgridguy on 2012-11-05
I appreciate the offers to help but I can't spend anymore time on this, I have given up on the printer conf.

---

