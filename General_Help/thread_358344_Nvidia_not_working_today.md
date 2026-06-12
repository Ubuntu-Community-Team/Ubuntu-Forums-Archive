---
title: "Nvidia not working today?"
date: 2007-02-10
forum: General Help
---

### Post by Russty of Oz on 2007-02-10
Nvidia is not working on both my Ubuntu machines today.  Something to do with yesterdays updates??  I tried booting into kernel ....10 but still nothing.   How can I get them to work again?

I tried  sudo apt-get install nvidia   but it said I already had the latest installed.   In fact I had to reconfigure xserver when I booted today, as I just got a black screen at first.

Can anyone suggest anything?

Russty.

---

### Post by amano on 2007-02-10
[http://www.ubuntuforums.org/showthread.php?t=357767&page=4](http://www.ubuntuforums.org/showthread.php?t=357767&page=4)

---

### Post by Russty of Oz on 2007-02-10
Ok, I tried that but nvidia still doesn't work and nor will beryl.  Sigh!

---

### Post by Russty of Oz on 2007-02-11
I have uninstalled nvidia drivers and beryl then rebooted and reinstalled all over again using the How To and it still won't work.

Nothing works :(

---

### Post by russell.h on 2007-02-11
You tried Envy and it still doesn't work?

---

### Post by Russty of Oz on 2007-02-11
Thats right!  Still doesn't work for me.

I even reinstalled Ubuntu on my other machine and still can't get it to work.  Tomorrow I will try reinstalling again and see if I can get Nvidia to work before doing any updates.  I am at a loss to know what else to try.   There is no Nvidia splash at boot up time and when I check Nvidia settings there is no mention of what version I am using.  Now if all this only happened on one machine, I would think I had done something wrong myself, but on two separate computers, that is strange!  And the fact that I can't get them to work by uninstalling the drivers and reinstalling, sounds like it is an update that has come through that has affected it.  But of course I don't know what it was that did it, so I cant uninstall it!

SIGH! :(

---

### Post by shane634 on 2007-02-11
Ok if you have the envy script installed try this:

```
sudo /etc/init.d/gdm stop
```

  This will log you out of the Xserver. Now you need to login and password to get to a command prompt. Now type:

```
envy
```

  Choose to install the nvidia drivers and envy will do it's thing.  Now we need to get back into the Xserver so use this:

```
sudo /etc/init.d/gdm start
```

  Or you can simply reboot. Let us know it this works.

---

### Post by Russty of Oz on 2007-02-11
I have tried that several times now and each time after pressing 1 to install the drivers, Ubuntu restarts and I just get a black screen, so I have to reconfigure xserver again.  :mad: 

Any other suggestions??

---

### Post by Russty of Oz on 2007-02-11
Is there a command I can use to totally remove all the nvidia graphics drivers and anything else that might be causing my problems so I can start afresh?

---

### Post by Mba7eth on 2007-02-12
look at my scenario : 
Like you guys i couldn't install nvidia drivers. I did some mistake and  didn't follow the guide 100%. Hence i end up with a lot of xserver problems. I removed all nvidia related packages thru this commaneds : 
```

sudo aptitude purge nvidia
```
This will not remove but will tell you that couldn't find any package with the name nvidia but will give you some other hits i.e nvidia-setting, nvidia-glx, ... etc. Then i reconfigured my xserver to [COLOR="Red"]nv no nvidia[/COLOR] . Removed also envy. After that applying the guide 100% and done \\:D/ . 
Sorry for making it so long  ):P .
Do it and tell us ?

---

### Post by Mba7eth on 2007-02-12
look at my scenario : 
Like you guys i couldn't install nvidia drivers. I did some mistake and  didn't follow the guide 100%. Hence i end up with a lot of xserver problems. I removed all nvidia related packages thru this commaneds : 
```

sudo aptitude purge nvidia
```
This will not remove but will tell you that couldn't find any package with the name nvidia but will give you some other hits i.e nvidia-setting, nvidia-glx, ... etc. Then i reconfigured my xserver to [COLOR="Red"]nv no nvidia[/COLOR] . Removed also envy. After that applying the guide 100% and done \\:D/ . 
Sorry for making it so long  ):P .
Do it and tell us ? one more what is ur model ? (mine nvdia 7300GT )

---

### Post by Mba7eth on 2007-02-12
Sorry but by mistake it was submitted twice. 
Correction : > Then i reconfigured my xserver to nv no nvidia .   
to 
 > Then i reconfigured my xserver to [COLOR="Red"]nv[/COLOR] not nvidia, you're suppose not to find nvidia. 

---

### Post by Russty of Oz on 2007-02-12
I have done the purge and then I tried to install nvidia drivers using Automatix, but I got the following message:

[B]FATAL ERROR: Nvidia Driver
An apt-based error occured and the installation was unsuccessful[/B]

I then did  apt-get update but that didn't help.

NOW WHAT DO I DO  :confused:

---

### Post by Russty of Oz on 2007-02-12
Cant anyone suggest anything?:confused:

---

### Post by Russty of Oz on 2007-02-12
Now I haven't got ANY screensavers either!!! :shock: 

What is going on here?

---

### Post by Mba7eth on 2007-02-12
well i don't know if downloading from repository is the same as using automatix. 
Try this plzz : 
first Re-remove all nvidia so far installed drivers then :
[goto this guide]("http://ubuntuforums.org/showthread.php?t=336412&highlight=nvidia") 
I personally followed this guide . 
You :-$  didn't tell us about ur nvidia model  :D ?

---

### Post by Russty of Oz on 2007-02-12
> **Mba7eth said:**
> 
You :-$  didn't tell us about ur nvidia model  :D ?

It is Geforce MX 440

---

### Post by Russty of Oz on 2007-02-12
I have finally got things working on my other machine by installing the Ubuntu Ultimate edition and installing the drivers from Automatix.  So that is something.  But I would still like to get them working on my main Ubuntu machine.  However, it is late down here now so I will sleep on it and try your suggestion tomorrow.

Wish me luck!

Russty.

---

### Post by brazzmonkey on 2007-02-12
i'd suggest using envy ( [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) ), after latest kernel update i had trouble with nvidia drivers as well (ABI mismatch). i could temporary solve this issue by manually installing nvidia drivers, but i'd have to do it again after rebooting. envy solved this out.

---

### Post by Russty of Oz on 2007-02-13
Thanks brazzmonkey but I have tried the envy thing several times already with no success, it seems there was something wrong somewhere which was affecting it.

**HOWEVER!!**:guitar: 

Thanks to Mba7eth, I have FINALLY GOT IT WORKING! \\:D/ 

That last link you gave me worked a treat!  During the installation of the drivers, it came up with some errors, one said "no compiled kernel interface was found" and there were a couple of other things that I thought were going to prevent the installation but fortunately the installer was able to fix them all and now it works like new!   WHAT A RELIEF! =D> 

So it has been a frustrating few days but I am really grateful for all the help.  

THANKS AGAIN EVERYONE!

Russty.

---

### Post by Mba7eth on 2007-02-14
No need to thanks dude :D .... A lot of people here helped me when i was totally newbi ( 45 days ago) .  I just wanna learn more , get more friends, and return the favor 8)

---

### Post by Russty of Oz on 2007-02-14
> **Mba7eth said:**
> No need to thanks dude :D .... A lot of people here helped me when i was totally newbi ( 45 days ago) .  I just wanna learn more , get more friends, and return the favor 8)

You sure learn fast!  I have been using Ubuntu for almost a year now and I still keep getting out of my depth :oops:

---

