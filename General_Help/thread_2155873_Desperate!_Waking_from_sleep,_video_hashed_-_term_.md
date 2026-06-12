---
title: "Desperate! Waking from sleep, video hashed - term just barely readable. Losing Work!"
date: 2013-06-19
forum: General Help
---

### Post by DiagonalArg on 2013-06-19
I just came back to my computer and couldn't get the video to wake up. After some playing around, I was able to hit Control-Alt-F1 and get a just barely visible terminal.  The screen is white with vertical black lines.  The terminal responds with output that I can <<barely>> see is probably what I would expect from commands.  There is no sshd running on this machine, so I can't ssh in.

The screen is working right now with VGA input from my thinkpad, so it's not a screen issue; though I did try unplugging the power cord & plug back in with no effect. I tried the vga output from the video card on the tyan, but that's giving me a blank. I tried unplugging/replugging the DVI, but that doesn't help.

I would just shut down and restart, but I have some very important information in a running gedit that I had not saved (that info had never been saved).  I desperately need to save those info's.  

Can anyone help?  Maybe I could just copy the whole /tmp directory somewhere?

/DA

-------------
Ubuntu 12.04
Tyan S3970 (server board)
Asus VE228H
GeForce 6200 (PCI), using non-free nvidia drivers ("recommended") and using DVI output.

---

### Post by DiagonalArg on 2013-06-19
I tried this.  At the tyan's terminal, whose output I can barely make out (I can't read it, but I see that many symbols are mirror reversed, and {'s seem to replace some other symbols), I did the following:

```
sudo aptitude install openssh-server
sudo /etc/init.d/ssh restart
```

Coudn't quite be sure, but it seemed to do what I would have expected, but trying to ssh in from the thinkpad gives me a "connection timed out".

```
pgrep ssh
``` on the tyan gives me two pid's (thought I can't read the number) and ```
pgrep sshd 
```gives me one.  So it appears that sshd is running, even if I can't connect.

---

### Post by DiagonalArg on 2013-06-19
Ok, I got sshd running on the tyan, and I can log in.

Now, does anyone have any ideas how I can get my gedit data back?

Other option, maybe there's some way I can "reset" the video?

---

### Post by MidnightGrey on 2013-06-20
not 100% sure on this but doesnt gedit do periodic autosaves?
ie: if you were working on file 'mywork.txt' gedit would create the a temp file called 'mywork.txt~' in the same directory, look for that, and see what is inside it.

---

### Post by DiagonalArg on 2013-06-20
Solution was worked out, with help, in this thread:

[http://ubuntuforums.org/showthread.php?t=2155898&p=12698562#post12698562](http://ubuntuforums.org/showthread.php?t=2155898&p=12698562#post12698562)

---

### Post by Impavidus on 2013-06-20
Better to save your work before going to sleep. It rarely happens, but power failures do occur even at night. Gedit can save a file automatically every x minutes, but you have to activate that option first. Several text editors (at least nano and vim) automatically save backups when they recieve SIGTERM, which you can send even when screen and network are down by typing alt+SysRq+E (as in alt+SysRq+REISUB). I don't think gedit offers this service.

---

