---
title: "How do I make my Linicks turn itself off after a given time?"
date: 2006-12-22
forum: General Help
---

### Post by Kittie Rose on 2006-12-22
I am leaving my computer on to download something over Christmas and I will be away from it. I am wondering if there's a way I can set it to shut down after a day or so.

---

### Post by tagra123 on 2006-12-22
> **Kittie Rose said:**
> I am leaving my computer on to download something over Christmas and I will be away from it. I am wondering if there's a way I can set it to shut down after a day or so.


Menu:  System - Prefereces - Power Management

Several setting are there.

---

### Post by MrHorus on 2006-12-22
FYI it's Linux - not Linicks.

---

### Post by 23meg on 2006-12-22
You can use *shutdown*.
```
sudo shutdown -h 900

```will power down your computer after 900 minutes.```
sudo shutdown -r 04:33
```will reboot your computer at 04:33. If you'll close the terminal in which you ran it, add & to the end of the line```
sudo shutdown -h 900 &
```to make it run in the background.

---

### Post by dannyboy79 on 2006-12-22
> **Kittie Rose said:**
> I am leaving my computer on to download something over Christmas and I will be away from it. I am wondering if there's a way I can set it to shut down after a day or so.

sure, there is a program called shutdown. it's in your PATH also. first create a file named shutdown.allow and store it in /etc/. within this file add your username on 1 line. so if your username is david your file would simply contain 1 line:
david
and that's it. then save the file and close it. the shutdown command will use this file to allow a user who is not root to shutdown the system. so first figure out how many hours you want it to wait before shutting down from the time you enter the command. so, say you're going to enter the command at 4:00 pm on the 23rd of dec. and you want your computer to shut down at 4pm on the 25th of dec.
 you would enter this in the terminal

shutdown -t 10 -ahHP +1440

this command tells the system to shutdown and halt or poweroff in 1440 minutes. it's going to wait 10 seconds after it tells the system it's shutting down before it actually does. If you want to double check my command just check the man pages. do man shutdown in a termianl and you can read the man page for yourself. good luck. i think this should work, I wouls suggest trying it out before you actually type in the command just prior to leaving. so do a test using this command and instead of using the 1440 minutes, use like 5 minutes to see if the command I have given ya works. let me know. another way would be to add it to cron maybe? don't use cron though so you'll have to investigate this yourself.

also just read about the "at" command. check out the man pages. it's really self explanatory. wow, I was typing all this and no other responces were here, then I hit enter and there's a bunch. glad to see this forum is so helpful!

---

### Post by dannyboy79 on 2006-12-22
> **23meg said:**
> You can use *shutdown*.
```
sudo shutdown -h 900

```will power down your computer after 900 minutes.```
sudo shutdown -r 04:33
```will reboot your computer at 04:33. If you'll close the terminal in which you ran it, add & to the end of the line```
sudo shutdown -h 900 &
```to make it run in the background.


i was trying to help him and I have never used this command but I read the man pages. I didn't think you could use sudo because he won't be here to enter the password but now that I thing of it, he is going to enter the password right away when he first types the command in right???? i see you didn't include creating the shutdown.allow file? would the way I suggested work? without using sudo but creating the allow file and adding his username to it? also, according to the man pages, if you are using minutes, you have to have a plus sign, so it should be +900 not just 900. the command would try to read the 900 as a time since that's the default. aren't I correct about this. at least that's how I read the man page??

---

