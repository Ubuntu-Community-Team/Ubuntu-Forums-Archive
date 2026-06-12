---
title: "Edgy problems - keeps crashing/logging me out [Somewhat urgent]"
date: 2006-12-18
forum: General Help
---

### Post by Daneeka on 2006-12-18
Hello.

I have to keep this brief because any second Edgy might log me out.

When I turn on the computer, Edgy will only sometimes let me log on, other times, I will type my user and pass and it will accept, but just stay on the brown screen, and not do anything.

If I do login successfully, it might work for a minute, but then the monitor will 'click' and when the screen returns, I will be logged out. After that I can rarely login for a while.

Sometimes the panels up the top and bottom dissapear, rendering my session virtually useless.

And other times still the whole computer will just freeze in it's tracks.

is this a common problem?
And does anyone know a way around this?

It's getting drastic, the computer is virtually unuseable as is.

In a second I will post some of the error messages I have been getting.

Thank you SO much for any and all help. :)

THANKS!!

---

### Post by aysiu on 2006-12-18
I can assure you this isn't a common problem, but it certainly is distressing.

It sounds as if it could be multiple things. One way to help isolate the source of the problem is to create a new test user and see if that test user has the same problems.

Boot into recovery mode (do you know how to do this?) and type these commands: ```
adduser test
reboot
``` Then boot into regular mode and try to log in as the test user. If the test user experiences the same problems, then you've got a systemwide problem. If not, there's something wrong with your user's home directory.

---

### Post by Daneeka on 2006-12-18
Thanks! I will try that.

I'll report back in a jiffy.

(I've shifted a laptop in here for the time being so I can read this and report back hassle free.)

---

### Post by aysiu on 2006-12-18
Of course, if we figure out whether it's systemwide or user-specific, that still doesn't solve the problem, but it may get us a little closer...

---

### Post by Daneeka on 2006-12-18
User 'test' doesnt' login either... :(

Hmm...

Not sure if this is useful information, but when I first installed Edgy, it logged me out (with the monitor 'click') occasionally, but I was always able to log back in, now (about a week later) it is far more frequent, and I can barely login in the first place.

---

### Post by aysiu on 2006-12-18
Hm.

I'm not sure what the problem could be.

I'm not really good at troubleshooting this sort of thing. Worst case scenario, you could **[create a separate home partition](http://www.psychocats.net/ubuntu/separatehome)** and then reinstall...

Maybe someone else has a better solution.

---

### Post by ayoli on 2006-12-18
the monitor clik make me think about an xorg config problem.
look for errors in your /var/log/Xorg.0.log (all lines starting with (EE))

offtopic: aysiu: i often drive new users to your guides (which are good) and just discovered your essays (in particular the linux desktop myth). very good litterature, congratulations.

---

### Post by Daneeka on 2006-12-18
That sounds promising, Ayoli... I seem to remember an error message saying something along those lines... perhaps.

However, I am not quite sure how to check for those errors... any hints?

Thanks very much.

When I am able to login again I will post some of the error messages I have been getting.

---

### Post by ayoli on 2006-12-18
can you log in console mode ? if yes type in:
```
cat /var/log/Xorg.0.log |less
```
(less will allow you to scroll with page up / page down, use "q" to quit)
and tell us about errors you see as precisely as possible

---

### Post by Daneeka on 2006-12-18
Okay! I got something...

```
(EE) Failed to initialize GLX extension (compatible NVIDIA X driver not found) error opening security policy file /usr/lib/xserver/SecurityPolicy
```

I'll keep going through and report back on any others... THANKS!

---

### Post by Daneeka on 2006-12-18
And one last one:


> (EE) xf86OpenSerial: cannot open device /dev/wacom - no such file or directory.
Error opening /dev/wacom:Success

This is written about eight times, interspersed with:

> (**) Option "Device" "/dev/wacom"

---

### Post by Daneeka on 2006-12-18
And that is all of it. :)

I hope that narrows it down a little... :/

Thanks a bazillion, you guys.

---

### Post by ayoli on 2006-12-18
okay
edit your xorg.conf:
```
sudo nano /etc/X11/xorg.conf
```
1. comment lines about wacom by adding a **#** at the begining of lines
2. find line *Driver* in Section "Device" try to change it to (i assume you have an nvidia graphics card/chipset)
```
Driver    "nv"
```
or if still doesnt not work
try:
```
Driver    "vesa"
```
note: if you have several Sections "Devices" edit the one corresponding to the one selected in the Section "Screen" (look at line DEvice in Section "Screen")
then reload X/GDM:
```
sudo /etc/init.d/gdm start
```
(or reboot if you were in recovery mode)

---

### Post by Daneeka on 2006-12-18
That file just seems to be empty...?

When I type sudo nano /etc/X11/xorg.conf I get the modification screen, but no text to modify... I'm not sure what I've done wrong here...

---

### Post by compwiz18 on 2006-12-18
That command looks right (and works on my computer)...make sure when you type it in you get proper case too.

---

### Post by ayoli on 2006-12-18
weird, what's the outpput of :
```
ls /etc/X11/
```
here's another thing you could try:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
that should reconfigure xorg and generate /etc/X11/xorg.conf

---

### Post by Daneeka on 2006-12-18
> **ayoli said:**
> okay
edit your xorg.conf:
```
sudo nano /etc/X11/xorg.conf
```
1. comment lines about wacom by adding a **#** at the begining of lines


I got the xorg.conf to work finally (yay! I wasn't capitalising the X11 ](*,) ), but I am a bit confused about where to put the #'s... I just put them as far left as I could, but the GDM thing couldn't load then.

Thanks for all your help!

I was trying to install a NVIDIA driver the other day, but I couldn't figure out that GhostScript stuff. PS. That was after all this started messing up.

---

### Post by Daneeka on 2006-12-18
> **ayoli said:**
> 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
that should reconfigure xorg and generate /etc/X11/xorg.conf

Trying that one now. :)

---

### Post by compwiz18 on 2006-12-18
> **Daneeka said:**
> Trying that one now. :)
If you still have trouble, feel free to post your /etc/X11/xorg.conf file on this board as an attachment, or using ```
 
``` tags, and I will help you edit it.

---

### Post by Daneeka on 2006-12-19
Thanks, I'm having a lot of trouble.

I'll post it when the Ubuntu computer lets me log on again. :)

Thanks!!

---

### Post by ayoli on 2006-12-19
> **Daneeka said:**
> Thanks, I'm having a lot of trouble.

I'll post it when the Ubuntu computer lets me log on again. :)

Thanks!!

you can try  to boot on live cd, then mount the partition where ubuntu is installed and search for etc/X11/xorg.conf in this partition, then post the xorg.conf here

---

