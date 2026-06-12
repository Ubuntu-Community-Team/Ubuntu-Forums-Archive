---
title: "Makefile help"
date: 2007-06-21
forum: General Help
---

### Post by Kzap333 on 2007-06-21
I thought I was good at ICT (I got an A* in my test) but when it comes to Linux I'm a complete noob which is strang because I usealy pick things up very quickly (like Mac).
But I am completly stuck on this entire makefile thing. I have googled it but everyone seems  to know what to do,
aprt from me!
I think it must have something to do with the terminal command promt I just need to know what the heck to type in I tryed make (then the adress of the folder with the makefile in) then I tried make (then the adress of the makefile itself) then the adress of the folder with the makefile in and then typed in make.
What the heck do I do almost all programs I download have makefiles but I am completly stumped please someone help me.
Step by step please.

*(again if you have read any of my other posts sorry about me grammer and spelling and stuff)*

---

### Post by r0ck80y on 2007-06-21
try installing make
```
 apt-get install make
```
You have to be a little more specific regarding the type of program ure trying to install

---

### Post by Kzap333 on 2007-06-21
> **r0ck80y said:**
> try installing make
```
 apt-get install make
```
You have to be a little more specific regarding the type of program ure trying to install
What do you meen also to run ```
 apt-get install make
``` do I need the internet cos Ubuntu is not picking up my wireless so I have to borrow my bro's tablet PC every Sunday and use it as a network bridge (with a crossover cable).
There are only a few things I want to install the only main one is Cinelerra [http://www.heroinewarrior.com/cinelerra.php3](http://www.heroinewarrior.com/cinelerra.php3) so if someone who has that could give me step by step instucsions that would be good.

One thing I don't get is why can't linux have a setup file like other opperating systems.

---

### Post by r0ck80y on 2007-06-21
Are u sure there is no 'configure' file in the package? This cinerella package needs:```

ALSA-1.0.11, GCC 4.1, NASM version 0.98.39, kernel 2.6.16.18 to compile anything
```
Make sure u have these on your system. And yes, u need internet to install 'make'. Also post the make errors you are getting.

---

### Post by Kzap333 on 2007-06-21
> **r0ck80y said:**
> Are u sure there is no 'configure' file in the package? This cinerella package needs:```

ALSA-1.0.11, GCC 4.1, NASM version 0.98.39, kernel 2.6.16.18 to compile anything
```
Make sure u have these on your system. And yes, u need internet to install 'make'. Also post the make errors you are getting.
Okay.
Yes there is a configure but when I duble click it nothing happens.
When I have got the ```
 apt-get install make
``` will I be able to run any makefile by just typing in make and then the adress of the makefill.

Also does Ubuntu not have this make command already on as most programs need it.

---

### Post by r0ck80y on 2007-06-21
Dont double click configure!! Go to console/command prompt. In that directory where 'configure ' is, type:```

./configure
```
You may get a message like "Good configure finished. Start make now!!" Then type:```

make
```
If there are no errors there, next step is (in the same directory):```

sudo make install
```
But its not gonna  be smooth judging by ur level of linux knowledge. You may get dependency errors for instance, cinerella might say it needs 'libmpeg' installed first. In that case install 'libmpeg' first using the same above procedure.
In any case, post ur make errors or any error u get

---

### Post by Kzap333 on 2007-06-22
In terminal totorail I've seen for Linux you have to type sudo what does it mean???

---

### Post by odiseo77 on 2007-06-22
'sudo' allows you to run a terminal program with root privileges; that's why you have to type 'sudo make install', because to install anything system wide in linux you need root privileges...

---

### Post by Kzap333 on 2007-06-22
UMMM... This is going to make me look realy dumb :oops: but I forgot to set the root password what is it by defult? I tried ubuntu.

---

### Post by odiseo77 on 2007-06-22
The root password in ubuntu should be the same password you use to login with your standard user account.

---

### Post by Kzap333 on 2007-06-22
> **odiseo77 said:**
> The root password in ubuntu should be the same password you use to login with your standard user account.
I'll try that then

---

### Post by Kzap333 on 2007-06-22
It's not working when I try to login as root it say something like Administrator cannot log in here.
So where do I log in???
It comes up with something like cannot change prilige for drive on my file system drive.
and on the other 2 the drop down lists are greyed out and it say the owner is root but I cannot login as root.

---

### Post by Kzap333 on 2007-06-22
> **r0ck80y said:**
> try installing make
```
 apt-get install make
```
You have to be a little more specific regarding the type of program ure trying to install
I get this error when I type that command
```
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
```

---

### Post by Kzap333 on 2007-06-22
I even tried putting sudo in front it asks me for the root password I put it in and it says it is wrong?!?
Help please.
edit: its working now

---

### Post by Kzap333 on 2007-06-22
> **r0ck80y said:**
> Dont double click configure!! Go to console/command prompt. In that directory where 'configure ' is, type:```

./configure
```

I'm stuck on that how do I get into the file with configure is in command prompt I tried typing it in and it does not work.

---

### Post by r0ck80y on 2007-06-22
Please use this guide first for help and then post in the forums
[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

whenever you use '**sudo**', you type your normal user passwd, NOT the root password!! When you type '**su**', here you use the root password.
And use **apt-get** method to install software; its all explained in the guide.
You type **./configure** to run that file like you run a **.exe** file in windows. Read my post carefully and you'll know.

---

### Post by Kzap333 on 2007-06-22
I get this error now
```
sh: Syntax error: end of file unexpected (expecting "then")
make[1]: Entering directory `/home/andrew/Desktop/install/cinelerra-2.1'
gcc -c -O2 -fomit-frame-pointer -falign-loops=2 -falign-jumps=2 -falign-functions=2 -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64 -I../../freetype-2.1.4/include -I../../ -DHAVE_OSS -DHAVE_FIREWIRE  soundtest.c -o i686/soundtest.o
soundtest.c:13:27: error: sys/soundcard.h: No such file or directory
soundtest.c:14:19: error: stdio.h: No such file or directory
soundtest.c:15:20: error: stdlib.h: No such file or directory
soundtest.c:16:20: error: unistd.h: No such file or directory
soundtest.c:17:19: error: fcntl.h: No such file or directory
soundtest.c:18:23: error: sys/ioctl.h: No such file or directory
soundtest.c:19:18: error: math.h: No such file or directory
soundtest.c: In function ‘main’:
soundtest.c:24: error: ‘audio_buf_info’ undeclared (first use in this function)
soundtest.c:24: error: (Each undeclared identifier is reported only once
soundtest.c:24: error: for each function it appears in.)
soundtest.c:24: error: expected ‘;’ before ‘playinfo’
soundtest.c:28: error: ‘AFMT_S16_LE’ undeclared (first use in this function)
soundtest.c:40: warning: incompatible implicit declaration of built-in function ‘log’
soundtest.c:94: warning: incompatible implicit declaration of built-in function ‘printf’
soundtest.c:96: error: ‘O_WRONLY’ undeclared (first use in this function)
soundtest.c:102: error: ‘SNDCTL_DSP_SETFRAGMENT’ undeclared (first use in this function)
soundtest.c:105: error: ‘SNDCTL_DSP_SETDUPLEX’ undeclared (first use in this function)
soundtest.c:110: error: ‘SNDCTL_DSP_SETFMT’ undeclared (first use in this function)
soundtest.c:112: error: ‘SNDCTL_DSP_CHANNELS’ undeclared (first use in this function)
soundtest.c:114: error: ‘SNDCTL_DSP_SPEED’ undeclared (first use in this function)
soundtest.c:117: error: ‘SNDCTL_DSP_GETOSPACE’ undeclared (first use in this function)
soundtest.c:117: error: ‘playinfo’ undeclared (first use in this function)
soundtest.c:126: error: ‘O_RDONLY’ undeclared (first use in this function)
soundtest.c:157: error: ‘SNDCTL_DSP_GETISPACE’ undeclared (first use in this function)
soundtest.c:157: error: ‘recinfo’ undeclared (first use in this function)
soundtest.c:162: error: ‘SNDCTL_DSP_RESET’ undeclared (first use in this function)
make[1]: *** [i686/soundtest.o] Error 1
make[1]: Leaving directory `/home/andrew/Desktop/install/cinelerra-2.1'
make: *** [all] Error 2

```

---

