---
title: "ati help"
date: 2008-02-18
forum: General Help
---

### Post by moparfan90 on 2008-02-18
i have fglrx install and when i do the command 
fglrxinfo i get:
```

moparfan90@ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

```

is this what it is suppost to say?

---

### Post by pointone on 2008-02-18
No. It should print the fglrx version.

I recommned following [this guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide").

---

### Post by Dennis on 2008-02-18
No, this is my output.

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X300/X550/X1050 Series
OpenGL version string: 2.0.6473 (8.37.6)
```

---

### Post by Shadowmeph on 2008-02-18
I just replied to a post and well I will just copy and paste it here because it was allot of typing for me follow these instructions to a tee it works for me every time 

your best bet is to do what I had to do and it took more over 20 reinstalls of Gutsy Gibbon to figure it out, during everything I state here don't do any multi tasking at all and I mean don't do anything it seems that the OS doesn't like Multi tasking while it is doing important things
1) do a fresh install
2) update
3)download Envy
( I know I know but this is how I got it took work for me tested it 3 times in a row and once I figured it out it worked all three times also remember do give in to the temptation of downloading Envy during the update because this will screw up everything)
4) install envy and then use it to install the drivers , after the install Do not turn on restricted drivers first reboot
5) after reboot turn on restricted drivers and then reboot again.
now if everything is good and you didn't Multi task during any of the Above instructions you 3d stuff should be working . If it isn't working and when you type in fglrxinfo into the terminal and it shows the Messa drivers then your best bet is to repeat the process but ans Like I stated I did over 20 reinstalls and during those 20 + reinstalls I sometimes Multi tasked which screwed up The install of the drivers the I wasted precious hours trying to reinstall but once I realized that you can't Multi task it went and I followed my instructions to the letter it works I did this three times in a row and every time it worked like a charm.
So good luck and be patient

---

