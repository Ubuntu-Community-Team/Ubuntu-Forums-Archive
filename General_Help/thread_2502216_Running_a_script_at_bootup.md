---
title: "Running a script at bootup"
date: 2024-11-05
forum: General Help
---

### Post by 1jarwolf on 2024-11-05
Hello everyone! I have just installed Ubuntu. I have not used this operating system for many years so I am now a beginner...again. So, in particular, I want to run a script at boot.

I have done some research and saw that I had to run the command:
> sudo vi /etc/rc.local
however, after this, I do not know how to save the file. I somehow found out to use the down arrow to get to a blank spot and then press the insert key to start typing in the command. From there, I was stuck so it was a dead end. The command I wish to insert there would be as follows:
> sudo macchanger --random enp5s0

     After realizing this did not work, I tried to go to "Startup Applications Preferences" and click "Add" and I typed in the above command into the command spot and hit save. I then rebooted the system and once back in, I opened up a terminal and typed in 
"ip addr" and the address was not changed meaning, it did not work. I am at a loss and do not know what to do anymore.

Thanks in advance!

---

### Post by 1fallen on 2024-11-05
Some catch up homework: [https://linuxize.com/post/how-to-save-file-in-vim-quit-editor/](https://linuxize.com/post/how-to-save-file-in-vim-quit-editor/)

---

### Post by &amp;KyT$0P# on 2024-11-05
> **1jarwolf said:**
> I have done some research and saw that I had to run the command:
> sudo vi /etc/rc.local


Those are some very old instructions.  In current Ubuntu versions the way to run a custom script during boot is to create a systemd service.

> The command I wish to insert there would be as follows:
[QUOTE]sudo macchanger --random enp5s0
[/QUOTE]

Why not just configure NetworkManager to randomize the MAC address?

---

### Post by TheFu on 2024-11-05
> **halogen2 said:**
>  Why not just configure NetworkManager to randomize the MAC address?

+1.  I think **nmtui** has this option.

---

### Post by davetheoldcoder on 2024-11-06
> sudo vi /etc/rc.local

It's useful to learn the basics of *vi*, in case that's the only choice, but *nano* is easier and self-explanatory.

---

### Post by 1fallen on 2024-11-06
> **TheFu said:**
> +1.  I think **nmtui** has this option.

+1 *nmtui* command for nice menus when editing connections. And painless. :)

---

### Post by TheFu on 2024-11-06
There are lots of different editors.  For routers and Unix systems, vi/vim is THE standard. But on Linux Desktops, the user can choose whichever editor they prefer. A few are pre-installed, but installing one of the 20+ others shouldn't be hard.  There are some that are very much like Notepad++, if that's to your liking.  **Geany** is one of those.  Kate, Gedit, nano, vim, emacs, and there are so many others.  

To have sudoedit use whatever editor you prefer, just add a line like this to the bottom of your ~/.bashrc
```
export EDITOR=gedit
```
That's it and gedit will be used going forward, if it is installed on the system.

Of course, the power that vim provides to an expert vim user is beyond what any other editor can touch, but that's a different question and it takes years to learn vim's greatness. Most typical Ubuntu Desktop users aren't really interested in that - so Kate, or Gedit or Geany are probably all they want/need.   OTOH, when I first started on Unix over 3 decades ago, I was laughed at for wanting to use emacs.  After about 6 months using emacs, I found myself switching emacs into vi-mode more and more ... until it finally clicked in my brain to just use vim and learn 1 thing new every week.  I was gaining knowledge that would pay off for decades, so it made perfect since.

Nano is such a basic editor as to be only good for emergencies when there isn't any other choice, IMHO.  On my systems, the first boot after install, I purge nano from the system. But that's for me.  YOU do YOU and anyway you like is what it should be.

---

### Post by Skaperen on 2024-11-06
> **halogen2 said:**
> Those are some very old instructions.  In current Ubuntu versions the way to run a custom script during boot is to create a systemd service.

what if i want my script to run *BEFORE* systemd is run?  i have a script that checks for certain hardware conditions that the hardware can randomly change, and if the conditions are not as desired, will reboot (this is when the conditions can change) the whole system as fast as possible, with a minimum of processes up and running.  i plan to add a sanity check to this script to count the reboots if a writable filesystem is mounted, and halt or freeze if that count is higher than a number coded into the script. or i could let it come up like normal and run another script to email me if it had difficulty (and shutdown once the email is networked off the system ... how yet to be explored ... probably sendmail logs).

---

### Post by TheFu on 2024-11-06
> **Skaperen said:**
> what if i want my script to run *BEFORE* systemd is run?  i have a script that checks for certain hardware conditions that the hardware can randomly change, and if the conditions are not as desired, will reboot the whole system as fast as possible, with a minimum of processes up and running.

Considering that systemd is job #1 (PID1), it isn't possible.  Nothing runs before that besides EFI code for loading into RAM the boot stuff.
[https://medium.com/@boutnaru/the-linux-process-journey-pid-1-init-60765a069f17](https://medium.com/@boutnaru/the-linux-process-journey-pid-1-init-60765a069f17)

---

### Post by vanadium on 2024-11-08
> **halogen2 said:**
> Those are some very old instructions.  In current Ubuntu versions the way to run a custom script during boot is to create a systemd service.

This is indeed the official way, but rather complicated. Systemd still ships with an rc.local service that, when enabled, allows you to run a command during startup through an '/etc/rc.local' file as of old. Another way to run a command during system start is using "cron" with @reboot. cron is still enabled by default. Also here, the "modern" approach would be to use systemd timers, but again, these require more than a single line in a file to set-up (but are more powerfull, e.g., can be sheduled to run a specific time after an event, or only when a previous task is completed).

---

