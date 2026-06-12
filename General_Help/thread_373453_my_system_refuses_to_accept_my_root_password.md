---
title: "my system refuses to accept my root password"
date: 2007-03-01
forum: General Help
---

### Post by comodor64 on 2007-03-01
hi there
i am trying to access root with my password
but it says "sorry try again"
this happend while i was trying to install Nvidia driver
you need to go outsode of x etc...but i cant tell
the system to go for another level-
why am i doing wrong here?
thanks

p.s. is there an easier way to unstall the nvidia driver?

---

### Post by taurus on 2007-03-01
What's the output of this command when you type it from a terminal and exactly what command have you tried?

```
id
```

---

### Post by BLIMPO on 2007-03-01
This may be a dumb question, but I also have a similar problem.  Only difference is my problem won't even let me put in a password.  When I am prompted for a password while working in the terminal, it just won't let me type anything in.  Is there something I am just not doing?  I can type anything normally in the terminal, but when I am prompted for a password, I just can't put anything in.

---

### Post by azazel00 on 2007-03-01
If you are doing:

```
sudo sh ./NVIDIA-pkg<etc>
```

it should work.

but if you login as 'root' when it prompts for your username, and then run the script, it will show a warning saying that you are running the installer in an inadequate level.

Regards,
az

---

### Post by Maestro23 on 2007-03-01
> **BLIMPO said:**
> This may be a dumb question, but I also have a similar problem.  Only difference is my problem won't even let me put in a password.  When I am prompted for a password while working in the terminal, it just won't let me type anything in.  Is there something I am just not doing?  I can type anything normally in the terminal, but when I am prompted for a password, I just can't put anything in.

In terminal, when inputing your password, the cursor will not move or give feedback.  This is a security feature.  Just type you password in and hit ENTER.

---

### Post by comodor64 on 2007-03-01
but now i have a bigger problem
i messed up while trying to install the nvidia driver
now when i boot i get only black screen :confused: 
how do i recover using live-cd?

helpp my foolish soul

thanks guys

---

### Post by bodhi.zazen on 2007-03-01
to recover X :

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

To install the nvidia driver :

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Use envy from the above link ;)

---

### Post by comodor64 on 2007-03-01
i tried the last command you gave me
but it says "warning..." i might overwrite somthing.... possibly customised configuration
 and the file path... back up in /etc/x11/xorg.conf...
whats next?

---

### Post by Maestro23 on 2007-03-01
> **comodor64 said:**
> i tried the last command you gave me
but it says "warning..." i might overwrite somthing.... possibly customised configuration
 and the file path... back up in /etc/x11/xorg.conf...
whats next?

Go ahead and continue with the reconfiguration.

---

### Post by bodhi.zazen on 2007-03-01
> **comodor64 said:**
> i tried the last command you gave me
but it says "warning..." i might overwrite somthing.... possibly customised configuration
 and the file path... back up in /etc/x11/xorg.conf...
whats next?

He he he ..

:lolflag:

That "warning" is more informational, but it is unnerving ...

It is just telling you it backed up your old xorg.conf, which is broken, so it does not matter at the moment ...

However you may want to refer to your old xorg.conf if you try to get beryl up and going ...

---

### Post by comodor64 on 2007-03-01
*However you may want to refer to your old xorg.conf if you try to get beryl up and going ..*
ok...who is that friend beryl and how do i pull off this amazing magik?

---

### Post by Maestro23 on 2007-03-01
> **comodor64 said:**
> *However you may want to refer to your old xorg.conf if you try to get beryl up and going ..*
ok...who is that friend beryl and how do i pull off this amazing magik?

[http://www.ubuntuforums.org/showthread.php?t=272104](http://www.ubuntuforums.org/showthread.php?t=272104)

Good luck.

---

### Post by comodor64 on 2007-03-01
o mannn.....
they say beryl is not supported for dapper drake...
guess ill download the 6.10 version-i am tierd of this i gues
thanks a lot for the help and friendship

have a mega week end !!! ultra week end...:guitar:

---

### Post by comodor64 on 2007-03-01
hi again guys
i used aptitude to install manually the navidia pakage
and now i restarted my pc and everything is great again

thanks again for your time

---

