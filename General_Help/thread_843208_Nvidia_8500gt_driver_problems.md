---
title: "Nvidia 8500gt driver problems"
date: 2008-06-28
forum: General Help
---

### Post by BumbleB on 2008-06-28
Ok, this is my first time using Ubuntu (sorry for saying its Kubuntu), but I'm getting this bug which is quite frustrating, because i have to reinstall Ubuntu all over again.

Well, the problem occurs when i enable the NVIDIA accelerated graphics driver by Going to SYSTEM>HARDWARE DRIVERS>TICKING ENABLE THE DRIVER

So i download it, install it and i have to reboot.

So im rebooting, all goes well, I have my first screen (dont know what it is called) then I start loading GRUB 1.5, I boot Ubuntu, the loading screen comes up, then when it finishes the screen goes black, and simply stays like that.

I dont know if its my Graphics Card or a bug, but it quite annoying not having the ability to use 3D features such as compiz.

Well sorry for the story, but i had to give an idea of what I mean, and i hope there is a solution, as for now, ill stay with windows.

About ubuntu:
I have not updated it, well i am now, but because of going over my download limit, it will take me 7hours to finish (LOL).

Well i hope theres a solution

BumbleB

---

### Post by daleus on 2008-06-28
Restricted Drivers Manager == Chocolate Fireguard.

use envy (or envyNG if you are running 8.04) it installs the 8500GT Driver really good and formats your xorg.conf for you, so you can just use the 3D effects.

(I myself have an 8500GT in my desktop, and I can confirm this method is the best!)

---

### Post by PmDematagoda on 2008-06-28
Jockey(which is the new Restricted Drivers Manager) isn't that bad since it works rather well on quite a lot of systems, but admittedly it isn't that perfect and there is still a bit more to do. 

But onto the problem at hand, boot Ubuntu in Recovery Mode and once you reach the terminal, execute:-
```
dpkg-reconfigure -phigh xserver-xorg
```
and then reboot the PC by executing:-
```
reboot
```
then see if that brings back (K)Ubuntu.

---

### Post by BumbleB on 2008-06-30
> **daleus said:**
> Restricted Drivers Manager == Chocolate Fireguard.

use envy (or envyNG if you are running 8.04) it installs the 8500GT Driver really good and formats your xorg.conf for you, so you can just use the 3D effects.

(I myself have an 8500GT in my desktop, and I can confirm this method is the best!)

Ok I've installed the EnvyNG because I'm running 8.04, but it still happens, I'm still getting that black screen.

---

### Post by PmDematagoda on 2008-06-30
> **BumbleB said:**
> Ok I've installed the EnvyNG because I'm running 8.04, but it still happens, I'm still getting that black screen.

Boot Ubuntu in Recovery Mode and instruct Ubuntu to do an xfix, after that is done, see if that fixes anything.

---

### Post by BumbleB on 2008-07-01
> **PmDematagoda said:**
> Boot Ubuntu in Recovery Mode and instruct Ubuntu to do an xfix, after that is done, see if that fixes anything.

What do you mean by that??? 

I did what you said before by doing the dpkg, that brings back Ubuntu, but the reason I installed linux is to use the cool visual effects, and everything else, instead of working countless hours having to do the samething over and over.

On the other part, I've installed envyNG, but ubuntu still doesn't recognize my graphics card, every time i log in, it tells me that its running on "low-graphics" and a tab saying configure, so i configure everything, and i still run in low graphics... and to stop that from happening i use the dpkg thing, but that restores everything back to normal... One last thing, before I find out I'm wasting my time, whats the difference between (K)Ubuntu and Ubuntu, is Ubuntu only to run on laptops, because I'm using a desktop

I'm so confused???

---

### Post by BumbleB on 2008-07-01
Another thing, is it right to have 16 diffrent xorg.conf, most of them are from the time where i configured my monitor and graphics card.

---

### Post by Plasma_NZ on 2008-07-01
ok i know i had no-end of problems getting both my 8500GT's to run..

here's how i got mine to go..

1. downloaded drivers from nvidia
2. ctrl + alt + f1
3. sudo /etc/init.d/gdm stop
4. went to the directory the drivers package was located (4 me it was /home/myaccount/Desktop)
5. sudo sh NVIDIA-DRIVER-PACKAGE-NAME and followed instructions..

When done

startx - all ran fine and then i opened a terminal and typed

sudo nvidia-settings

and configured

- only thing when u install drivers this way is when there's a kernel update u have to reinstall driver, but that's no biggie.. hope this helps..

As for having 16 different xorg.conf's - u can remove all the old ones but make sure u keep your current one which is called   xorg.conf , once u delete the others, backup your current one with ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

---

### Post by PmDematagoda on 2008-07-01
Also you may want to remove the nvidia-glx-new package if you have it with:-
```
sudo apt-get remove --purge nvidia-glx-new
```

---

### Post by BumbleB on 2008-07-04
> **Plasma_NZ said:**
> ok i know i had no-end of problems getting both my 8500GT's to run..

here's how i got mine to go..

1. downloaded drivers from nvidia
2. ctrl + alt + f1
3. sudo /etc/init.d/gdm stop
4. went to the directory the drivers package was located (4 me it was /home/myaccount/Desktop)
5. sudo sh NVIDIA-DRIVER-PACKAGE-NAME and followed instructions..

When done

startx - all ran fine and then i opened a terminal and typed

sudo nvidia-settings

and configured

- only thing when u install drivers this way is when there's a kernel update u have to reinstall driver, but that's no biggie.. hope this helps..

As for having 16 different xorg.conf's - u can remove all the old ones but make sure u keep your current one which is called   xorg.conf , once u delete the others, backup your current one with ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

