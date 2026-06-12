---
title: "Uberkey / LKL"
date: 2008-01-08
forum: General Help
---

### Post by cbarboza on 2008-01-08
Has anyone successfully gotten Uberkey or LKL installed and configured to work properly on Ubuntu 7.04?  I'm looking for it to start automatically on boot, in the background and log to a file.  Maybe someone created a .deb package?

---

### Post by opscure on 2008-01-23
yes I got it to work ok.  you need all the dependencies installed ie. sudo apt-get install whateverpkg
after that I installed expect to automate the password process  and used a script in the autostarted applications (file ran: ```
expect log.sh
```) that ran the following code from log.sh
```
spawn sudo lkl -l -k /home/test/lkl/keymaps/us_km -o /pmp/logs/key.log
expect Password:
send "password\r" 
interact
```

yet I am having problems when I upgraded to 7.10; for some reason or another lkl is taking up 30-60% of my cpu and is sporadically blocking my keyboard port, repeating key strokes, and shutting down due to segmentation faults.  If anyone has a way around these issues in gusty it would make me very happy.

---

### Post by cbarboza on 2008-01-26
Thank you for the reply.  I installed expect.  When I entered 'expect log.sh' into a terminal, it says the file or directory doesn't exist.  I think I may be missing something here.  I currently have LKL installed and run it by doing the following in terminal:

sudo lkl -k /usr/share/lkl/keymaps/us_km -o /home/`echo $USER`/.cart/log.log -l

I then exit out of the terminal, then enter the following:

sudo lkl -k /usr/share/lkl/keymaps/us_km -o /home/`echo $USER`/.cart/log.log -l &

I can then enter and get my terminal prompt back, then close terminal.  This leaves LKL working in the background while logging to the log.log file, in a folder that I've name .cart.

I don't know enough yet about creating a script to have this automatically done each time the computer boots up and not having to enter a root password.

Also, I had read some other posts about correcting certain lines in the keymap files for LKL so that it would better output, rather than some garbled words.  The posts were a little unclear to me because it went line by line in number, which didn't seem to match the keymap files I found in my files.   I would also like to fix this as well.

---

### Post by frojnd on 2008-01-28
I have installed lkl on 7.10 and I am missing something here: 

sudo lkl -l -k /usr/share/dock/lkl/us_km -o /usr/share/doc/lkl/loglkl.txt

Started to log port 0x60. Keymap is /usr/share/dock/lkl/us_km. The logfile is /usr/share/doc/lkl/loglkl.txt.

unable to find keymap-file: No such file or directory
a keymap is required!! run lkl with -k <keymap>


What's up with this keymap, if someone would help I'd appreciated!

---

### Post by frojnd on 2008-01-30
> **frojnd said:**
> I have installed lkl on 7.10 and I am missing something here: 

sudo lkl -l -k /usr/share/dock/lkl/us_km -o /usr/share/doc/lkl/loglkl.txt

Started to log port 0x60. Keymap is /usr/share/dock/lkl/us_km. The logfile is /usr/share/doc/lkl/loglkl.txt.

unable to find keymap-file: No such file or directory
a keymap is required!! run lkl with -k <keymap>


What's up with this keymap, if someone would help I'd appreciated!

Nevermind about this: I've change the path: sudo lkl -l -k /usr/share/lkl/keymaps/us_km -o /usr/share/doc/lkl/loglkl.txt


But now now there is a new problem, it wont work as I wanna to, I can't write into firefox nor anywhere :S Opscure I'm having the same problems as you.

---

### Post by opscure on 2008-04-02
LKL seems to function in the correct manner on 7.04.  Gusty seems to have a problem with the iopl() system call.  For a bit more information about this see my other post here: [http://ubuntuforums.org/showthread.php?t=675937](http://ubuntuforums.org/showthread.php?t=675937)

I am still waiting for a more in depth explanation of why this is occurring from any of the wizards out there...

In response to cbarboza:

You should have created the /home/`whoami`/log.sh file with the following code
```
spawn sudo lkl -l -k /usr/share/lkl/keymaps/us_km -o /home/`whoami`/.cart/log.log
expect Password:
send "password\r" 
interact
```


Once you have created this file then use the autostarted applications feature in applications->settings->Autostarted Applications and enter:
```
expect /home/`whoami`/log.sh
```

---

### Post by Baka Dasai on 2008-05-23
> **opscure said:**
> ...when I upgraded to 7.10; for some reason or another lkl is taking up 30-60% of my cpu and is sporadically blocking my keyboard port, repeating key strokes, and shutting down due to segmentation faults.  If anyone has a way around these issues in gusty it would make me very happy.

I'm still having this problem with lkl in 8.04.  Anybody have an answer?

---

