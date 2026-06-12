---
title: "ubuntu is unreliable.....SOS"
date: 2008-01-02
forum: General Help
---

### Post by mbailey1 on 2008-01-02
this is the same computer i have had for about 4 months. i tried upgrading to gusty but failed got a gusty cd from a friend and all was well. then bout 3 weeks ago movies stopped playing on the internet but the problem isnt flash because flashl works. i could still watch movies if brought from an outside source, i.e. external hard drive. then today all the sound dissapeared. gone nada zip without any warning what in the world could be wrong. 

this is the last straw. if this cant be fixed without reformating again i will have lost my trust in this OS

---

### Post by kellemes on 2008-01-03
> **mbailey1 said:**
> if this cant be fixed without reformating again i will have lost my trust in this OS


:-({|=
Formatting is a bad bad habit you've taken from some "other os".
It's hardly ever needed with GNU/Linux.

Have you got the flash-**plugin** installed?
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by crazybeard on 2008-01-03
Are these the ONLY problems you are having?   What I mean is, it sounds like this is exclusively a multimedia issue (as opposed to a hardware, data corruption, etc., issue).    The sound could easily be due to the sound resources being taken up by some other piece of software running in the background. You could try running, say, rhythmbox from the command line and seeing if it gives you a "resource busy" error (or you just may get a popup).   

Also, check to make sure that your sound  isn't being piped through your earphone jack even though the earphones are unplugged (o.k., so you can't tell if you don't have the ear phones plugged in.  If you plug them in and hear sound and unplug them and all the sound goes away, chances are the OS still thinks they are plugged in).    


Finally, fill us in as to what OS you have and what software you are using to play the movies (Is it actually Flash or just the gnome version of a flash player - I believe Gnash.  Flash normally doesn't get installed unless you force it).


brian

---

### Post by mbailey1 on 2008-01-03
well there are no other words to describe this computer than garbage. now i cant even boot up! the only chance i have is command prompts through recovery mode. i am oblivious as to what is going on. no login window or anything so give me some prompts to try.

---

### Post by AndyCooll on 2008-01-03
```
sudo dpkg-reconfigure xserver-xorg
```

Work your way through the prompts accepting the defaults until you get to the graphics card. Choose VESA for now, it's a bog standard card that works with most things and should at least help you get to a gui. You can then always optimise your graphics card details later.

Then:
```
startx
```

:cool:

---

