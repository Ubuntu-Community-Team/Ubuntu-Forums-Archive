---
title: "Weird problem"
date: 2008-01-01
forum: General Help
---

### Post by revelationman on 2008-01-01
Well  for the last few days I have been getting my  Ubuntu  running so far I got wine installed and other apps , computers are fun again  

But here is  weird problem I am not sure if it the video driver doing this 

I have a HP Compaq  nx6325  with the Radeon 1150 

When I reboot   I get a black  screen with text in large fonts I  am lost where to start  now it in the  restricted drivers there is ati accelerated graphics enabled also the broadcom chipset

I do not want to reload this system i have with lots of pain got this system  running  great  

So anyone  has a clue 

cheers

---

### Post by ~LoKe on 2008-01-01
Try logging into that black screen.  It should be asking you for a username then password.  If you've successfully logged in, type...
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
After that, type this:
```
sudo /etc/init.d/gdm restart
```
Everything should work.

---

### Post by nirpius on 2008-01-01
If you can't log in, try running a live CD and altering

/etc/usplash.conf

MIne had a similair problem where xres and yres were set to weird values (I assumed it meant resolution and just typed in my maximum and that worked fine for me)

---

### Post by revelationman on 2008-01-01
could you just run the  command in  the terminal full screen or is that what you  are referring too 

cheers

---

### Post by ~LoKe on 2008-01-01
> **revelationman said:**
> could you just run the  command in  the terminal full screen or is that what you  are referring too 

cheers

The "black screen" you're seeing is the virtual terminal.  You need to log in then type the commands.

---

### Post by revelationman on 2008-01-01
tried that  and nothing inputed the command as you  said the nothing  i had to poweroff the laptop  and reboot again

---

