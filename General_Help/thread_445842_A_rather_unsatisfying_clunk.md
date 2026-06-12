---
title: "A rather unsatisfying clunk"
date: 2007-05-16
forum: General Help
---

### Post by cypherzero on 2007-05-16
So I shut down Kubuntu and after a few seconds of routine shutdown display messages my hard drive goes 'clunk' as the power suddenly turns off.

It appears that the computer is shutting down too fast, before the hard disks have chance to stop properly, this never happened with Ubuntu edgy, any ideas of how to stop this would be greatly appreciated!

---

### Post by vtel57 on 2007-05-16
I tend to doubt that the OS is causing this. It's very rare for software to damage hardware. My guess is that your hard drive is getting ready to take a dump on you. BACK-UP! BACK-UP! BACK-UP! While you have the chance.

Luck!

---

### Post by Unicast on 2007-05-16
I get this with a Dell inspiron 1501 with 7.04 installed.

Mine makes a kind of clunk and whirring sound as the dive spins down.

---

### Post by smoker on 2007-05-16
this is a warning of imminent hard drive failure, follow vtel57's advice, backup, and save up for a new drive.

---

### Post by Unicast on 2007-05-17
Absolute rubbish. Sorry but it is. :lolflag:

I've only had ubuntu installed for a couple of days and prior to that I had vista, and had no problems with the hard drive making strange noised on shutdown then. So why now?

---

### Post by cypherzero on 2007-05-25
I don't think this is a hardware problem since XP doesn't have the same problem, then again that takes over 3 minutes to shut down :roll:

(Sorry about bumping an old thread, I forgot I'd already posted this! :oops:)

---

### Post by Znupi on 2007-05-25
Mine makes the clunk and whirl sound all the time on shutdown. I thought it was something normal, lol :|. I think it used to do it on XP, too, can't remember though. Anyway my PC is new (I got it last Christmas, so it's like 5-6 months old) so I don't think my hardware is failing...

Edit: The whole PC is pretty noisy at all times...

---

### Post by Unicast on 2007-05-28
Is there a config file somewhere that can be edited that will allow the HDD to spin down before the machine powers down?

---

### Post by Lucifiel on 2007-05-28
Hmmm... I get this too and wonder if it's safe for the hardware to shut down in such a manner.

---

### Post by insane_alien on 2007-05-28
yeah this is a feisty thing. there was a script in the feisty development section that fixed it but i can't find it  now and i can't remember what i done

---

### Post by Lucifiel on 2007-05-28
Oh dear... lol.

---

### Post by Unicast on 2007-05-28
> **insane_alien said:**
> yeah this is a feisty thing. there was a script in the feisty development section that fixed it but i can't find it  now and i can't remember what i done

Fan-bloody-tastic, found it and you know what, it works as well! 8)

Bug report here: [https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810](https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810)

With the salient information here:
> 

Simply write a file at "/etc/rc0.d/S00hdd-shutdown-workaround" which includes this two lines:

#!/bin/sh
echo 1 > /sys/class/scsi_disk/0\:0\:0\:0/stop_on_shutdown

If you have more than one directory at "/sys/class/scsi_disk/" try to find out which of it is your internal harddisk (e.g. "cat /sys/class/scsi_disk/a:b:c:d/device/model") If you have more than one harddisk add another line for each of them.

Then make it executable ("chmod +x filename")
At the next shutdown it should park the hd heads.

What I did, for the less technically minded:

```
gksudo nautilus
``` - opens nautilus in gnome** environment with root privileges - so be careful kids! ;)

**or for KDE enviro```
kdesu konqueror
``` or for Xubuntu.```
gksudo thunar
```

Navigate to /etc/rc0.d

Right-click - Create new document - right click on new doc and rename to **S00hdd-shutdown-workaround**

Right-click on the renamed doc and select "open with text editor."

Copy and paste the following into the empty file and save.
```
#!/bin/sh
echo 1 > /sys/class/scsi_disk/0\:0\:0\:0/stop_on_shutdown
```

In terminal change to the etc/rc0.d directory and make the new file executable:

```
sudo chmod +x S00hdd-shutdown-workaround
```

and you're done. :D

Next time you shutdown there will be no nasty clunk / whirr.

---

### Post by Lucifiel on 2007-05-29
Thanks, Unicast, but that might be too late.

Though perhaps the cause could be another factor, I wonder if this could be related to my newly RMAed hdd developing tons of errors in different values. :/

---

### Post by Scruffynerf on 2007-05-29
I just read this with something akin to horror.

Canonical - 1992 called, they want their hard drive park routines back.

Seriously, WTF is going on when brand new OS's operate in such a manner that *WILL* cause hardware failure?? ](*,) 

We are all supposed to be moving forward people, not backwards.

---

### Post by insane_alien on 2007-05-29
thanks unicast. i honestly couldn't find that. i was surprised when it was in the final version. i didn't think much of it in the development stages because things tend to be crappy during those times.

---

### Post by Lucifiel on 2007-05-29
Okay, well, how about external hard disks? I think I'm going to get an external casing + internal hard disk and transfer all my o/ses to it.

---

### Post by insane_alien on 2007-05-29
my external drive has a battery and control board for automatically parking it when you flick the power so i don't know how it would work with a normal casing.

---

### Post by Swab on 2007-05-29
> **Unicast said:**
> Absolute rubbish. Sorry but it is. :lolflag:

I've only had ubuntu installed for a couple of days and prior to that I had vista, and had no problems with the hard drive making strange noised on shutdown then. So why now?

You might be right... but I hear this all the time from users when something brakes.  They'll say "well it worked fine yesterday!"  I always think.. yup that's the usual order with a hardware failure, working then not working :)

---

### Post by Znupi on 2007-05-30
Umm... it still makes that sound for me. Windows makes it, too.
```

$ ls -l /etc/rc0.d | grep S00hdd
-rwxr-xr-x 1 root root  68 2007-05-28 19:29 S00hdd-shutdown-workaround
$ cat /etc/rc0.d/S00hdd-shutdown-workaround 
#!/bin/sh
echo 1 > /sys/class/scsi_disk/0\:0\:0\:0/stop_on_shutdown

```
Is this right?

---

### Post by clem-vangelis on 2007-05-30
just add this line :
echo 1 > /sys/class/scsi_disk/0\:0\:0\:0/stop_on_shutdown
to /etc/rc.local

but if it do the same noise under noise it's more probably a hardware problem :/

---

### Post by Znupi on 2007-05-30
> **clem-vangelis said:**
> to /etc/rc.local
Isn't that file executed on login? :|

---