The part where you mean "went to the directory the drivers package was located (4 me it was /home/myaccount/Desktop)"

is that still in the "ctrl alt F1" stage???

or did u just click on the driver???

---

### Post by BumbleB on 2008-07-04
And with these codes you guys keep throwing at me, where do i put them in?????

---

### Post by Plasma_NZ on 2008-07-04
Ok.. i'll make it more understandable


Download your gfx card's driver from NVIDIA's website..

put it on your desktop..

once done that press

```
ctrl + alt + f1
```

This will throw you out of the GUI and in prompt mode... which needs to be done..

It will ask u for your username/password, enter them

Once logged in (still in prompt mode) u need to stop the GomeDisplayManager by issuing the following command

```
sudo /etc/init.d/gdm stop
```


that will stop gnomedisplaymanger so u can install the driver..

now u need to move to the directory u put the driver, which would be desktop.. to move there use 

```
cd /home/you_user_name/Desktop
``` replace "your_user_name" with your user-account name u use to login

once there, u need to issue the command

```
sudo sh NVIDIA-Linux-x86_64-173.14.09-pkg2.run
```
This is nvidia's latest release for this card for 64bit linux OS, if u have 32bit it should read 
```
NVIDIA-Linux-x86-173.14.09.pkg1.run
```

From there just follow its directions... it will try and download a module for your kernel but that will probley fail, so it'll probley compile one automatically for u, and also ask if u want to use 32bit something, just hit yes..

once it has finished and thrown u back to prompt - type

```
 startx 
```

It should load, once it has open a terminal window and type

```
sudo nvidia-settings
```

this should launch the nvidia settings manager.. and change settings as u need..

Hope this helps your problem..

---

### Post by BumbleB on 2008-07-04
> **Plasma_NZ said:**
> 
```
NVIDIA-Linux-x86-173.14.09.pkg1.run
```

From there just follow its directions... it will try and download a module for your kernel but that will probley fail, so it'll probley compile one automatically for u, and also ask if u want to use 32bit something, just hit yes..

once it has finished and thrown u back to prompt - type

```
 startx 
```

It should load, once it has open a terminal window and type

```
sudo nvidia-settings
```

this should launch the nvidia settings manager.. and change settings as u need..

Hope this helps your problem..

From there on when i do the code, its telling me it cant open it???

and im using the 32bit version

when i do 64 it stop and tells me im using 64...

---

### Post by Plasma_NZ on 2008-07-04
Ok do this for me..

Open up a terminal window from - applications - accessories - terminal

type in 

```
uname -a
```

and copy and paste the results into a post here for me..
this way we can determine which ubuntu you are using, weather it's 32bit or 64bit..

And we can go from there..

---

### Post by BumbleB on 2008-07-04
> **Plasma_NZ said:**
> Ok do this for me..

Open up a terminal window from - applications - accessories - terminal

type in 

```
uname -a
```

and copy and paste the results into a post here for me..
this way we can determine which ubuntu you are using, weather it's 32bit or 64bit..

And we can go from there..

2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux

---

### Post by Plasma_NZ on 2008-07-04
> **BumbleB said:**
> 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux

ok, heres the revised instructions, in breif

**Please remeber linux is very specific with code, everything needs to typed out exactly as stated, linux is capital specific **

--------------------------------------------------------------------

Download your driver which should be 

> NVIDIA-Linux-x86-173.14.09.pkg1.run

the follow the directions to install

..

Press 

```

ctrl + alt + f1
```

This will throw you out of the GUI and in prompt mode... which needs to be done..

It will ask u for your username/password, enter them

Once logged in (still in prompt mode) u need to stop the GomeDisplayManager by issuing the following command

```

sudo /etc/init.d/gdm stop
```


that will stop gnomedisplaymanger so u can install the driver..

now u need to move to the directory u put the driver, which would be desktop.. to move there use

```
cd /home/you_user_name/Desktop
```

replace "your_user_name" with your user-account name u use to login

once there, u need to issue the command

```

sudo sh NVIDIA-Linux-x86-173.14.09.pkg1.run
```

From there just follow its directions... it will try and download a module for your kernel but that will probley fail, so it'll probley compile one automatically for u, and also ask if u want to use 32bit something, just hit yes..

once it has finished and thrown u back to prompt - type

```

 startx
```

It should load, once it has open a terminal window and type

```
sudo nvidia-settings
```

this should launch the nvidia settings manager.. and change settings as u need..

Hope this helps your problem..

---

### Post by Plasma_NZ on 2008-07-05
Would like to know if this has helped..

---

### Post by BumbleB on 2008-07-05
> **Plasma_NZ said:**
> Would like to know if this has helped..

Sorry for the late reply...

I'm getting a problem, and i think it needs my system to be updated, but when i start installing it i get this error message saying 

"ERROR: You do not appear to have libe header files installed on your system. please install your distribution libe development package."

But yeh, i only need my libe thing and it should work.

---

### Post by Plasma_NZ on 2008-07-06
ok.. so install them using 

```
sudo apt-get install build-essential
```

u also might want to make sure u have the source for your current kernel your using too

to find out which kernel u are running use 

```
uname -a
```

from there u will want to use 

```
sudo apt-get install linux-headers-2.6.24-19-generic 2.6.24-19.34
```

yours might vary so change accordingly.. from there try re-installing drivers... good luck hope this helps..

---

### Post by BumbleB on 2008-07-07
Well Plasma...

Sorry to say, it didn't work, that means i now have the black screen of death:(, thank you for your help and all, but it didn't work, and ill be going back to windows, nothing will work, and i dont think anything will.

But still thank you for your help

Cheers,
BumbleB

---

