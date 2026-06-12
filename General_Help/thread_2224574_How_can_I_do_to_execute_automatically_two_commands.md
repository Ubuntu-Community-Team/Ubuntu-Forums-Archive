---
title: "How can I do to execute automatically two commands during/after system boot?"
date: 2014-05-16
forum: General Help
---

### Post by Luis_Estevez on 2014-05-16
Hello, I speak Spanish, so my English is not so good. I'm sorry.
Recently, I've installed Lubuntu 10.04 on my old PC, and this computer has an ISA sound card (Sound Blaster AWE 64). I've followed the steps included in this tutorial:

[http://www.linuxjournal.com/article/3269?page=0,0](http://www.linuxjournal.com/article/3269?page=0,0)

and finally my sound card is working (believe me, it wasn't a simple work).
Now, the only problem that I have is that I must type these two commands everytime I boot the computer:

sudo isapnp /etc/isapnp.conf
sudo modprobe snd-sbawe

If I don't type these commands, the sound card doesn't work.
The question is:
How can I do to execute automatically these commands after/during system boot?
I've tried to include the commands inside /etc/rc.local file, but it doesn't work.
I'll thank any kind of help.

---

### Post by Luis_Estevez on 2014-05-16
Hello, I speak Spanish, so my English is not so good. I'm sorry.
Recently, I've installed Lubuntu 10.04 on my old PC, and this computer has an ISA sound card (Sound Blaster AWE 64). I've followed the steps included in this tutorial:

[http://www.linuxjournal.com/article/3269?page=0,0](http://www.linuxjournal.com/article/3269?page=0,0)

and finally my sound card is working (believe me, it wasn't a simple work).
Now, the only problem that I have is that I must type these two commands everytime I boot the computer:

sudo isapnp /etc/isapnp.conf
sudo modprobe snd-sbawe

If I don't type these commands, the sound card doesn't work.
The question is:
How can I do to execute automatically these commands after/during system boot?
I've tried to include the commands inside /etc/rc.local file, but it doesn't work.
I'll thank any kind of help.

---

### Post by tragicallyhip on 2014-05-16
Try this Task: Use Text based GUI Runlevel configuration tool to add or remove services

rcconf is Debian runlevel configuration tool. Rcconf allows you to control which services are started when the system boots up or reboots. It displays a menu of all the services which could be started at boot. The ones that are configured to do so are marked and you can toggle individual services on and off. If rcconf is not installed use apt-get command:
# apt-get install rcconf
OR
$ sudo apt-get install rcconf
Now run rcconf and just follow on screen instructions:
# rcconf
Good luck
trag

---

### Post by coldcritter64 on 2014-05-16
> **Luis_Estevez said:**
> isapnp /etc/isapnp.conf
modprobe snd-sbawe

Put those 2 commands without sudo into the file /etc/rc.local; /etc/rc.local is run as root every boot, you launch them from a root file with this. Place them before the "exit 0" line, this line exits the file at startup anything after it is ignored.

To edit the file,
```
gksu gedit /etc/rc.local
```

Make your file look like below,

> ```
!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

isapnp /etc/isapnp.conf;
modprobe snd-sbawe;

exit 0

```

> 
I've tried to include the commands inside /etc/rc.local file, **but it doesn't work.**
What went wrong ? Did the boot hang like the rc.local file didn't complete ? The commands may need to be backgrounded if so, can be adjusted by placing an "&" symbol at the end of the code line sometimes. Did you have the commands in before the "exit 0" line as mentioned above ?

**Edit**: I should point out I'm not actually familiar with that hardware etc, I'm wondering if the order you are running them in is right or not. Whether or not the modprobe should go first ? Then any "isapnp" command (but I'm really not sure if it matters).

---

### Post by steeldriver on 2014-05-16
***I have merged your threads - please don't start multiple threads for the same question***

You may need to give the full path to the isapnp command (whatever it is...) and it wouldn't hurt to do the same for modprobe (usually /sbin/modprobe - but check using 'which modprobe').

---

### Post by mörgæs on 2014-05-17
Lubuntu 10.04 is obsolete. Better to begin with a fresh install of 14.04.

---

### Post by Luis_Estevez on 2014-05-17
> **coldcritter64 said:**
> Put those 2 commands without sudo into the file /etc/rc.local; /etc/rc.local is run as root every boot, you launch them from a root file with this. Place them before the "exit 0" line, this line exits the file at startup anything after it is ignored.

To edit the file,
```
gksu gedit /etc/rc.local
```

Make your file look like below,




What went wrong ? Did the boot hang like the rc.local file didn't complete ? The commands may need to be backgrounded if so, can be adjusted by placing an "&" symbol at the end of the code line sometimes. Did you have the commands in before the "exit 0" line as mentioned above ?

**Edit**: I should point out I'm not actually familiar with that hardware etc, I'm wondering if the order you are running them in is right or not. Whether or not the modprobe should go first ? Then any "isapnp" command (but I'm really not sure if it matters).

Thank you very much. I've tried all the alternatives that you suggested me, but didn't work.  The system doesn't hang, simply the boot process finish, but those commands apparently are not executed. The order of the commands is correct, because if I run them when the system is ready (after boot), they work correctly.

---

### Post by Luis_Estevez on 2014-05-17
> **mörgæs said:**
> Lubuntu 10.04 is obsolete. Better to begin with a fresh install of 14.04.

Thank you very much. Yes, I know. But 10.04 is the last version that is possible to install on this old machine, because the processor doesn't support CMOV and PAE.

---

### Post by spynappels on 2014-05-17
For the modprobe one, edit /etc/modules and add snd-sbawe
```
sudo nano /etc/modules
```
so it looks like this (you may have other modules in yours as well, just make sure the snd-sbawe one is there too):
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
# Parameters can be specified after the module name.

lp
rtc
snd-sbawe
```

---

### Post by Luis_Estevez on 2014-05-17
> **spynappels said:**
> For the modprobe one, edit /etc/modules and add snd-sbawe
```
sudo nano /etc/modules
```
so it looks like this (you may have other modules in yours as well, just make sure the snd-sbawe one is there too):
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
# Parameters can be specified after the module name.

lp
rtc
snd-sbawe
```

Yes, Yes, Yes Sir !!! Thank you very much!!! It Works perfectly !!! Thank you very much for your time in helping me. Greetings from Argentina. :)

---

