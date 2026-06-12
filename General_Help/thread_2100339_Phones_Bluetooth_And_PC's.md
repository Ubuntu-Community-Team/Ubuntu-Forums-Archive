---
title: "Phones Bluetooth And PC's"
date: 2013-01-01
forum: General Help
---

### Post by dave r on 2013-01-01
I have a Desktop PC with dual Core Procesor and 4 gigs of Ram running Lubuntu 12,10, I was on Ubuntu for a long time and the bluetooth was a bit iffy on there, but its worse on Lubuntu.
I have a basic Nokia Flip phone
I can send a file to the computer from the phone no problem, normally an image file.
I can't send a file to the phone from the computer
I get a window called Bluetooth File Transfer, then a long delay, then a Connection refused, Error Occurred while Sending file  window, in this case an image file. 
I can't browse the phone, clicking on Browse files on device brings up a Failed to Launch'''' (Errno 13) Permission denied window. 
Any idea's people? Theres a lot on the internet about Lubuntu and bluetooth but I haven't yet found a solution.

---

### Post by dave r on 2013-01-02
I suspect the computer is treating the phone as Root and this is all to do with permissions? if it is how do I change the permissions and get full access to the phone?

---

### Post by dave r on 2013-01-02
Bump

---

### Post by MSPdwalt on 2013-01-02
Check your settings on the phone, you might have to allow it to receive files. What version of Ubuntu are you on?

---

### Post by dave r on 2013-01-02
> **MSPdwalt said:**
> Check your settings on the phone, you might have to allow it to receive files. What version of Ubuntu are you on?

I'm on Lubuntu 12.10, I've been looking at the phone settings and can  find nothing to change, I could receive files before I moved to Lubuntu, I was on ubuntu version 10.04, though it was a bit hit and miss

---

### Post by dave r on 2013-01-03
bump

---

### Post by MSPdwalt on 2013-01-04
Which Bluetooth applet are you using?  This is probably not advisable, but a sure way to test your theory that it's a permissions issue would be to kill the Bluetooth applet and restart it as root.  Also, is your user a member of the Bluetooth group? Mine is, I can send files.  But I'm on Ubuntu 12.04 sending to a GSIII

---

### Post by dave r on 2013-01-04
> **MSPdwalt said:**
> Which Bluetooth applet are you using?  This is probably not advisable, but a sure way to test your theory that it's a permissions issue would be to kill the Bluetooth applet and restart it as root.  Also, is your user a member of the Bluetooth group? Mine is, I can send files.  But I'm on Ubuntu 12.04 sending to a GSIII

Its blueman, how do I check the bluetooth group and add to it if I'm not there? And how do I kill it and restart as root?

---

### Post by MSPdwalt on 2013-01-05
How to install the users and groups manager: [http://ubuntuforums.org/showthread.php?t=1974343](http://ubuntuforums.org/showthread.php?t=1974343)

```
ps aux 
``` will list your running processes and their PIDs and paths

```
kill <pid>
```

```
gksu /path/to/applet/
```

---

### Post by dave r on 2013-01-05
Thanks for that, I'll have a look later, I have the users and groups already installed, though I haven't used the group part of it before.

---

### Post by dave r on 2013-01-05
Adding me to the bluetooth group did nothing. opening Blueman as root produced this error message when I tried to browse the phone

Could not display "obex://[2C D2 E7 DA 02 C3]/".
Error: Message did not receive a reply (timeout by message bus)
Please select another viewer and try again.

I now have local services advanced set at Nautilus, I did have it as the default Lubuntu file manager PCManfm, but now if I change it to that its not recognized.
I've been looking at Gigolo, this recognizes the phone but I haven't worked out how to set up a file manager yet,

---

### Post by Elludium_Q-36 on 2013-01-25
I've been limping along with an OLD desktop, 
with Ubuntu "Lucid Lynx" 10.04 LTS.

I thought to try Lubuntu, and have a 10.04 live CD...

Unfortunately my only tie to the online world,
comes via bluetooth.  Right out of the box,
Lubuntu 10.04 won't get to first base.
No joy with my wireless web connected phone, via:
```
sudo dhclient bnep0
```

In fact, I can't even pair with the USB BT dongle.

maybe it's a missing library, or other package.
Perhaps I could find it in /var/cache/apt/archives, 
but then again, it could be a deeper issue.

I had to give up on Kubuntu, with this old hardware.
Now, after updates, Ubuntu becomes a DINOSAUR,
at times.  It just crawls!

Really, being offline, does me little good,
especially if it's a pain to transfer files to an ONLINE device.
Say I write a letter.  Now what?  I can't bluetooth it to the phone.
What, a USB drive, on SNEAKERNET, to the public library?

How about a modified rigid frame backpack, to haul the desktop,
monitor, keyboard, wifi device, mouse, power cords, etcetera,
to the public library?  That's progress!

Yeah, no solution here, but it looks better than "bump".
Sometimes I post, and it seems it only matters to me...

---

### Post by dave r on 2013-01-25
I've given up on this, I can send pictures to the computer from the phone and thats all, I'm thinking either Lubuntu doesn't do bluetooth, or it will only do bluetooth with the sort of advanced tweaking thats far beyond my capabilities. This is the only fail I've had since I've been on Lubuntu, so far everything else has worked very well.

---

### Post by Elludium_Q-36 on 2013-01-26
Some of the dumbest, of dumb phones (non smart phones),
with ultra slow browsers, etc. do bluetooth, just fine.

Why is it then, that Lubuntu can't get the job done?

Ubuntu 10.04, out of the box, does what I need, 
with bluetooth; albiet a little buggy.

**_L**_ubuntu is made to be lightweight, obviously.
So, along with other lightweight linux distros, 
it probably sacrifices some functionality.

I've burned Puppy linux on a CD and you visibly see,
it uses roughly 1/3 of the disk capacity.
An Ubuntu CD is about full.

That should tell you, 
aside from all the bells and whistles,
plus all the bloatware, 
that maybe some support and compatibility had been left out.

I tried Puppy Linux on an old laptop.
The screen resolution was way too small,
and the mouse/pointer was so uncoordinated,
you didn't know where you were clicking.
The pointer was actually off from where it should have been.
It was diagonally away, by a couple inches, or a few centimeters.
I might as well have been wearing a blindfold.

Really, someone is supposed to come forward, here...

Anyone?  Anyone?

The problem is that, 
someone with the potential answer needs to read this thread.
Either that or we stumble upon the answer elsewhere...

---

### Post by Elludium_Q-36 on 2013-01-26
**_I just installed Lubuntu 10.04 on a P III with 250 MB of ram!!!**_

Maybe you've seen references to how Ubuntu, Kubuntu or Edubuntu, 
"automagically" completes installations, etcetera.
With lightweight *buntu distros, it seems a bit more "hands on".
We need to roll up our sleeves and get "under the hood", a bit.

Besides, sometimes the developers don't really triple check, 
all that "automatic" install script stuff, that's supposed to do things, 
as if by magic. I've had to go looking for programs, after installing them; 
to find the launch command, make a menu entry, and find the icon.  
Then, sometimes the command needs arguments, or run as the super user.

But hey, it all beats Windows!  Try even putting XP on a P3 with 250 MB...

---

