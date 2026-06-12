---
title: "raaaaaaaaah random crashes drive me nuts!!!"
date: 2008-05-08
forum: General Help
---

### Post by eel on 2008-05-08
For the last few days hardy has been crashing like it's going out of fashion. To begin with mostly when i opened a site with a flashplayer, which is sort of a known issue so i didn't let it get to me on any level (hmmmm zennnn) BUT things got a bit more weird and annoying when crashes began to occur 5 out of 7 times (approx) when hitting ctrl+f in firefox and then typing a word. Now i am working on somthing in Open Office Impress and the past hour hardy has crashed five or six time. 

Oh ehm by crash i mean sudden and unwanted restart of X right to the login screen. 

I've also had sound problems, sound slowing down to slowmotion sometimes when watching a video. So the general feeling i have is that my laptop (3 years old) is Not Coping in some way/shape/form. 

Even if noone can say anything useful about the above i am a happy girl now i have decently ranted off all my frustration. Thanks for listening :)

---

### Post by gsiliceo on 2008-05-08
I'd suggest you switch the sound to alsa, as pulse is inestable right now, and check your hard disk for surface errors, i'm not sure how to do this in ubuntu.

---

### Post by eel on 2008-05-09
switched everything to alsa but to no avail...
what i find weird is that its not a complete crash, it's just x rebooting.

---

### Post by eel on 2008-05-09
now also when i'm in the middle of filezilla connecting to a website
its no loose power cable because it happens only with some specefic events. 
SOMEBODY????

---

### Post by vdawg on 2008-05-09
Hmm this may be a long shot, but did you try monitoring your system to see if you are using up too many resources like ram etc?

Maybe you are running out of ram and then gdm just crashes.

Open up terminal and then type in
top
to see your system usage

Or you can use the system resource monitor, but that itself takes up some juice lol.

---

### Post by eel on 2008-05-10
ehm i don't really know where to look for in terms of 'using much ram'. Is that virtual memory, resident memory, writable memory, shared memory, x server memory or % cpu? As far as i can see nothing is using extreme amounts of cpu apart from system monitor, firefox and pulseaudio. Which i end processed (pulseaudio that is) which might be a solution because my boyfriends computer slowed down terribly untill i on a hunch ended pulseaudio. Which i then completely forgot about but now i remembered again. Sometimes being hungover gives me brilliant insights (:


Nope... didn't do the job. Tried connnecting to my site w/ filezilla and x restarted. AGAIN! So i am open for wild five cents and long long long shots

---

### Post by Gina on 2008-05-10
I have had X reboot a couple of times myself but it's pretty rare and not reproducible. I do get total system crashes (nothing works but switching off) quite often though mainly when playing music or video.  Others find the same and there are bug reports about it.  I wondered about PulseAudio too.

---

### Post by signifer123 on 2008-05-10
Do you know what video driver you are using?

Press Alt+F2
type in ```
gksu /usr/bin/displayconfig-gtk
``` and hit run
Enter your password
Click the tab labeled Graphics Card
The driver name will be next to Driver:

Examples:
fglrx
ati
nv
vesa
vga
radeon


And video card?
If you don't know it a computer ID would probably work as well.
Example being "Dell XPS 420"

---

### Post by eel on 2008-05-10
it says 

Graphics Card (Ati Radeon)
Driver: None

don't know about my video card but my laptop is a Toshiba Satellite L100-130
thanks for reacting!

---

### Post by signifer123 on 2008-05-11
You have the same chipset as my laptop. So you should probably switch to fglrx(which isn't opensource in case you want an all opensource desktop, use ati driver for this)

In that same dialog as before (gksu /usr/bin/displayconfig-gtk), graphics card tab.

Click on the button next to Driver:

Then the box next to "Choose driver by name:", click it and select fglrx.(Or ati if you want the opensource one)

then OK, and OK. From here it is recommended you reboot, but Ctrl + Alt + Backspace probably does what Xserver wants, it might just bug you till next restart.

[COLOR="SlateGray"]If you don't have fglrx, go into synaptic(or whatever package installer you use) and install xorg-driver-fglrx.[/COLOR]


Anyone else looking to help here are the specs:
[http://www.kieskeurig.nl/product/2D4F89D23E2A34CEC125715D0037C452.htm](http://www.kieskeurig.nl/product/2D4F89D23E2A34CEC125715D0037C452.htm)

---

### Post by eldragon on 2008-05-11
have you checked /var/log/Xorg.0.log ?

it usually has useful info on what might have gone wrong. 
have you tried a different DE? say KDE?

---

### Post by eel on 2008-05-11
bedankt
tried switching to fglrx, didn't work though...
i get the feeling that x restarts everytime i do something that is 'impossible' like when i use ctrl-f to find a word in a website and the word doesnt exist, or when i make a typo in terminal, or when i try to connect to my site with filezilla but type the wrong password. Maybe my laptop is just trying to tell me to to quit messing around...

---

### Post by eel on 2008-05-11
how do i check my var log?
what i also find strange is that i never get a crash report.
and a different DE, why?

---

### Post by signifer123 on 2008-05-11
Okay well fglrx was just a hunch because that fixed my laptops display problems.

> **eel said:**
> how do i check my var log?
what i also find strange is that i never get a crash report.
and a different DE, why?

You can see the log with:
hit Alt + F2 then run
```
gksu gedit /var/log/Xorg.0.log
```

It wouldn't be able to display the crash report, since the thing needed to view the crash report is crashed.

As for the DE
It could be Gnome, or at least GTK acting screwy. So if you try KDE, it's based off QT rather than GTK. Then we know it's that not Xorg.

From what you seem to saying I would think it would be some wierd sound problem, seeing as this only happens with errors that typically make beeps.

---

### Post by eel on 2008-05-12
My var/log is completely empty.
How do i try kde, will there be dataloss?
Very wise thing about the beeps!

---

### Post by eldragon on 2008-05-12
if everytime you make a mistake, it reboots, everything points out to the pulse audio sound server.

im not experienced enough to troubleshoot your problem, see if muting the entire system fixes it.


or go to system / preferences / sound 
then navigate to the system beep and disable it.

then go to a terminal and make a mistake :D

if this solves your problem, someone with more experience might help you fix it, or as a last resort, revert to alsa for the time being. you could submit a bug report too :D

---

### Post by eel on 2008-05-12
i tried your (eldragon) solution but it didn't work. It did have some effects though, when i tried to login after making a mistak in terminal nautilus didn't work when i logged in. I am sort of tempted to uninstall pulseaudio since alsa seems to be working better, but i don't know in how far this will eff up my hole installation... anybody?

---

### Post by eel on 2008-05-22
BUMP!!!!
really. 
still the same problem and i have no idea what to do, tried everything mentioned here but to no avail...

---

