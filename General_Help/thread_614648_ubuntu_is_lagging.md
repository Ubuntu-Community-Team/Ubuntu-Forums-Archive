---
title: "ubuntu is lagging"
date: 2007-11-16
forum: General Help
---

### Post by zivxx on 2007-11-16
hey everyone,
I'm new to Linux so i don't really know how to fix things...
the problem is like that, since i installed Ubuntu my computer getting "lag" or in other words, freeze for about 6 seconds...Ubuntu is installed in my computer for 3 days, ive restarted it few times after about 60 updates that was ready to be made, and also turned it off for a night.
I thought it might be my rar,that was 512mb ddr1..so i went today to get 1gb ddr2...but still nothing better...if anyone know what to do please help...

my other problem is,
when i installed Ubuntu i was really excited and didn't mentioned all the fields in the installation, means i didn't gave password for my root user..only made adim user...is there a way to make root password now?or i need to re-install my Ubuntu

---

### Post by mellowd on 2007-11-16
Open up a terminal and type top then enter. Paste what you see there. That will show what recources are being used by the system

---

### Post by zivxx on 2007-11-16
ok i did that...you want me to post what i see there here?

---

### Post by NilsHG on 2007-11-16
how did you manage to install 1gb ddr2 memory when your computer ran on ddr1 memory before?

---

### Post by mellowd on 2007-11-16
> **zivxx said:**
> ok i did that...you want me to post what i see there here?

yes please

---

### Post by zivxx on 2007-11-16
took out the ddr1 stick..
entered the ddr2 stick..bios menu and its working

i have 2 places for 2 sticks of each, but can't run them together tho

---

### Post by zivxx on 2007-11-16
mellowd,
top - 14:59:57 up  1:30,  2 users,  load average: 0.56, 0.47, 0.42
Tasks: 113 total,   4 running, 109 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.8%us,  0.2%sy,  0.0%ni, 97.8%id,  0.0%wa,  0.2%hi,  0.0%si,  0.0%st
Mem:   1035584k total,  1021596k used,    13988k free,   376952k buffers
Swap:  1502036k total,        0k used,  1502036k free,   335100k cached

ziv@ziv-desktop:~$  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5145 root      15   0  338m  62m  14m R    1  6.2   2:50.64 Xorg               
 7557 ziv       15   0 91516  20m  12m R    1  2.1   0:00.41 gnome-terminal     
 5447 ziv       15   0 87636  29m  19m S    1  2.9   0:18.47 nautilus           
 5745 ziv       15   0  249m 101m  28m S    1 10.1   3:46.37 firefox-bin        
 5555 ziv       15   0 19076  12m 5384 S    0  1.2   0:11.66 compiz.real        
 7580 ziv       15   0  2364 1156  876 R    0  0.1   0:00.08 top                
    1 root      18   0  2952 1856  532 S    0  0.2   0:01.34 init               
    2 root      11  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      34  19     0    0    0 S    0  0.0   0:00.28 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      34  19     0    0    0 S    0  0.0   0:00.05 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      10  -5     0    0    0 S    0  0.0   0:00.03 events/0           
   10 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/1           
   11 root      10  -5     0    0    0 S    0  0.0   0:00.00 khelper

---

### Post by NilsHG on 2007-11-16
> **zivxx said:**
> took out the ddr1 stick..
entered the ddr2 stick..bios menu and its working

so your motherboard supports both, ddr1 and ddr2? thats rare, but possible ;) good for you then.
however, that means your hardware should be fast enough to run ubuntu even with 512 mb ram without any problems.

---

### Post by zivxx on 2007-11-16
oh its rare?lol i never knew that, but yea it can work with both of them..but for some reason my ubuntu laggs, it never happend on the XP you think its problem with the installation?

---

### Post by Rmantingh on 2007-11-16
> **zivxx said:**
> 
my other problem is,
when i installed Ubuntu i was really excited and didn't mentioned all the fields in the installation, means i didn't gave password for my root user..only made adim user...is there a way to make root password now?or i need to re-install my Ubuntu

I'm not going into discussions about whether it is wise or not to log in to root account.
I do it myself a lot as well :-)

You could issue following command in a terminal:

sudo passwd root

When asked, enter your own password first followed by root's password twice.

Or go to System - Administration -> Users and Groups

And set a password for the root user there.

---

### Post by mellowd on 2007-11-16
I don't see anything maxing out in your recources. Plenty of ram and cpu is avalible. hmm.

---

### Post by zivxx on 2007-11-16
Thanks Rmantingh..it worked :-)

---

### Post by zivxx on 2007-11-16
mellowd, i know thats whats making me wondering..
you think i need to re-install my Ubuntu?

---

### Post by mellowd on 2007-11-16
You said you experienced the same sort of hardware lag in xp as well. That leads me to assume more than likely its a hardware issue but thats odd. Has XP previously ever worked correctly without lag? Did it all of a sudden come or a gradual downward trend?

