---
title: "Cannot open files with GNOME"
date: 2008-04-23
forum: General Help
---

### Post by thedudething on 2008-04-23
Everytime I use a GNOME program such as GIMP, Totem or Rhythmbox, if I try to Open something, it just crashes.

How do I fix this?

---

### Post by ryanhaigh on 2008-04-23
You are going to need to provide more information than what you have. What do you mean it crashes, what crashes, the application, the desktop, the system? Do you mention gnome applications because you are using something other than gnome usually?

---

### Post by thedudething on 2008-04-23
If I try to open a file with GNOME programs (Totem, Rhythmbox, GIMP), the program just closes itself. Also if I try to save a file on GIMP it closes itself. Do you know what's causing this?

---

### Post by forrestcupp on 2008-04-23
Try installing the restricted extras.  Open a terminal and type
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by thedudething on 2008-04-23
Still the same...
Any other suggestions?

---

### Post by thedudething on 2008-04-23
OK I just realized that I'm having the same problem with OpenOffice, I can't save or open files without it closing itself

---

### Post by rune0077 on 2008-04-23
Could you try and open the original program through the terminal. For example:

```
totem
```

This may produce some kind of error-output when the program crashes. If it does, try posting it here.

---

### Post by thedudething on 2008-04-23
administrator@administrator-laptop:~$ gimp

(script-fu:14916): LibGimpBase-WARNING **: script-fu: gimp_wire_read(): error
Segmentation fault (core dumped)

administrator@administrator-laptop:~$ rhythmbox
Segmentation fault (core dumped)

Segmentation fault (core dumped) seems to be the thing that comes up

---

### Post by chrisccoulson on 2008-04-23
Do you have any crash reports in /var/crash? If so, double clicking on the relevant ones will open a bug report on Launchpad with all the relevant information about the crash.

However, it seems strange that you are experiencing crashes of this frequency. Is this a fresh install or one that you have played around with? Is your hardware okay? (Please try running memtest).

---

### Post by rune0077 on 2008-04-23
Well that wasn't very useful. If it happens for all your programs there must be something really wrong. It may have been a flaw in the installation CD (in which case you will need to get another and reinstall). I would first suggest trying to reinstall all your libx11 files (you can do that through synaptic).

Sorry, not sure what else could be causing this.

---

### Post by thedudething on 2008-04-23
how do you run the memtest?

---

### Post by chrisccoulson on 2008-04-23
Should be an option from the GRUB menu (press ESC at the GRUB prompt before the Ubuntu splash loads).

If not, I think you can run it from the live CD

---

### Post by thedudething on 2008-04-23
I checked the error reports, It just tells me to upgrade alot of packages. I did so and it's still the same problem :/

---

### Post by thedudething on 2008-04-24
It used to work fine, it only started doing this recently in the past 2 weeks

---

### Post by thedudething on 2008-04-24
Okay I have realized that the problem is not just GNOME, it seems to happen to every program that opens the file manager to save or open a file.

---

### Post by chrisccoulson on 2008-04-24
> **thedudething said:**
> I checked the error reports, It just tells me to upgrade alot of packages. I did so and it's still the same problem :/

Once you've upgraded all the packages, try and re-submit a new crash file. Should work now.

I think you have a pretty broken system though, as I've never seen this before. Can you open files from the live CD?

---

### Post by thedudething on 2008-04-24
I installed with Wubi, I didn't use the live CD.

I was able to get Totem to open a file using sudo totem in the terminal, but I want to know how to do that without using terminal.

Also I get segmentation fault whenever I try to sign in to my email.

---

### Post by chrisccoulson on 2008-04-24
I would seriously consider a re-install. This behaviour is not normal

---

### Post by Tatty on 2008-04-24
Segmentation faults are often caused by faulty RAM.  There are other causes, but its most likely to be hardware failure, have a read of this link...

[http://aplawrence.com/Unixart/segmentation_fault.html](http://aplawrence.com/Unixart/segmentation_fault.html)

It could just be a hard disk corruption though, re-installing might help.  It may be worth checking whether the same thing happens with a live CD.

---

### Post by kamstrup on 2008-04-24
I am having the exact same problem. When ever Gnome apps try to read or write data they just hang. Pretty hard to debug because there are no errors printed.

This problem started after I dist-upgraded today. *gulp* this happens on the release day...

UPDATE: After waiting ~5 min (ie. no reboot) the symptoms disappeared. Strange - I have a nagging feeling that it is Tracker somehow hogging the drive...

---

### Post by Hackbert's Celine on 2009-03-29
I got the same Problem, all gnome apps with this behavior. When I use Ark (a KDE App), i can open and save. And as root its no Problem with gnome apps, too. So i tried to make a new user - all fine there ... But i dont want to do all the settings and things again, so if anybody could help it would be very nice!

For Example here the breakdown of gimp: 
gimp

(script-fu:8326): LibGimpBase-WARNING **: script-fu: gimp_wire_read(): error
Segmentation fault

---

