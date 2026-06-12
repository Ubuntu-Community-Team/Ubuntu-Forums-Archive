---
title: "Boot-up stuck in text world"
date: 2008-04-30
forum: General Help
---

### Post by fuag155555 on 2008-04-30
Hey, since my upgrade to 8.04, the boot screen will show a nice kubuntu logo for roughly 5 seconds, then it moves me to tty1 and shows me an ugly text boot, and i can't see any fails or warnings in the boot process, there's a hint about sausld or something but the end result is [OK], how do I get my graphical boot back? :(

---

### Post by ibutho on 2008-04-30
When you get to the text login prompt, login and run "sudo /etc/init.d/kdm stop" and then "startx". Does KDE run? If not what are the error messages printed on the screen.

---

### Post by Wartender on 2008-04-30
the same happens to me (i'm using ubuntu 7.10 though), and i don't get a text login prompt. at least i don't think so, i'm going to see if i can log in even though it doesn't tell me to, and then i'm going to do what ibutho suggested (even if i don't log on), wait... should i do the same thing even though i'm running ubuntu 7.10? (probably not, huh?) can someone help me too?

---

### Post by fuag155555 on 2008-04-30
> **ibutho said:**
> When you get to the text login prompt, login and run "sudo /etc/init.d/kdm stop" and then "startx". Does KDE run? If not what are the error messages printed on the screen.

It does run, it logs me in like normal, it just takes me to the text prompt while its starting up, then it takes me into kdm, just wondering why i can't get the pretty boot splash to continue.

wartender, the commands should be the same for you.

---

### Post by ibutho on 2008-05-01
When you login to the terminal, try
```

sudo /etc/init.d/kdm stop
sudo update-rc.d -f kdm remove
sudo update-rc.d kdm defaults
sudo /etc/init.d/kdm start

```
Can you login using KDM?

---

### Post by danwood76 on 2008-05-01
When it says tty1 try switching to tty7:

ctrl + alt + F7

thats the graphical one ;)

---

### Post by Wartender on 2008-05-01
about what happened to me, when i boot (i don't know what tty1 or tty7 is, but it doesn't display any of that anyway). and i just found out that after it displays all the things with [OK] on the right, and they stay onscreen, i can't do anything, no matter what i type it doesn't say or do anything!!!!
this started happening after i tried to enable desktop effects, and it said it didn't recognize my video card, so i installed the appropriate driver, i rebooted, then it said it didn't detect a video card at all, so i changed the driver again, and then next time i booted, the screen turned off and that's it, so on another thread (try searching "screen turns off" in the archive) they told me to enter this: "sudo dpkg-reconfigure xserver xorg" so i did that when i booted into recovery, and i answered all the crap it asked, and i entered it correctly btw, and now this happens.
somebody help meeeeeeeeeeeeeeeee!!!!!:(

---

### Post by linxuser14 on 2008-05-09
I'm in a similar fix. tty they refer to is a terminal screen with just a login prompt. Keyboard shortcuts to the available screens are by using multiple keys. hold down ctrl+alt and press the F1 key and your in tty1. F2 key will be tty2, F3 - tty3 thru F6 then in my experience when ubuntu is running a graphical user interface (gui) its running in tty7 or ctrl+alt+F7. But it switches to it without you needing to select it. Anyway get tty1 (ctrl+alt+F1) at login enter your sign-on or name then it asks for password. Enter it and you should end up at a command prompt. My user name on my machine is XX2 so my prompt is XX2@XX2:~$
At that point its waiting for the commands like they said in previous posts.
Lots of luck. I'm going to try the series of last post's commands. i.e.

sudo /etc/init.d/kdm stop
sudo update-rc.d -f kdm remove
sudo update-rc.d kdm defaults
sudo /etc/init.d/kdm start

and see if it works for my problem. write these things down as when you do the command 
sudo /etc/init.d/kdm stop
your gui will shut down and won't be available on tty7 .
if this sequence of commands doesn't work for you I'm using the 1st one
sudo /etc/init.d/kdm stop
and getting a tty1 login screen. After logging in I've done a
sudo startx
And thats how I'm at my screen now. I'm looking for a way to keep it like
this after rebooting. Hope this last person's way is the answer. Later.
:guitar:

---

### Post by danwood76 on 2008-05-09
There has to be a reason why the GUI isnt loading up.
The errors will be in the /var/log/Xorg.0.log file (or the Xorg.0.log.old)

run these 2 commands to see if any errors or warnings are presant:
```

cat /var/log/Xorg.0.log | grep '(EE)' # This checks for errors
cat /var/log/Xorg.0.log | grep '(WW)' # This checks for warnings

```
and in the previous xorg log:
```

cat /var/log/Xorg.0.log.old | grep '(EE)' # This checks for errors
cat /var/log/Xorg.0.log.old | grep '(WW)' # This checks for warnings

```
post up any errors/warnings if you have any.

---

