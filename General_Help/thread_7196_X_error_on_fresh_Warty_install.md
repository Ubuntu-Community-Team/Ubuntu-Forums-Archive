---
title: "X error on fresh Warty install"
date: 2004-12-05
forum: General Help
---

### Post by oddabe19 on 2004-12-05
I reinstalled Warty (after getting a new HD) and I tried to get imwheel working and my foward and back buttons via the faq by panickedthumb, so i figure that was the start of my problems anyway, i apt-get --purge remove imwheel and the config files i had to make. It worked last time i used warty.

My error is ```
There already appears to be an X server running on display :0.
 Should I try another number? 
If you select 'no' i will try to restart the Xserver on display :0..... etc...etc...
```

Now, this happenes AFTER the NVIDIA logo, a X cursor appears then the error shows. I modified my XFConfig-4 to just the 'nv' driver, got rid of the mouse options (from imwheel) with no success. So I know X works, so i think it might be a problem with GDM.

(ps Load GLcore and Load dri commented out)

Any ideas? I'm stuck in windows right now... cause I couldn't get LYNX to sign into the forums.

---

### Post by daniels on 2004-12-05
Can't tell you anything without /var/log/XFree86.0.log, sorry.

---

### Post by tricky1 on 2004-12-05
I have the same error, but this was after having Mplayer lock on me and not being able to open a terminal to kill it, so i had to hold the power button in (*,)  and upon reboot got the above error, here is my log as stated above...

[XFree86.0.log](http://www.magefreedom.org/junk/XFree86.0.log)

Help Appreciated cause Windoze is currently driving me nuts

---

### Post by tricky1 on 2004-12-05
okay, managed to fix it
once you get the screen that says:
"There already appears to be an X server running on display :0....."
press Ctrl+Alt+f1
login using your info
ps aux | grep gdm
sudo kill GDM_PID
sudo apt-get install --reinstall gdm
startx or reboot

---

### Post by oddabe19 on 2004-12-06
didn't work...

hmmm... it seems as though my /home directory was deleted.... which kinda is scaring me, since I didn't delete it.... and i've been in windows, and noone touches my computer.

---

