---
title: "[SOLVED] console problem in gutsy ... i need help"
date: 2008-03-02
forum: General Help
---

### Post by bigbrovar on 2008-03-02
it all started today while i was try to drop in to console to install a nvidia driver but when i do ctrl + alt + f6 my screen goes black and all i can see is a blinking cursor ... strangely  if i reboot i can log into console as root from grub.. i just cant seem to do it from a normal x session... it started today cus i remembered being able to enter console last night ... i tried thinking back what i did .. but all i can remember was watching a movie on vlc ..could that be the problem ...

---

### Post by bigbrovar on 2008-03-02
Please if any body can help me here i would really appreciate .. this is the only problem i have with my system .. and its a very annoying one for that ... its seriously limit the power of my ubuntu when i cant easily drop to console.. the last time it happened i had to format and reinstall my system to fix it .. i dont want to have to do that again ... please suggestions anybody

---

### Post by bigbrovar on 2008-03-02
i dont have a home internet connection so i have to travel a long way to a place where i can post this .. i was hoping that it would be worth it after all the money i have spent and i would go home with a solution to my problem .... i have done all the search i can but i cant seem to have a definite solution .. please some one any one make my day

---

### Post by bigbrovar on 2008-03-02
oh i for got here are my specs 
sony vaio fz21e
Nvidia geforce 8400GT
2GB RAM
Intel core 2 duo 2.0 ghz
gutsy 32bit dual boot with vista 

attached is a copy of my xorg
hope it helps

---

### Post by koenn on 2008-03-02
it's a bit optimistic to expect a working sollution within 15 minutes when asking for help on a volunteer forum on a sunday afternoon and people have no physical access to your computer to quickly check a few things or experiment a bit ...

anyway, this sounds as if the consoles dont run the /bin/login program. 
normally, this is triggered from /etc/inittab : the respawn:/sbin/getty  create the consoly ("TTY"), and call /bin/login to let you login. 

first check if inttab sets up the tty's : 
```
cat /etc/inittab
``` should show something like
1:2345:respawn:/sbin/getty 38400 tty1
2:23:respawn:/sbin/getty 38400 tty2
3:23:respawn:/sbin/getty 38400 tty3
4:23:respawn:/sbin/getty 38400 tty4
5:23:respawn:/sbin/getty 38400 tty5
6:23:respawn:/sbin/getty 38400 tty6

If not, that may be your problem, or Gutsy / upstart doesn't really use inttab anymore - that, I don't know

also check that /bin/login exists, and what the permissions look like.
```
x:~$ ls -l /bin/login
-rwxr-xr-x 1 root root 31208 2006-07-11 14:51 /bin/login
```

lastly, you should find tty's ("consoles") behind F1, F2, F3, F4, F5 and F6
from your post, it looks as if you only tried ctrl+alt+F6. Try the other ones as well. 

bonus : 
it has happend to me that the ctrl and alt to the left of my keyboard didn't work.
Try the ones on the right, either Ctrl+ Alt Gr,  or just Alt Gr as this sometimes works identical to Ctrl+Alt

---

### Post by bigbrovar on 2008-03-02
thanka man .. am soo sorry for sounding kind of pushing .. its just that am a bit desperate cus once i go home i wont have access till the next 5 days when i come to the internet center .. and i didnt want to carry this problem for 5 days ...

i tried the first suggestion  ***cat /etc/inittab***
and what i got was  ***No such file or directory***

and yes login exist in bin but the permission is root ..
i dont think it a problem with my keyboard like it said earlier i dont get the problem if i log in into root from grub ..... but in normal sesstion what i get is a black screen with a blinking cursor although am about to resume x with ctrl alt f7

---

### Post by koenn on 2008-03-02
like I said, I don't know if ubuntu still uses inittab since it introduced upstart (maybe someone else reading this can check .)
but I suppose it doesn't hurt to try.

Here's the contents of my inittab
copy it to a text file, make that file /etc/inittab, set the permissions
```
chmod 644 /etc/inittab
```

then, try again.
if it doesn't help, you might want to remove (or rename) it so it doesn't interfere with anything else

```

# /etc/inittab: init(8) configuration.
# $Id: inittab,v 1.91 2002/01/25 13:35:21 miquels Exp $

# The default runlevel.
id:2:initdefault:

# Boot-time system configuration/initialization script.
# This is run first except when booting in emergency (-b) mode.
si::sysinit:/etc/init.d/rcS

# What to do in single-user mode.
~~:S:wait:/sbin/sulogin

# /etc/init.d executes the S and K scripts upon change
# of runlevel.
# Runlevel 6 is reboot.

l0:0:wait:/etc/init.d/rc 0
l1:1:wait:/etc/init.d/rc 1
l2:2:wait:/etc/init.d/rc 2
l3:3:wait:/etc/init.d/rc 3
l4:4:wait:/etc/init.d/rc 4
l5:5:wait:/etc/init.d/rc 5
l6:6:wait:/etc/init.d/rc 6
# Normally not reached, but fallthrough in case of emergency.
z6:6:respawn:/sbin/sulogin

# What to do when CTRL-ALT-DEL is pressed.
ca:12345:ctrlaltdel:/sbin/shutdown -t1 -a -h now

# /sbin/getty invocations for the runlevels.
#
# The "id" field MUST be the same as the last
# characters of the device (after "tty").
#
# Format:
#  <id>:<runlevels>:<action>:<process>
#
# Note that on most Debian systems tty7 is used by the X Window System,
# so if you want to add more getty's go ahead but skip tty7 if you run X.
#
1:2345:respawn:/sbin/getty 38400 tty1
2:23:respawn:/sbin/getty 38400 tty2
3:23:respawn:/sbin/getty 38400 tty3
4:23:respawn:/sbin/getty 38400 tty4
5:23:respawn:/sbin/getty 38400 tty5
6:23:respawn:/sbin/getty 38400 tty6


```

---

### Post by bigbrovar on 2008-03-02
ok am about to do what u suggested .. although i most say am still quite a noob in ubuntu so .. but i try to the best of my understanding thinks very much for ur help ..

---

### Post by bigbrovar on 2008-03-02
But wait a minute i think my prolem has something to do with changing  vga=xxx to the grub conf from my search most pple who have done that reported the same problem... and i remember editing grub some minutes b4 i noticed the problem ..... hmmm

---

### Post by koenn on 2008-03-02
> **bigbrovar said:**
> But wait a minute i think my prolem has something to do with changing  vga=xxx to the grub conf from my search most pple who have done that reported the same problem... and i remember editing grub some minutes b4 i noticed the problem ..... hmmm

then you just have to change it back, no ?

why do you need those consoles anyway ? you can do command stuff in an X terminal too, can't you ?

---

### Post by bigbrovar on 2008-03-03
> **koenn said:**
> then you just have to change it back, no ?

why do you need those consoles anyway ? you can do command stuff in an X terminal too, can't you ?
yeah that was what i did i had to change the vga =xxx to the default so now i can drop into console using ctrl alt f1 ..... i something need to enter console when i want to install a nvidia driver which i can do in xterminal cus i would have to stop gdm... anyway problem solved although i now have an ugly big usplash ..but hell u can have it all 

thanks koenn for being there ... i apprecaite

---

### Post by koenn on 2008-03-03
you're welcome

---

