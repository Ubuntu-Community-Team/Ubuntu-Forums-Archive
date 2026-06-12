---
title: "Ubuntu won't start after I edited xorg file when I tried using dual monitors"
date: 2007-01-26
forum: General Help
---

### Post by Darkstar0082 on 2007-01-26
I tried to use dual monitors and followed the advice in this thread [http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174) and have seemed to screw my whole system up. When I try to start ubuntu it says "failed to start the X server..." and "Fatal server error: No Screens Found". I'm not sure what to do but in that thread it says something about backing up your system and gives a command that I did use. How do I return my Ubuntu system back from that previous command if possible. I am a big NEWBIE so I might need a step by step detailed instruction. What's this recovery mode option that I see? I tried using that command to fix the problem but that didn't work. Thanks in advance for your help.

---

### Post by fenian on 2007-01-26
After all those error messages you should get to a black and white text only screen, log in with your username and password then enter this...
sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by guysmiley25 on 2007-01-26
When this happened to me awhile ago when I was starting out. I did the following, but there probably is a better way.

Boot to a Live CD ubuntu/kubuntu/xubuntu etc.
Mount the partition that contains your intstall in the terminal.

```

mkdir local
sudo mount -t ext3 /dev/hda1 local

```

Then goto where you xorg file is.

```

cd local
cd etc
cd X11
ls

```

Then hopefully you can restore an old xorg.conf file.

```

sudo mv xorg.conf.backup xorg.conf

```

You may not need to use a live cd, but you need to access your xorg.conf file some how. Also you maybe able to configure X.

---

### Post by Darkstar0082 on 2007-01-26
Thanks for the advice.. But I am not sure how to use those commands. In the black and white screen, how would I login?

---

### Post by fenian on 2007-01-26
When the error messages pop up does it ask you if you want to see the x log or something like that?

---

### Post by Darkstar0082 on 2007-01-26
Yeah it asks if I want to...I can get to recovery mode ( I think that is the black and white text  screen you were referring to. But how do I log on with my user name and password?

---

### Post by fenian on 2007-01-26
O.k. once you get to the recovery screen type your username hit enter type your password hit enter.Now you should be logged onto ubuntu in text only mode from here you can type the command
sudo dpkg-reconfigure -phigh xserver-xorg
this should reset your xorg to default settings.

OR

You can type 
sudo nano /etc/X11/xorg.conf
this will open your xorg.conf file in nano (a terminal based text edit program) you can then try to fix whatever may be wrong with your xorg.

---

### Post by Darkstar0082 on 2007-01-26
SUCCESS! finally back to the default setting! thank you so much for your help (although I was stuck in the black and white command mode trying to type my username a million times until I typed login randomly and luckily was prompted to sign in, for anyone who wanted to know how to login) I can't thank you enough for your support!

---

