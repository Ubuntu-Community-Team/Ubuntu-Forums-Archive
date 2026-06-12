---
title: "GDM trouble"
date: 2006-09-18
forum: General Help
---

### Post by PereUbu on 2006-09-18
After kernel-update (.25 -> .26) the GDM login doesn't show up after boot. I get an bluscreen which tells me that X is not configured right (which it is). But somehow, when I login through the console and type startx the XFCE desktop pops up. 

If I set KDM as default instead, I'm able to login to the gnome-desktop again. 

I have tried to boot the .25, .26, .27 kernel but I get the same result.

What can I do to get GDM function again? 


Best regards
PereUbu

---

### Post by croak77 on 2006-09-18
Try running sudo dpkg-reconfigure gdm from a terminal. Pere Ubu = great band. Also try running sudo /etc/init.d/gdm start from your login console. Post any errors.

---

### Post by PereUbu on 2006-09-19
Thanx for advice croak77.

I tried sudo dpkg-reconfigure gdm from a terminal, and chose GDM as default.
Then I rebooted and did sudo /etc/init.d/gdm start from the login console without getting any error message only an OK.

So I guess I have to find out exactly what the before mensioned bluescreen tells me.

I'll be back!

/PereUbu

---

### Post by PereUbu on 2006-09-19
Ok I'm back again

Here's my Xorg.93.log file, xorg.conf file and the bluescreens:
[REMOVED]

/PereUbu

---

### Post by croak77 on 2006-09-19
Have you tried using the Nvidia driver instead of nv? Are you using xgl/compiz?

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by PereUbu on 2006-09-20
Hi croak77!

I reinstallled nvidia-glx and enabled the nvidia driver again and that did the trick.

I really don't understand why this did the trick now, because I have tried exactly the same thing over and over again before. And the funny thing is this problem occurred after a [kernel-update]("http://www.ubuntuforums.org/showthread.php?t=213420") with the nvidia driver enabled.

So when X didn't start I changed to the nv driver, which has done the trick before.

Never mind, it's working again and I'm glad!


Thanks alot for your help croak77!

Best regards
[PereUbu :-)]("http://en.wikipedia.org/wiki/Pere_Ubu_%28band%29")

---

### Post by apelete on 2006-09-20
I have exactly the same problem.
GDM is randomly crashing at boot. Sometimes it just boots fine, but other times it just keeps crashing until I reboot once, twice or even more (today it keeps crashing until my third reboot :confused: ).

I don't understand why is this happening since I didn't change anything in my  setup (no XGL, I have and ATI gpu, no compiz..).
What's going on here since the last two kernel updates ??? :confused:

---

