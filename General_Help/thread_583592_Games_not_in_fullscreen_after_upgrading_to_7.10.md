---
title: "Games not in fullscreen after upgrading to 7.10"
date: 2007-10-20
forum: General Help
---

### Post by -LsV- on 2007-10-20
Hi!

Before I updated from 7.04 to 7.10 my games (such as Americas Army and Enemy Territory) worked perfect in fullscreen. But after the upgrade they are just in a windows.

I have a ATI graphic card 9550 which is using fglrx drivers and "Wobly Windows" working fine - so I think the correct drivers are working. Under Restricted Drivers Manager "ATI Accelrated Drivers" have a green dot.

Does anybody have an solution?

---

### Post by ales on 2007-10-21
Hi,

I have the same problem. But I noticed this problem already in 7.04 after installing compiz. Also the mouse pointer in windowed enemy teritir disappears. I think this has something with the settings which are used for 3d desktop, because before I had ubuntu without the accelerated desktop and all games run in fullscreen. Now all games tun only windowed and change in settings does not react, the game stays in window.

I have searched the forums, but I have not found any direct solution to this problem.


Ales

---

### Post by -LsV- on 2007-10-22
I found out that Xmoto still works in fullscreen well its actually jumps in and out of a window.

In loading screen, its fullscreen
in level select its in a window
in "gamemode" its fullscreen.

I cant remember the normal behavior of this game

- But how do I then stop "compiz" - I really dont care about the "woply windows"
I tried System > Preferences > Appearance and set Visual Effects to "None" but nothing happens to my game still in a window.

My mouse cursor in Enemy Territory are the correct mouse cursor

---

### Post by ales on 2007-10-22
Hi,

the problem is then even I disable the compiz, the defect still exists. I think there will be needed to do something also with xgl. 


Ales

---

### Post by ales on 2007-10-23
hELLO I am now 100 percent sure , that this problem is caused by XGL X server. I unistalled it and restarted computer and all games now run in fullscreen. Also XGL causes the graphical defects on my ATI X800 in Urban Terror. After unistallation of XGL Urban Terror runs in Full Screen and there are no artifacts on screen. One thing stayed - cursor in Enemy Teritorry disappears and I have to quit game. This is a problem which is on my system permanent, also after unistallation of XGL. Usually if I want to play Enemy Ter. I have to reinstall the whole Ubuntu to get things work normally. 
Compiz in 7.10 is great, Ubuntu gets really nice effects and also great feeling fo user, but it seems there are more things to solve. Also I don't understand, why there is so big problem with new installation on ATIX800 and widescreen monitor 19"/black screen and monitor gets no signal, like the software is unable to handle the correct resolution or frequency/.

Ok back to Fullscreen. 

1. Have I to choose wether I want to ue compiz or run 3D games in Ubuntu, or is there a way how to handle this problem?
2. Would changing the vendor from ATI to NVIDIA solve  the issue?
3. Missing cursor in enemy can be this system problem solved?
4. Is there an automatic script, which would disable compiz when starting 3D game and setup the system for the game same way like Ubuntu without compiz has?


Yhanks a lot for any answers.


Ales

---

### Post by -LsV- on 2007-10-23
I got things to work again...
First I
#apt-get remove compiz*

Then reboot - now my desktop were really dead - with funny color striped from top to down. - So I started up in Gnome (Failsafe) - now my games runs in fullscreen - and I reinstalled compiz with #apt-get install compiz

So now if I wanna play - I just CTRL+ALT+BACKSPACE and choose Gnome (Failsafe) - and if I want compiz I just choose the normal login

I actually had the same problem with my cursor in Enemy Territory, but now its gone - so I can play normal now :)

---

### Post by Mischa on 2007-10-25
for now i managed to play urban terror by creating a new user and switching to that user when i want to play. this user does not use compiz, while my default user does.

it's just a temp solution untill someone fixes the problems with conpiz/glx

---

### Post by Diabolis on 2007-10-27
I have the same problem, but I already removed xgl and compiz :confused:

I you want to quit compiz you can do it just by replacing it with another window manager. Something like this: metacity --replace.

---

### Post by ales on 2007-10-29
Hi,


I think this issue, should be corrected as primary goal for developers of Ubuntu. It shoudl be able to run games without problrms like games under Vista with Aero.
But for now I log in to as two separate users, one with xgl, one without to play games.


Ales

---

### Post by Beretta_NZ on 2008-03-16
Same problem here. This is sure to be a priority for updates to Ubuntu/xgl, because xgl is such a basic feature. At least, let's hope that it's a priority.

---

### Post by ales on 2008-03-17
Hello, I solved my problem.   1. My mistake was, that I installed xgl and xgl-xserver. Ubuntu 7.10 supports compiz directly with 3D card. There is no need to install these 2 components.
2. My second problem was, that my ATI X800 GPU was blacklisted in compih. I had to remove in compiz config file checking of GPU. After doing that, and with installed drivers, 3D desktop started to work after restart without xgl andvxgl-xserver installed (i removed these components in synaptic). 
3. Som e chips are blacklisted cause theyhave some issues, which e not solved. For example, now I can play 3D games in fullscreen, but the screen is blinking sometimes. It is better to turn of the effects in Appereance menu before playing. Also my TV tuner won"t display picture in windowed mode, only in fullscreen. After turning of the desktop effects it works.
I suppose, that this will be no problem in case of Nvidia and not blacklisted Ati Gpu"s.

Anyway, for me is Ubuntu better than Vista.

---

### Post by Beretta_NZ on 2008-03-17
Ales, could you perhaps detail the steps, one at a time, that you went through to fix this? Terminal commands would be helpful. Thanks.

---

### Post by ales on 2008-03-18
Hi,
I will try to do that. Till Saturday. I have to find and summarize all steps. It took me 3 months till I found the solution because I am a bit busy, but I will write it here, withnterminal commands, today I am too wasted to make it. 
I have to mention, that I am  not pro user of ubuntu so I will write onlcommands and I hope it will help others.

Bye for now.

A.

---

### Post by ales on 2008-03-22
Hello,



so here are the steps:


1. Install the driver for your card so, that you will have 3D acceleration enabled without compiz.
  If you have ati just check in terminal: ** fglrxinfo**


**2. Do not install [B]xgl-xserver** in Synaptic. If you did so, go to synaptic and uninstall it.[/B]

I suppose you have Ubuntu 7.10 installed. So that means, you have also by default compiz installed.

If you got message, that effects could not be enabled, when you try to get the effects in Appear menu, you have to try to edit compiz configuration file:

3. sudo gedit /usr/bin/compiz


After restart you should be able to enable the effects. And also the fulscreen will work. 

In the configuratio file find this

# blacklist based on the pci ids 
# See [http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist) for details[B]
SKIP_CHECKS=yes[/B]
T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12"  # intel 965
T="$T 8086:2972" # i965 (x3000)
T="$T 1002:3152 1002:3150 1002:5462 1002:5653 " # ati X300 X600,X600 X700 
BLACKLIST_PCIIDS="$T"

and add there: SKIP_CHECKS=yes

Save the file and restart the Ubuntu. Compete restart not ctrl + alt + bckspace


I hope it will help you.
Please write me if it worked. 


Ales

---

### Post by TaTaE on 2008-05-04
There are two solutions for this. Try one of these:

1. Start Advanced Compiz Settings and disable "Unredirect Fullscreen Windows" in "General Options --> General".
2. Second solution is here [http://ph.ubuntuforums.com/showpost....2&postcount=10](http://ph.ubuntuforums.com/showpost....2&postcount=10)


Cheers,

---

