---
title: "How do I open a .run file in the Terminal as root?"
date: 2008-05-02
forum: General Help
---

### Post by coldswede on 2008-05-02
The new Nvidia beta drivers ( 173 .08 )use .run format and open in a terminal, but you need to be root for it to work.  It never gives you the chance to use sudo, it just fails. Anyone know how to open these installers?

---

### Post by Monicker on 2008-05-02
sudo sh file.run

---

### Post by Bal_Zac on 2008-05-02
Also chmod +x file.run to make it executable, if it isn't already.

---

### Post by coldswede on 2008-05-02
Thanks. I have tried that however Sh says it "cannot run the file"

---

### Post by BLTicklemonster on 2008-05-02
[unproductive rant]I still say that there needs to be some program in ubuntu that will take .rpm .sh .run and all other file types and allow them to be clicked to be run, asking for passwords when necessary. Normally when this is brought up, the "terminally terminals" come out of the woodwork against it, but honestly, can't you do anything in terminal, so who cares if there's some ui that can do the same thing?[/unproductive rant]

---

### Post by coldswede on 2008-05-02
Thanks Bal_Zac, it was already an executable file.

BL Ticklemonster: Yeah that would be handy sometimes. I have nothing against the Terminal.  Sometimes however, remembering all the possible phrasing of commands can be  ummm "terminal" ...sorry I couldn't resist :)

---

### Post by warp99 on 2008-05-02
If the executable is not in your $PATH then you need to prefix the command with ./ to run in the current directory. 

Example:

```
sudo ./NVIDIA-Linux-x86-169.12.pkg1.run
```
the file also has to be executable so change the permissions first:
```
chmod +x NVIDIA-Linux-x86-169.12.pkg1.run
```

---

### Post by Monicker on 2008-05-02
> **coldswede said:**
> Thanks. I have tried that however Sh says it "cannot run the file"

Interesting, because these are the instructions from the Nvidia site.

```
Type "sh NVIDIA-Linux-x86-169.12-pkg1.run" to install the driver. 
```

I recall doing that when I installed the drivers.  It should work as long as you prefix it with sudo.

---

### Post by sisco311 on 2008-05-02
i.) To install the driver you need build-essential and linux-headers:
```
sudo aptitude update
sudo aptitude install build-essential linux-headers
```ii.) You must stop the X server:
Press Ctrl+Alt+F1 and log in.
stop the x:
```
sudo /etc/init.d/gdm stop
```iii.) Install the driver:
```
sudo sh **path/to/the/driver/drivername.run**
```Example:
```
sudo sh ~/Desktop/NVIDIA-Linux-x86-173.08.pkg1.run
``` Assuming you downloaded the driver in your Desktop and the file name is NVIDIA-Linux-x86-173.08.pkg1.run

iv.) Start the x server
```
sudo /etc/init.d/gdm start
```

---

### Post by coldswede on 2008-05-02
Thanks for all the reply's ... I got it to install seems I was missing the PATH .... Yeah I'm slow sometimes :(

---

### Post by krasisv on 2008-05-15
thanks SISKO is work for me:guitar:

---

