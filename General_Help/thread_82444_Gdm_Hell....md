---
title: "Gdm Hell..."
date: 2005-10-26
forum: General Help
---

### Post by cagljevic on 2005-10-26
i'm hoping someone has been in this situation before and knows the answer...

while logged into gnome, i typed in a terminal window 'sudo killall gdm' and after i typed that the entire screen went black, not giving me the typical console and the entire computer was locked up, no ctrl-alt-fanything would get me another console.  even after restart, i am completely locked out unless i choose safe mode from grub which i can get a console.

can anyone out there tell me what happened to gdm, how i clear up this mess?  as i said, i'm still able to get a console in safe mode, so i can edit, delete files to fix this mess.

any help would be greatly appreciated.

-mark

---

### Post by Kyral on 2005-10-26
Ouch....that is NOT the way to shutdown gdm ( sudo /etc/init.d/gdm stop )

Maybe a "sudo dpkg-reconfigure gdm" will work

---

### Post by sanjose on 2005-10-26
or type this on your console

[INDENT]***sudo update-rc.d /etc/init.d/gdm defaults***
[/INDENT]

---

### Post by Breezy Badger on 2005-10-26
Man I had the exact same problem, my mistake I will never do that again...in fact I still have not been able to fix it.  Let me try these solutions and I will let you all know if they work

Badger

---

### Post by Kyral on 2005-10-26
Nice avatar :P

---

### Post by Breezy Badger on 2005-10-26
haha thanks man

---

### Post by cagljevic on 2005-10-26
thanks for both the quick replies, its awesome that there are people here that are on point to help.

both suggestions resulted in the same thing, black flickering screen then solid lockup.

i also tried doing the apt-get remove gdm, followed by apt-get install gdm, given me the same solid lockup after the nice ubuntu graphical loader screen.

not sure if it makes a difference, but i have the latest nvidia 1.0-7676 installed with a nvidia fx 5950 ultra.

-mark

---

### Post by Breezy Badger on 2005-10-26
As the above user has pointed out, both solutions were a no go.  I tried both and got the exact same results.

thanks for the help guys, please someone help me here I do not want to do another install just to fix this

Badger

---

### Post by linuxgrrl on 2005-10-26
no Idea if this is your problem, but I recently had a similar experience after updating Hoary.  Turns out the update had somehow edited my xorg.conf to replace the nvidia driver with the generic nv (!), which did not work on my system.  I had not rebooted in a while after updating, so I  never did find out what package would do such a horrible thing to me :) 

the solution was to boot into safe mode, and edit /etc/X11/xorg.conf to put nvidia back instead of nv.

---

### Post by Breezy Badger on 2005-10-26
ok linuxgirl thanks for the info, I suspect this is not it in this case but let me restart and try, I will get back to you

Badger

---

### Post by Breezy Badger on 2005-10-26
hello again, turns out that is also not the problem

it still says nvidia, thanks for the suggestion tho

BAdger

---

### Post by Breezy Badger on 2005-10-26
Ok eveyone I figured it out, thanks for all the help.  My solutions were actually a combo of some of your hints.

I figured out from some internet searching that it all comes back to the Nvidia drivers, they were the source of the problems.

So from the safe mode promt I reinstalled the Nvidia drivers that I had on my har drive, so kind of a fresh driver install. I then did:

```
sudo /etc/init.d/gdm stop
```

after this use:

```
sudo /etc/init.d/gdm start
```

Now with a restart of the gdm and the drivers reinstalled it was all fixed.

moral of the story, just avoid kill all gdm hahaha

thanks everyone

---

