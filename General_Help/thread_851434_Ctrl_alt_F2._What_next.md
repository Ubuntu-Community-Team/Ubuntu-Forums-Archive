---
title: "Ctrl alt F2. What next?"
date: 2008-07-06
forum: General Help
---

### Post by Robbyx on 2008-07-06
Sometimes a program freezes and effects the ability of other actions. After I press ctrl alt F2 and it drops me into the manual login, what should I do next to restart the system and minimise the loss of data.

---

### Post by ibuclaw on 2008-07-06
Instead of Ctrl Alt F2, you can use **Ctrl+Alt+Backspace** to restart X and return to the login screen.

Although, if you wish to carry on with your current method, just login to the VT session and type in
```
sudo killall **appname**
```
Then return to your X session (Ctrl+Alt+F7), then continue with your duties.

Regards
Iain

---

### Post by isecore on 2008-07-06
Another alternative is to restart X (the graphical interface). When X freezes, simply push ctrl-alt-backspace. This will restart X without restarting the computer, then you can login again. Be aware though that you lose any unsaved data in any open applications.

If ctrl-alt-backspace won't do anything you can use a terminal (getting to it as you described) and then after login issuing

```
sudo /etc/init.d/gdm restart
```

If that doesn't do the trick either (which is rare) you can raise a skinny elephant. It's a silly name for a simple meme.

Hold down alt + SysRQ (often also labeled Print Screen) and press the following keys in order:

R - raising (switches keyboard from raw mode)
S - skinny (sync all mounted filesystems)
E - elephants (shuts down all processes except init)
I - is (terminates all processes except init)
U - utterly (remounts all filesystems in read-only mode)
B - boring (immediately reboots the system)

This is for when nothing else works.

---

### Post by Robbyx on 2008-07-08
Thank you both for your responses. 

Is there any restart combinaton of keys that does not bring a loss of data?

Robin

---

### Post by rossjman1 on 2008-07-08
What's the difference between these commands?

> 
sudo reboot
sudo shutdown -r now
sudo /etc/init.d/gdm restart

---

### Post by artir on 2008-07-08
The 1 and 2 reboots and the last one restarts only the GDM, not the whole system.

---

### Post by sayakb on 2008-07-08
```
sudo init 0
```

---

### Post by Robbyx on 2008-07-08
It seems that after Ctrl alt F2 I should in preference run 

sudo init 0 

so as to avoid a loss of data.

sudo init 0 seems to halt the system.  I should then follow it with 

sudo /etc/init.d/gdm restart

If that  fails try the other ideas mentioned in the replies.

Have I understood properly?



I have found that killall is difficult to use unless I know the exact process name. How do I find it if I have dropped into the command line?

Robin

---

### Post by Robbyx on 2008-07-14
Would someone like to confirm my assumptions in my last posting above?

Robin

---

### Post by CatKiller on 2008-07-14
> **Robbyx said:**
> I have found that killall is difficult to use unless I know the exact process name. How do I find it if I have dropped into the command line?

Well, you can tab-complete the process name. So, for example, **killall fire** followed by TAB will complete the command to **killall firefox**. Otherwise, **ps ax** will show you all the processes that are running, with their process IDs. If you want to *really* kill a process, you can **kill -9 <*PID*>**. See **man ps** and **man kill** for more information.

---

### Post by Rhubarb on 2008-07-31
I use htop to find and kill misbehaving apps in the terminal.
```
sudo aptitude install htop
```
Then after you've logged in by pressing ctrl + alt + F2, just run:
```
htop
```
find the process / highlight the processes by pressing space, then press F9 to kill.
You may leave it open, or press Ctrl + Alt + F7 to go back into gnome.
Press F10 to quit htop if you desire.

---

### Post by Robbyx on 2008-07-31
Thank you everyone for you help. I have printed out your advice and will try it as the need arise arises.

---

