---
title: "Lost tool bars in Xubuntu"
date: 2006-10-30
forum: General Help
---

### Post by Ulysses on 2006-10-30
Hello,

Running Xubuntu on IBM Thinkpad X22 with 128MB of RAM
Customizing my desktop when I lost all of my toolbars top and bottom
I've seen the fixes for Ubuntu. Is there something I can do in Xubuntu?

Any help would be apprecaited. Frustrating working without those toolbars

](*,)

---

### Post by john.nicholls on 2006-10-31
Alt-F2 to open a Run menu, and enter xfce4-panel to get the panels back. Then  right-click on a blank part of the panel and click Restart to save your configuration and ensure the panels are there when you login next time.

John

---

### Post by Ulysses on 2006-11-09
Hey

Perfect. Sorry for the delay in responding. My wife just had our baby and I kinda got away from the computer for a bit

The solution was perfect. Worked like a charm.

New problem, though

Everytime I go to customize the toolbar it freezes up on me. Is there anything I can do about that?

](*,)

---

### Post by Sef on 2006-11-09
> Perfect. Sorry for the delay in responding. My wife just had our baby and I kinda got away from the computer for a bit

Congrats on the baby.  

> Everytime I go to customize the toolbar it freezes up on me. Is there anything I can do about that?

Does it also freeze when you click 'Add New Item or anything else?'

---

### Post by Ulysses on 2006-11-09
Hello,

The toolbars work now. But there's more

Went to try and work through where exactly it freezes and Xubuntu did not freeze when I was customizing the desktop. I thought 'Great! Glitch is gone!'.
But now it freezes up for no reason that I can see.
Ubuntu does the same thing, and I thought it was because of my system and it not being compatible. That's why Xubuntu was to be the thing that would solve all of my problems
This is what I've got
IBM Thinkpad x22, Pentium 3, 800 with 128mB of RAM
The BIOS is a little over three years old. It's not a bad laptop.

Is there anything I can do? It seems to freeze up without rhyme or reason and the only way to recover is to unplug and remove and  replace the battery and plug it back in and restart.
And, yup, I've tried different combinations - leaving it plugged in all the time to see if the change in the battery status could trigger it. It still happens. I even took off the update notifier, in case that it froze when trying to snag an update.

Help?

](*,) 

RAR

---

### Post by kerry_s on 2006-11-09
Did you create swap space? It sounds like it's running low on memory and it's trying  find some.

---

### Post by Ulysses on 2006-11-09
Hello

Here's where it gets interesting

Uhh...What's a swap space?

I'll search the forums for an answer but if you can get back to me with your answer that will be the best news I've had in the past three hours

RAR 

:-D

---

### Post by kerry_s on 2006-11-09
swap space is space on your hd that the system would use like it was memory, it should have been made when you installed. so for example you have 128ram and a 512swap is like having 640 of memory. 

I'm not sure how to add it after install so hopefully someone else can talk you through it.

---

### Post by Sef on 2006-11-09
Swap should be double the memory, e.g. 128 ram should have a swap of 256; 256 ram should have a swap of 512.

How much ram do you have?


You can use the install cd to create swap; however, [GParted]("http://gparted.sourceforge.net/") would be better since it is a graphical installer.

---

### Post by Ulysses on 2006-11-09
Hey

Searched the forums to see what swap space was. Checked my install notes and I made nothing for swap space.
I installed 6.06 from CD and I chose the automatic partitioning method, so if there were options for swap space I did not see it (at least I didn't make notes on it)

My machine is as follows
IBM Thinkpad X22
128MB RAM
Pentium 3, 800mhz
Standard keyboard and pointing device, though I am using a Dell USB mouse

I am going to install Gparted and navigate my way through the GUI  to see just how easy it is (after I backup my stuff)

Please forward me anything else you think I should know. Figure I will get to the install in about an hour after I do all of my backups and change my daughter's diaper

Thanks alot. The crashing was starting to get me down, no pun intended.

RAR

:D

---

### Post by Sef on 2006-11-09
> installed 6.06 from CD and I chose the automatic partitioning method....

If I remember correctly, it should have made a swap, but maybe also the swap's too small.  

Another problem be a faulty installation.

Did you md5sum the download?

---

### Post by Ulysses on 2006-11-09
Hello

After a matter of days I am a diaper ninja when it comes to changing my daughter.
But my ubuntu-fu is weak. My laptop has now froze 4 times in the past fifteen minutes as I tried to assemble a response. MAN do I ever want this fixed.

](*,) 