---

### Post by zivxx on 2007-11-16
hmm no, i said in XP i never lagged

---

### Post by mellowd on 2007-11-16
I see, my bad.

You could try a reinstall. If you've only just installed Ubuntu and haven't configured much it won't be too much of a problem. Have you also tried using another interface too see if gnome is lagging you?

---

### Post by zivxx on 2007-11-16
erm..no how can i switch interface?

---

### Post by mellowd on 2007-11-16
open up a terminal and enter this:

sudo aptitude update && sudo aptitude install kubuntu-desktop



now logout and you'll have the option of using kde instead. there will be an optin on the login menu which interface to use

---

### Post by zivxx on 2007-11-16
Need to get 229MB/230MB of archives. After unpacking 773MB will be used.
Do you want to continue? [Y/n/?]


should i continue?

---

### Post by mellowd on 2007-11-16
yeah, kde/gnome etc use quite a bit of space.

if you notice it much faster you can reinstall it from scratch but install kubuntu instead of ubuntu this time

---

### Post by bingoUV on 2007-11-16
> **zivxx said:**
> Need to get 229MB/230MB of archives. After unpacking 773MB will be used.
Do you want to continue? [Y/n/?]


should i continue?

continue if you have about 800 MB of spare hard disk space, and you are prepared to wait for the time it would take for your internet connection to download 230 MB, plus around 10 minutes installation time. 

You can do other work during this time, but your internet connection will be likely fully utilized.

---

### Post by zivxx on 2007-11-16
ok, im going to get something to eat for now while its installing, i'll be back soon and tell you whats going on

---

### Post by zivxx on 2007-11-16
ok im gona quit anything related to the internet so download will go faster, laters

---

### Post by zivxx on 2007-11-16
i downloaded the xubutu and that appear:
[http://img526.imageshack.us/my.php?image=screenshot1py2.png](http://img526.imageshack.us/my.php?image=screenshot1py2.png)

---

### Post by zivxx on 2007-11-16
please someone its really important i can barely use Ubuntu otherwise

---

### Post by bingoUV on 2007-11-16
press enter.

---

### Post by zivxx on 2007-11-16
its asking me to choose between gdm and kdm...what should i choose?

---

### Post by bingoUV on 2007-11-16
Does not matter. When it asked me, I chose gdm and my PC has not exploded (just kidding). Choose anything.

---

### Post by zivxx on 2007-11-16
ok im back well,
mellowd told me that gnome might be the reason for my lags..so i guess gdm is gnome, so i choose kdm but its still on gnome...any idea?

---

### Post by bingoUV on 2007-11-16
You chose kdm, that means kdm manages the screen that asks you for login, password etc. as soon as you boot.

 From this screen, there must be some option to decide where will you go after login i.e. gnome or kde. Look for some option saying "session", or "Desktop" etc. That will provide you with a list of available desktop environments (I think gnome and kde). You can choose kde there.

---

### Post by NilsHG on 2007-11-16
when at the screen where you enter username and password hit "F10". it should bring up a menue where you can choose between desktop environments (gnome or kde)

---

### Post by zivxx on 2007-11-16
ok i have enterd this select sessions thing..only Gnome appear

---

### Post by skymera on 2007-11-16
only gnome?

thats not right.

try reinstalling kubuntu-desktop again

sudo aptitude reinstall kubuntu-desktop

---

### Post by zivxx on 2007-11-17
ok now thats where i get really confused, i did the re install and i have:
last session
xclient script(or something like that)
Gnome
Failsafe gnome
some other gnome...
i think im just gona download kubuntu from linux site

---

### Post by zivxx on 2007-11-18
ok everyone, ive installed kubuntu and im on kde atm...but nothing got better
any idea?

---

### Post by Flying caveman on 2007-11-18
nevermind

---

### Post by Vince4Amy on 2007-11-18
Back to your first post about the memory. Usually I've found that if a motherboard supports both DDR & DDR 2 (Which is Rare). You can either use one or the other, having both DDR & DDR 2 in the same machine I've known to cause stability issues.
 
Have you tried firstly removing the DDR stick & trying the machine with the DDR2 stick on it's own?

---

### Post by Krydahl on 2007-11-18
I had a similar problem at one point. It was because Gnome was trying to resolve a DNS everytime it started a new application.

Go System ->Administration->Network

Select the hosts tab. What does it say?

---

### Post by zivxx on 2007-11-18
vince4amy,ive took out the ddr1 stick
krydahl, i can barely go on gnome after i installed kubuntu

---

### Post by zivxx on 2007-11-18
SOLVED!

the whole comp keep runing on kde, only the mouse freeze once a while

---

### Post by zivxx on 2007-11-18
sorry for posting again and again..but here goes,
what happen is,
if i use the amarok audio player...the music plays good like the freezes didn't existed but the whole other computer keep freezing, the writing the kde everything but the music..
anyone?

---

