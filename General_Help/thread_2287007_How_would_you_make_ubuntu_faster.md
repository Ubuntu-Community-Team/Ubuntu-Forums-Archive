---
title: "How would you make ubuntu faster"
date: 2015-07-16
forum: General Help
---

### Post by dellboy56 on 2015-07-16
Hello these are my specs I'm running ubuntu on this is not a dual boot I'm doing this through virtualbox 
HP laptop [windows 8.1] installed ram 4gigs with a 4gig hard disk 
guest [ubuntu]
Guest HDD configured with 11gig hard disk 
video memory given to guest 128
3d and 2d turned off
ram given to guest is 630 i think I configured 


this his is just a experiment like I ran this a couple times with diffrent set up and I want to know your opions on how would u make it faster with like lightweight apps and desktops thanks

---

### Post by howefield on 2015-07-16
For starters, give more ram to the guest. 630 is pretty tight I'd say.

---

### Post by dino99 on 2015-07-16
why dont you try to boot the iso (select 'try ubuntu') from a usb stick ? its way better than virtualization

---

### Post by slickymaster on 2015-07-16
> **howefield said:**
> For starters, give more ram to the guest. 630 is pretty tight I'd say.

+1 

If you're running Ubuntu, not one of the official flavors, I'd recommend at least 2 GB of RAM if you want a smooth experience with it.

---

### Post by grahammechanical on 2015-07-16
In my case I would not use a VM at all.

"video memory given to guest 128." Is that 128 MB? I would not expect a good user experience with twice the amount of video memory. Remember, Ubuntu has a 3D user interface that requires a graphic adapter that can do its own accelerated 3D rendering. And it is not getting that.

Regards.

---

### Post by mastablasta on 2015-07-16
> **grahammechanical said:**
> 
"video memory given to guest 128." Is that 128 MB? I would not expect a good user experience with twice the amount of video memory. Remember, Ubuntu has a 3D user interface that requires a graphic adapter that can do its own accelerated 3D rendering. And it is not getting that.
.

yeah that is 128 MB and this is virtual GPU. I don't know how this virtual stuff actually works but I think partially some stuff is piped to real GPU or maybe only real RAM and CPU using "virtualbox guest additions" if I am not mistaking. anyway Ubuntu should work well in Virtualbox but it does need RAM. 2 GB should do it. maybe even 1.5 GB.

But Xubuntu or Lubuntu work well even with less. and less GPU power.

you might need to enable some acceleration (maybe 2D?!). I think forum member TheFu has some good articles on his blog for optimum setup for vbox.

---

### Post by v3.xx on 2015-07-16
Two thoughts ..

#1
You can add the lighter "Flashback" desktop to your install and choose your desktop at the login screen by clicking on the icon in the top right of the screen.
```
sudo apt-get install gnome-panel
```
#2
Try Mate, I find it fast out of the box.

And I do agree you need more ram.

---

