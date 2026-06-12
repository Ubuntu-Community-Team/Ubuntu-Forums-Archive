---
title: "Can't get past tty1 screen"
date: 2013-06-01
forum: General Help
---

### Post by rTekku on 2013-06-01
So I just installed Ubuntu 12.04 using Virtual Box and i'm now stuck on the tty1 screen.

I can log in and it will greet me with a message saying Welcome, but I don't know how to get past that and get to the actual desktop.

---

### Post by ibjsb4 on 2013-06-01
This is the "Ubuntu Live CD" you installed and not the "Server Edition".

---

### Post by rTekku on 2013-06-01
So did I download the wrong file or something?

Because I downloaded the one my professor specified for us (ubuntu-12.04.1-desktop-i386.iso is the filename) and followed the same exact steps.

---

### Post by steeldriver on 2013-06-01
Hello and welcome to the forum

If you installed the desktop iso (not the server version) then the desktop should start automatically - if it doesn't, that usually means there's a problem with graphics drivers - you can try

```
sudo service lightdm start
```

- it probably won't work (else it would have started automatically) but any errors it produces may help diagnose the problem

Did you run the 'Try Ubuntu' option first from the installer to check that everything worked on your hardware?

---

### Post by QIII on 2013-06-01
Hello!

And could you also tell us a little bit about your hardware -- particularly your graphics card?

---

### Post by rTekku on 2013-06-01
I just tried the option to Try Ubuntu and i'm stuck on a black screen.

*edit*

Running a Pentium B950, 4 GB of Ram, Windows 7 64 Bit, Intel HD Graphics

---

### Post by rTekku on 2013-06-02
Had to reinstall it again and i'm back to the tty1 screen.

I ran the command you told me to and I don't see any errors jumping out at me...Just starts and stops a bunch of different things.  The last line says "Stopping Userspace bootsplashstems devicessing daemon".  After awhile the screen goes black and nothing happens.

---

### Post by HiImTye on 2013-06-02
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
try
```
startx
```it will provide you with some useful output. you can also scour```
less /var/log/kern.log
less /var/log/syslog
``` to read through the init stuff

---

### Post by rTekku on 2013-06-02
After I ran the startx command, it produced the same output as the previous command steel gave me.  Eventually the screen went black.

---

### Post by sandyd on 2013-06-02
Try pressing control+alt+f7 - for some reason, Ubuntu doesnt switch to the graphical display automatically sometimes.

---

### Post by rTekku on 2013-06-02
Quick update

I managed to get Ubuntu up and running on my desktop....I ran into the exact same error that i'm having on my laptop and I fixed it using sudo apt-get install nvidia-current to get the necessary drivers for my GPU.  After that, Ubuntu booted up with no issues.  However, since my laptop is using Intel HD Graphics, i'm not exactly sure what to do.

---

