---
title: "How to find WHO started bash?"
date: 2013-08-18
forum: General Help
---

### Post by andreaconsole on 2013-08-18
Everytime I plugin an usb flash drive in my laptop (kubuntu 13.04), something starts a bash process that remains open and that doesn't allow me to unmount the pendrive. I can unmount it only after having forced the bash process to terminate. Any hint?

---

### Post by zero2xiii on 2013-08-18
Hay,

Here are some options as to start digging into the issue.

If the terminal that opens up are interactive (you can run commands in it) try seeing what is run from there:
```
ps -T
```
```
ps --forest
```

if it is not interactive a similar result can be obtained by:
```
ps -e --forest
```

It is very similar to "tree". You should be able to see what started the other terminal and (if any) what is being executed from it.

Hope this helps.

---

### Post by andreaconsole on 2013-08-18
Thank you! As I found, the answer was quite obvious: dolphin! (since the terminal window is not visible, I succesfully use the last command you suggested)
So, when I plug in the pendrive, if I mount it and browse with dolphin, it opens this bash session that prevents me from unmounting the device. If I close dolphin, I can unmount the pendrive from the system tray. What's wrong with dolphin?

---

### Post by zero2xiii on 2013-08-18
Hay,

That is strange behavior. I have no idea why dolphin would do that, maybe some custom commands that are being run?

What happens when you run dolphin from terminal and then browse the drive and close dolphin? (also note any terminal output that might be of interest).

Is dolphin swapped in for another file manager? (This might be the cause of an unterminated command eg "dolphin &")

We need to find a purpose for the terminal to understand what is causing this behavior.

Cheers

EDIT:
I will actually include this to save time.

Open up everything up to the point where you know dolphin created the terminal and then continue from there:
```
sudo -i
apt-get install reptyr
echo 0 > /proc/sys/kernel/yama/ptrace_scope #This is temporary, see "man reptyr".
exit
ps -e | grep bash #to get a list of all bashes running and their PIDs
ps #to get the PID of the current terminal, note the other PID (This should be the terminal ran by dolphin) called here PID_other
reptyr PID_other

```

Now the terminal created by dolphin should be in the current terminal. Check the process is not in the background by running "fg".
If there is an error: "bash: fg: current: no such job" it means it is an empty terminal (nothing running in it).
Just double check by running ps again, this should be the only output:
```
PID TTY          TIME CMD
27346 pts/4    00:00:00 bash
27825 pts/4    00:00:00 ps
```

If this is the case, it is somewhat save to assume it is an empty terminal. Also make a note of "pwd". It should be your home directory.
If all of the above checks out, I would think you can assume some command is not being terminated properly.

---

### Post by andreaconsole on 2013-08-18
Thank you for your effort!
I was disappointed for dolphin's lack of verbosity, indeed, but I didn't know about reptyr. 
However this is the result:

```
reptyr 24377
[-] Timed out waiting for child stop.
[+] Allocated scratch page: b72af000
[+] Looking up fds for tty in child.
[+] Resolved child tty: 8802
[+] Found an alias for the tty: 0
[+] Found an alias for the tty: 1
[+] Found an alias for the tty: 2
[+] Found an alias for the tty: 255
[+] Opened the new tty in the child: 3
[+] Set the controlling tty
andrea@andrea-K50IJ:/media/VOLUME$ fg
bash: fg: attuale: job inesistente
andrea@andrea-K50IJ:/media/VOLUME$ ps -e | grep bash
23634 pts/1    00:00:00 bash
24377 pts/3    00:00:00 bash
andrea@andrea-K50IJ:/media/VOLUME$ pwd
/media/VOLUME
```

Is this what you expected to see?

However, even if this bash process seems stuck and it doesn't do anything, probably it does something when I plug in the pen drive and it cannot terminate its job for some strange reason. I think I should see this error to solve the problem...

EDIT: it's something related to my account: no problem after logging in with a test account! Probably I can simply delete dolphin related folder

---

### Post by zero2xiii on 2013-08-18
Hay,

Well SOMETHING is being executed since your working directory changes to:
> /media/VOLUME

Also the ps you gave was for all running processes, when you only run "ps" it shows the current process and child processes.

It might be something to do with the current user's setting.

You can try deleting the dolphin settings folder and see if that fixes the issue.

Last thing, please plug the device in and immediately run:
```
dmesg | tail --lines=25 
```

This should show us any errors that might be cause by the drive. Albeit I think this will not produce anything useful. But it might be worth a try. (before you delete the settings folder).

Cheers

---

### Post by andreaconsole on 2013-08-19
didn't find any error... however, although quite drastic, renaming .kde directory from a console session did the trick.
Thank you again!

---