> Another problem be a faulty installation.

Did you md5sum the download?

CD came via Shipit so there are no issues there.

> If I remember correctly, it should have made a swap, but maybe also the swap's too small. 

I installed GPartEd and ran it. Seems as if the swap did happen when I chose the automatic partitioning during the install

The swap is 360MB which should be plenty, right? It's still freezing. And there is a padlock icon next to the swap line. I can't increase the size to experiment. 

Help?

RAR

---

### Post by Ulysses on 2006-11-09
Hello

](*,) 

Can't post the screenshot so you will have to take my word for it

/dev/hda2 (padlock) filesystem extended 360.84MB
Then down from that
>/dev/hda5 (padlock) filesystem linux swap 360.81MB

I'm assuming that the swap is 360.81 of the 360.84 of the extended filesystem (assuming because I really don't know)

Went into System>Administration>Disks to see if I could unlock anything but no joy

Any and all help would be appreciated.

RAR

---

### Post by kerry_s on 2006-11-10
Sounds like your not running gparted as root, press alt+F2 and type>  gksu gparted  <also if swap is on, you have to turn it off first. In terminal do > sudo swapoff -a. Generally the more swap you can spare the better< no need to go more than a gig(1024).

It might be as simple as your swap is not turned on.

---

### Post by Choad on 2006-11-10
> Sorry for the delay in responding. My wife just had our baby and I kinda got away from the computer for a bit

rofl

that is hillarious. damn babies! distracting u from whats really important

---

### Post by Ulysses on 2006-11-10
Hello,

> Sounds like your not running gparted as root, press alt+F2 and type> gksu gparted 

Did that and it just ran GPartEd. Nothing different from what I was doing before.

> 
also if swap is on, you have to turn it off first. In terminal do > sudo swapoff -a.

Did that and I got this message
```
swapoff: /dev/hda5: Cannot allocate memory
```

I'm working from two threads here (not sure if that's kosher or not but it was late and I was frustrated) and on the second thread the advice was to go and get a more recent version of GPartEd and boot from that CD and see what might happen. That is my next resort.

> Quote:
Sorry for the delay in responding. My wife just had our baby and I kinda got away from the computer for a bit
rofl

that is hillarious. damn babies! distracting u from whats really important


I change diapers wa-aaay better than I work on computers but guess which one I've been doing longer?

RAR

---

### Post by Ulysses on 2006-11-10
Hey

Had two threads going. Hope that's not bad form. Man, is everyone ever helpful around here. Seriously. Does Vista have a forum?

Anyway. Here's what happened

```
sudo swapoff -a
```

Gave me this result

```
swapoff: /dev/hda5: Cannot allocate memory
```

So I went to here and downloaded the Live CD ISO for GPartEd

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php) 

I burned the CD, rebooted from the CD, used to excellent, idiot proof GUI to change my swap size (opted for an even 1GiB) and waited 22 minutes while the computer did it's bit.

Thanks to everyone that helped me out. Now that everything is okay with my laptop I am going to find new and interesting ways to screw it up all over again. Maybe by having a 2nd OS on a 2nd partition

Thanks again. My daughter's first words will be Ubuntu.

RAR

---

### Post by dthuk on 2008-01-03
I had a similar problem with lost toolbars in Xubuntu and the Alt-F2 and xfce4-panel thing worked a treat. Thanks a lot to john.nicholls for that. When you haven't got toolbars it seems that there is no way out.

Just a thought though, when this happened I was using Wicd to connect to my network. Very occasionally I get no connection and I go into Wicd to reconnect and on this occasion it crashed whilst trying to connect and when I rebooted, I had no toolbars. Does that ring any bells with anyone? I'd love to know what actually happened to remove my toolbars.

Thanks for any help and thanks again for getting me out of a tight spot.

---

