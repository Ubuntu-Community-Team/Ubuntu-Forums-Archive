---
title: "I went from not being able to play csgo to not being able to login/login loop"
date: 2017-03-22
forum: General Help
---

### Post by axemax92 on 2017-03-22
So yeah, it was a normal day, I booted my PC up and was going to start playing cs:go. Then it said 

>  Failed to create GL context: Could not create GL context: BadValue (integer parameter out of range for operation) 

So I started searching for solutions and only few came up. The only one that was for ubuntu 16.04 (which is what I use) was something about Bumblebee.
Ofc I searched up Bumblebee and installed it using 

>  sudo apt-get install bumblebee bumblebee-nvidia primus linux-headers-generic 

but that didn't quite do it for me. It installed and everything went well unless I rebooted.

Boot took a bit longer than usual and it prompted me to login (I have checked the login prompt off)
When I tried to login the screen started to login then it flashed a black background with "recovering journal" and "clean, amount of files/amount of files something something..." it flashed really quick so I couldn't make up much more.

Then I started searching a way to solve that and found something about alt+ctrl+f1-f6 so pressing them got me into console login (fyi my login name is low-tier.pl and password is all lowercase letters no numbers etc.) which showed lowtierpl login:
and when I typed my login (trying both lowtierpl and low-tier.pl, also some combinations with upper case letters etc) and my password below (which was right, I tried it many times) it would just say incorrect login. 

And that's where I am stuck now, after 2 hours of searching information and ways to solve it I decided to start my own thread.

Thanks in advance!

---

### Post by efflandt on 2017-03-24
If you want a dot in your username, you may need to change something in your system (maybe from live/install system): [http://askubuntu.com/questions/405638/what-are-the-disadvantages-of-having-a-dot-in-a-user-name](http://askubuntu.com/questions/405638/what-are-the-disadvantages-of-having-a-dot-in-a-user-name)

What graphics card/chip do you have and what drivers are you using? I would not recommend using bumblebee for nvidia with nvidia drivers because that makes things more complicated for running Steam games (additional launch parameters for the games) and may be slower for both the Nvidia and Intel graphics on a hybrid laptop. I have not used bubblebee since I had to in 13.10. Newer nvidia drivers include nvidia-prime which can switch graphics using **NVIDIA X Server Settings**. My gaming laptop no longer turns on now, but when it did, after switching Nvidia to Intel I just had to log out of X and log back in, but had to reboot after switching Intel to Nvidia. If it is a desktop, I don't think there is any point at all for installing bumblebee.

---

### Post by axemax92 on 2017-03-24
I have GTX 980TI and had the latest linux drivers, not really sure about the excact number, and can't check now, but I had NVIDIA X Server Settings. I installed the Bumblebee just because I thought it would solve my problem for csgo tirms out it didn't tho:P Anyway for me to uninstall the drivers without accessing terminal?

---

### Post by #&amp;thj^% on 2017-03-24
Can you get to tty1 or tty2....Black login window I assume?
EDIT:...Kindly disregard  Just read this **"fyi my login name is low-tier.pl" **as efflandt suggests the dot in your user name is a possible cause of not getting to a TTY1/6

EDIT#2 Applications that reads usernames might use a regex that assumes your  username follows the rules and therefore can't handle your username.

---

### Post by axemax92 on 2017-03-25
So I shouldn't be putting the dot there? The name shows without the dash or dot in tty1-6 tho, it just won't let me login there, even though I put the correct password and username.

But I guess I am just gonna make a fresh install of ubuntu, I really ain't losing anything, but time put into setuping it to suit my needs.

---

